#buck install  
构建和安装一个以 `android_binary` 为目标的 APK 。  
需要 `android_binary` 来构建，并且通过 `adb install -r <path_to_the_APK>` 来安装。  
  
##参数  
  
- `--run (-r)` 安装后使用默认活动启动 `.apk`。  
  
- `--activity <fully qualified class name> (-a)` 安装后使用指定活动启动 `.apk`。