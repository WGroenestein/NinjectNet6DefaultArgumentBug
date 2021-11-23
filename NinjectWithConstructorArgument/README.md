# Repro steps

1. Open the solution in VS 2022
2. Run it
3. See that it crashes with the following error

    ```log
    System.InvalidProgramException: 'Common Language Runtime detected an invalid program.'
      at System.Runtime.CompilerServices.RuntimeHelpers.CompileMethod(RuntimeMethodHandleInternal method)
      at System.Reflection.Emit.DynamicMethod.CreateDelegate(Type delegateType)
      at Ninject.Injection.DynamicMethodInjectorFactory.Create(ConstructorInfo constructor)
      at Ninject.Planning.Strategies.ConstructorReflectionStrategy.Execute(IPlan plan)
      at Ninject.Planning.Planner.<> c__DisplayClass9_0.< CreateNewPlan > b__0(IPlanningStrategy s)
      at Ninject.Infrastructure.Language.ExtensionsForIEnumerableOfT.Map[T](IEnumerable`1 series, Action`1 tion)
      at Ninject.Planning.Planner.CreateNewPlan(Type type)
      at Ninject.Planning.Planner.GetPlan(Type type)
      at Ninject.Activation.Context.ResolveInternal(Object scope)
      at Ninject.Activation.Context.Resolve()
      at Ninject.KernelBase.Resolve(IRequest request, Boolean handleMissingBindings)
      at Ninject.KernelBase.Resolve(IRequest request, Boolean handleMissingBindings)
      at Ninject.KernelBase.Resolve(IRequest request)
      at Ninject.Planning.Targets.Target`1.ResolveWithin(IContext parent)
      at Ninject.Activation.Providers.StandardProvider.GetValue(IContext context, ITarget target)
      at Ninject.Activation.Providers.StandardProvider.<> c__DisplayClass15_0.< Create > b__0(ITarget target)
      at System.Linq.Enumerable.SelectArrayIterator`2.ToArray()
      at System.Linq.Enumerable.ToArray[TSource](IEnumerable`1 source)
      at Ninject.Activation.Providers.StandardProvider.Create(IContext context)
      at Ninject.Activation.Context.ResolveInternal(Object scope)
      at Ninject.Activation.Context.Resolve()
      at Ninject.KernelBase.Resolve(IRequest request, Boolean handleMissingBindings)
      at Ninject.KernelBase.Resolve(IRequest request)
      at Ninject.ResolutionExtensions.GetResolutionIterator(IResolutionRoot root, Type service, Func`2   nstraint, IEnumerable`1 parameters, Boolean isOptional, Boolean isUnique)
      at Ninject.ResolutionExtensions.Get[T](IResolutionRoot root, IParameter[] parameters)
      at Program.Main() in C:\Redacted\NinjectWithConstructorArgument\NinjectWithConstructorArgument\Program.cs:line 16
    ```

4. Change the TargetFramework in the csproj file to net5.0
5. Run it
6. See that it runs happily
