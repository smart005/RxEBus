# RxEBus
一个轻量级IPC通信框架;
/*EBus进程内与进程间通信包括实现原理可下午demo查看*/

<span style="width:300px;">![images](/docs/cur_process.png)</span><span style="width:300px;">![images](/docs/process_messsage.png)</span>

主要功能和特点:
1.支持跨页面通信;
2.支持进程(process)和线程(thread)通信;
3.根据指定的receivekey分发消息机制;
4.消息发送与接收参数支持无限个;
5.支持跨应用通信;
## 引用
###### 1.项目build.gradle引用仓库地址
```docker
repositories {
    maven { url 'http://mv.slcore.com:81/content/repositories/geeasejars/' }
}
```
###### 2.对应模块build.gradle引用以下版本
```docker
implementation 'com.geease:ebus:1.0.2'
```
## 使用
需要接收消息位置注册EBus
```docker
EBus.getInstance().registered(this);
```
发送消息事件
```docker
#进程内通信(Posts the given event to the event bus)
EBus.getInstance().post(String receiveKey, Object... event)
#跨进程通信(Posts the given event to the event bus for current process or other process)
EBus.getInstance().postMultiProcess(Context postProcessContext, String receiveKey, Object... event)
```
接收消息处理
```docker
@SubscribeEBus(receiveKey = "receive_key",threadMode = ThreadModeEBus.MAIN)
public void onEventTest(String data) {
    
}
#其中接收参数类型与个数和发送消息可变参数对应即可;
```
## 与EventBus比较
| 选项         | RxEBus   | EventBus | 备注                                                                            |
|--------------|----------|----------|---------------------------------------------------------------------------------|
| 进程间通信   |     √    |     ✕    |                                                                                 |
| 接收参数个数 | 可自定义 |   一个   |                                                                                 |
| 性能         |     ↑    |     -    | RxEBus指定key对应发送; EventBus根据参数类型，只要参数类型一致都会收到消息;      |
| 方便         |     √    |     ✕    | EventBus接收消息体时需要定义不同的model容易产生冗余；而RxEBus只要追加参数即可； |


###
<font size="12" color="#041d29">如果觉得有帮助请转到右上角顺序帮忙点个星吧！！！</font>
###
<font size="12" color="#041d29">如果觉得有帮助请转到右上角顺序帮忙点个星吧！！！</font>
###
<font size="12" color="#041d29">如果觉得有帮助请转到右上角顺序帮忙点个星吧！！！</font>
