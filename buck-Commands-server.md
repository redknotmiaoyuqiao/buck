#buck server  
  
通过运行 BUCK 找到关于http服务器的信息。  
  
    buck server status --http-port  
  
##命令  
  
- `status --http-port` 如果 BUCK 进程正在运行一个 HTTP 服务，那么就返回服务器上运行的端口，否则返回-1。
  
##参数  
  
- `--json ` 输出结果为 JSON。