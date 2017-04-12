For example, the extension method "FastInvoke" defined for MethodInfo type gets the corresponding worker object by the MethodInfo instance as the key from cache, and execute the Invoke method in the worker object. Apparently keeping the worker object and use it directly after getting it would give us better perfermance than retrieving it from cache again and again.

Here's the list of worker types for each XxxInfo type:
* PropertyInfo: IPropertyAccessor
* MethodInfo: IMethodInvoker
* ConstructorInfo: IConstructorInvoker
* FieldInfo: IFieldAccessor

We can get an IMethodInvoker object from FastReflectionCaches.MethodInvokerCache by a MethodInfo object:
```CSharp
static void Execute(MethodInfo methodInfo, object instance, int times)
{
    IMethodInvoker invoker = FastReflectionCaches.MethodInvokerCache.Get(methodInfo);
    object[] parameters = new object[0];
    for (int i = 0; i < times; i++)
    {
        invoker.Invoke(instance, parameters);
    }
}
```