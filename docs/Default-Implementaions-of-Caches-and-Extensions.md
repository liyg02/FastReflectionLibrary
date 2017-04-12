FastReflectionLib uses the caches based on System.Collections.Generic.Dictionary<TKey, TValue>. When we invoke a FastXxx extension method, the library would retrieve the worker object from the cache container and execute it. If the worker object cannot be found in the cache, a new one would be created by the corresponding factory. In the [Benchmarks](Becchmarks) section we can found that considerable time is "wasted" in searching the cache.

If you have better cache implementation you can replace the build-in one as following:

```CSharp
public class BetterMethodInvokerCache :
    IFastReflectionCache<MethodInfo, IMethodInvoker>
{
    public IMethodInvoker Get(MethodInfo key) { ... }
}

class Program
{
    static void Main(string[] args)
    {
        FastReflectionCaches.MethodInvokerCache =
            new BetterMethodInvokerCache();
        ...
    }
}
```