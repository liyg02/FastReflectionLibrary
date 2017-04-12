FastReflectionLib has already provide default implementations for each worker interfaces. These implementations generate lambda expressions and compile them (by call Compile method) to delegate objects with the same signatures as the corresponding reflection methods. The implementation is simle, general and safe than directly Emit and the performance is good enough for most scenarios (please refer to the [Benchmarks](Benchmarks) section).

But it's not the most efficient way to do so. The best optimized way by Emit could get better performance than directly access the members in code ([Dynamic Reflection Library](http://dynamic.codeplex.com/) is one of these implementations). You can build your one worker interface implementation and factory to replace the build-in ones if necessary:
```CSharp
public class BetterPropertyAccessor : IPropertyAccessor
{
    public BetterPropertyAccessor(PropertyInfo propertyInfo) { ... }
    ...
}

public class BetterPropertyAccessorFactory :
    IFastReflectionFactory<PropertyInfo, IPropertyAccessor>
{
    public IPropertyAccessor Create(PropertyInfo key)
    {
        return new BetterPropertyAccessor(key);
    }
}

class Program
{
    static void Main(string[] args)
    {
        FastReflectionFactories.PropertyAccessorFactory =
            new BetterPropertyAccessorFactory();
        ...
    }
}
```