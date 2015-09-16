# 5. 流和多路复用

在一个HTTP/2的连接中, 流是用于客户端与服务器交换frame的独立双向序列. 流有几个重要的特点:

+ 一个HTTP/2连接可以包含多个并发的流, 各个端点从多个流中交换frame
+ 流可以被客户端或服务器单方面建立, 使用或共享
+ 流也可以被任意一方关闭
+ frames在一个流上的发送顺序很重要. 接收方将按照他们的接收顺序处理这些frame. 特别是HEADERS和DATA frame的顺序, 在协议的语义上显得尤为重要.
+ 流用一个整数(流标识符)标记. 端点初始化流的时候就为其分配了标识符.

## 5.1 流状态