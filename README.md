# log
基于zap封装的log库

打造 Zap 开箱即用日志组件

提供的功能:
像 logrus 一样, 全局的 Debug, Info ... 函数  
日志分割功能. 默认文件大小1024M，自动压缩, 最大有3个文件备份，备份保存时间7天, 不会打印日志被调用的文文件名和位置  
日志默认会被分成五类文件：debug、info、warn、error、panic 都会打印在xxx.log. xxx.log.Request输出 request log 的地方(如果有需要的话)


使用方法
```go
 go get github.com/yizhidaozuihou/log
```

例子
```go
package main

import "github.com/yizhidaozuihou/log"

func main() {
	// init log
	// set absolute path, and level
	// set output level
	// don't need request log
	// set log's caller using logOption
	log.Init("./test.log", log.DebugLevel, false, log.SetCaller(true))
	log.Info("hello george log")
	// flush
	log.Sync()
	//output: {"level":"info","ts":"2019-12-16T10:37:11.364+0800","caller":"example/example.go:12","msg":"hello george log"}
}
```