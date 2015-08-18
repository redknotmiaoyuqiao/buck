#buck project  
  
为一个 IDE 生成配置文件并且使用这个 IDE 构建项目。  
目前,只有 IntelliJ 支持。  
  
这个命令处理所有的`project_config`规则，包括所有的 BUCk 文件,并使用它们来为 IDE 生成配置文件。如果规定目标是位置参数，那么这个项目就只包含“生成指定目标”的代码。这对大型存储库是十分有用的。  
  
在 IntelliJ 环境下，生成的文件包括：  
  
- `.idea/libraries/*.xml` 每一个都在 IntelliJ 中定义了一个库。一个库就相当于一个`prebuilt_jar`。  

- `.iml文件` 每一个都在 IntelliJ 中定义了一个模块。 在每一个具有`project_config` 的 `BUCK`文件目录中，`.iml`文件都将被创建。一个模块不仅可以依赖其他模块,也可以依赖库。  

- `.idea/modules.xml` 列出了项目中的所有 IntelliJ 模块。  

因此，通过运行 `buck project` 就在本地的存储库中创建了所有上述文件。不同于那些在独立目录中产生输出的 BUCK 命令，它们将通过运行 `buck clean` 被删除。  
  
注意：所有通过 `buck project` 产生的文件，都应在 `.gitignore.` 中记录。  
  
##参数  
  
- `--without-tests` 表明： BUCK 应该建立一个不进行测试的项目（所有引用`source_under_test`项目的目标，都被默认包含在测试中）。 