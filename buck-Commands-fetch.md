# buck fetch  
  
这个命令可以获得一个或多个资源，它是通过 `remote_file` 规则定义得到的。如果`remote_file` 规则被用于存储库，那么他通常被放在 `buck build` 之前运行。你必须在命令行中指定一个或多个构建目标。  
  
Buck 将查看您所指定的目标的传递依赖,所以在一般情况下，最好是指定你的高层目标来获得所有你需要的远程对象。  
  
    buck fetch //third-party/jetty:jetty-source  
  
如果你查询存储库中的依赖关系，并使用一个预先构建的规则，我们坚信,你和你的团队将会有一个更好的体验。Buck团队不鼓励你去获取它。  
  
## 参数  
  
- `--verbose (-v)` 记录了控制台上显示的详细情况。1为最简要的，10为为最详细的。