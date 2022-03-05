## I. 帮助完善已有的模块


1. 拉取最新的模块

在向已有的模块添加新的内容时，请确保已经拉取了最新的模块。
拉取最新的模块的方法是在requestment.txt中使用latest版本。
例如：
```
STM32G0==latest
```

2. **删除reqeustment.txt中需要开发的模块**，防止误操作（比如再次拉取模块）导致正在开发的模块被覆盖掉。
2. 修改模块并测试

为模块添加新的Python接口 --> [module].py
或者提供更好的实现 --> pikascript-lib/[module]/*.c
​


4. （可选）在 pikascript/README.md 和 pikascript/README_zh.md 中更新模块信息。
4. 提交模块的文件
   1. fork一份pikascript仓库，然后clone到本地。

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638664526181-09b00c29-fc72-429a-bb99-3f009eae141e.png#clientId=u1df381a6-8a3b-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=45&id=ubb540eb4&margin=%5Bobject%20Object%5D&name=image.png&originHeight=90&originWidth=716&originalType=binary&ratio=1&rotation=0&showTitle=false&size=10629&status=done&style=none&taskId=u6e4ba5c7-6918-47ee-8227-7e0e6e684ee&title=&width=358)

   2. 复制[module].py到pikascript-lib/[module]文件夹中。
   2. 复制整个修改后的pikascript-lib/[module]文件夹到fork后的pikascript/package文件夹中。
   2. git add 添加文件，并git commit 提交一次。
   2. git log 查看提交后的commit id，在fork后的pikascript/packages.toml中填写新的版本名，并复制当前的commit id。

例如：
```
[[packages]]
name = "STM32G0"
releases = [
  "v1.0.2 0052a28582ac8a85cc48e1d676d9a3be5cb1b93f",
  "<新的版本名> <当前的commit id>",
]
```

   6. git commit -a再提交一次，添加packages.toml的修改。
   6. git push到你fork后的仓库中。
   6. 提交pull request。

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638664500423-e4ad59fa-e476-48f0-b7ec-89f98eb70e6c.png#clientId=u1df381a6-8a3b-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=70&id=u41301d54&margin=%5Bobject%20Object%5D&name=image.png&originHeight=140&originWidth=1086&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12365&status=done&style=none&taskId=uf6e69a81-cd1b-49a8-9de6-1ba9ca4ef59&title=&width=543)
## II. 提交新的模块


1. 新建[module].py文件和pikascript-lib/[module]文件夹。
1. 开发和测试新的模块。
1. （可选）在 pikascript/README.md 和 pikascript/README_zh.md 中更新模块信息。
1. 提交模块的文件
   1. fork一份pikascript仓库，然后clone到本地。

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638664526181-09b00c29-fc72-429a-bb99-3f009eae141e.png#clientId=u1df381a6-8a3b-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=45&id=e2G0m&margin=%5Bobject%20Object%5D&name=image.png&originHeight=90&originWidth=716&originalType=binary&ratio=1&rotation=0&showTitle=false&size=10629&status=done&style=none&taskId=u6e4ba5c7-6918-47ee-8227-7e0e6e684ee&title=&width=358)

   2. 复制[module].py到pikascript-lib/[module]文件夹中。
   2. 复制整个pikascript-lib/[module]文件夹到fork后的pikascript/package文件夹中。
   2. git add 添加文件，并git commit 提交一次。
   2. git log 查看提交后的commit id，在fork后的pikascript/packages.toml中新增新的模块，填写模块名、版本名和当前的commit id。

例如：
```
[[packages]]
name = "<新模块名>"
releases = [
  "<新的版本名> <当前的commit id>",
]
```

   6. git commit -a再提交一次，添加packages.toml的修改。
   6. git push到你fork后的仓库中。
   6. 提交pull request。

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638664500423-e4ad59fa-e476-48f0-b7ec-89f98eb70e6c.png#clientId=u1df381a6-8a3b-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=70&id=JSPzV&margin=%5Bobject%20Object%5D&name=image.png&originHeight=140&originWidth=1086&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12365&status=done&style=none&taskId=uf6e69a81-cd1b-49a8-9de6-1ba9ca4ef59&title=&width=543)
