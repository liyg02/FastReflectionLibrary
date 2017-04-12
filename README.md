
最近在学习反射的知识，于是发现了这个类库，这个类库通过Expression Tree来创建反射调用，旨在提高运行效率。生成反射的调用又多种方法:`委托`、`CodeDemo`、`接口`、`Emit`、`Expression Tree`、`dynamic`，作者选择使用Expression Tree来生成反射的调用一定有他的道理，经过测试也验证Expressioin Tree确实是一种高效的办法 *（测试结果：直接调用 >= 委托 >= 接口调用 > Expression Tree >= Emit > Invoke）* ，本人才疏学浅，无法做出准确性的判断，于是选择相信该类库的作者，毕竟该作者在.net领域还是很权威的。

## 类库简介
这个类库是一个轻量级反射类库，旨在提供通用的、高效的生成反射调用的方法，这个类库 fork from [Fast Reflection Library 1.0 bate](http://fastreflectionlib.codeplex.com)，作者为[Jeffrey Zhao](http://www.cnblogs.com/JeffreyZhao)。

## 目标

该类库作者至2009年以来已经停止了版本的维护，接下来我准备接手继续开发，最终目标将打造一款轻量级IOC框架，在这里提前预祝自己成功。

## 文档

[中文文档地址](http://www.cnblogs.com/JeffreyZhao/archive/2009/02/01/Fast-Reflection-Library.html)

[英文文档地址](docs/Home.md)
