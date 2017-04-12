A benchmark project is provided with the source of FastReflectionLib. Here's part of the results (the benchmarks were run on my laptop with release build):

Execute the following method 1,000,000 times:

```CSharp
public class Test
{
    public void MethodWithArgs(int a1, string a2) { }
}
```

<table>
    <tbody>
        <tr>
            <th>The way to excute </th>
            <th>Time elapsed (in second) </th>
        </tr>
        <tr>
            <td>Directly invoke </td>
            <td>0.0071397 </td>
        </tr>
        <tr>
            <td>Build-in reflection </td>
            <td>1.4936181 </td>
        </tr>
        <tr>
            <td>MethodInvoker.Invoke </td>
            <td>0.0468326 </td>
        </tr>
        <tr>
            <td>FastInvoke </td>
            <td>0.1373712 </td>
        </tr>
    </tbody>
</table>