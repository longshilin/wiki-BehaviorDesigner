# 安装
导入行为设计器后，您可以从“Tools”工具栏访问它。您可以通过导入“[下载](https://opsive.com/downloads/?pid=803)”页面上的“运行时源代码”包来访问运行时源代码。解压缩该程序包之前，请确保已删除"Behavior Designer"文件夹，否则会出现编译错误。

为了为通用Windows平台（UWP）编译行为设计器，必须使用运行时源代码而不是已编译的DLL。无需更改编译设置– Behavior Designer可以在启用.Net Core的情况下进行编译。

当您尝试运行您的UWP应用时，您可能会收到一条错误消息，指示找不到任务。为了解决此问题，TaskUtility.GetTypesWithinAssembly（在TaskUtility.cs中）的以下行应更改为：

```csharp
    loadedAssemblies = GetStorageFileAssemblies(typeName).Result;
```

到：
```csharp
    loadedAssemblies = new List(); 
    loadingAssemblies.Add("Assembly-CSharp");
```
这将允许在应用程序中找到Unity的C＃程序集。

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMzNjg0NDY0MSwtNzA1MDUwNjAyLDExMT
M2NzIwMV19
-->