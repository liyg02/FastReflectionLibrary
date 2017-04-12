Reflection is one of the most important features of .NET platform. The way of accessing/assigning a property or invoking a method dynamically is widely used by numerous projects. As we all know, invoke-by-reflection is much less efficient than direct access. FastReflectionLib provide the same as part of the refection features like executing method dynamically but give simple and faster implementations. It can be use as the foundation of reflection-based scenarios such as ORM framework.

Please look at the code snippets below:

```CSharp
using System;
using System.Reflection;
using FastReflectionLib;
    
namespace SimpleConsole
{
    class Program
    {
        static void Main(string[] args)
        {
            PropertyInfo propertyInfo = typeof(string).GetProperty("Length");
            MethodInfo methodInfo = typeof(string).GetMethod("Contains");
    
            string s = "Hello World!";
    
            // get value by normal reflection
            int length1 = (int)propertyInfo.GetValue(s, null);
            // get value by the extension method from FastReflectionLib,
            // which is much faster
            int length2 = (int)propertyInfo.FastGetValue(s);
    
            // invoke by normal reflection
            bool result1 = (bool)methodInfo.Invoke(s, new object[] { "Hello" });
            // invoke by the extension method from FastReflectionLib,
            // which is much faster
            bool result2 = (bool)methodInfo.FastInvoke(s, new object[] { "Hello" });
        }
    }
}
```
When we get the MethodInfo object, we can call the Invoke method to execute the method. FastReflectionLib contains several extension methods on these types (such as MethodInfo), so we can just put "Fast" before the method to replace the build-in ones. Comparing with the build-in functions, these new implementations get big performance improvements.