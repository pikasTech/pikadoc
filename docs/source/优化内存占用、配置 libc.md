1. PikaScript本身是**免配置**的，所以通常情况下**不需要**了解这部分内容。
2. 可以通过创建pika_config.c，重写[PikaPlagform.h](https://gitee.com/Lyon1998/pikascript/blob/master/src/PikaPlatform.h)里面的弱函数来配置PikaScript。

![1e7cc2fbce28dd51cfb3ac50af92ded.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639152750280-2b8de507-8a50-4cf6-9d14-86fbb79a775b.png#clientId=uf23b85cd-130f-4&crop=0&crop=0&crop=1&crop=0.5829&from=paste&height=504&id=WQ1yA&margin=%5Bobject%20Object%5D&name=1e7cc2fbce28dd51cfb3ac50af92ded.png&originHeight=1007&originWidth=1215&originalType=binary&ratio=1&rotation=0&showTitle=false&size=101411&status=done&style=none&taskId=u297f9833-b284-491b-ade1-4e204987309&title=&width=608)

3. 配置项包括：
   1. 中断保护 —— 提供中断总开关，保护PikaScript内存安全
   1. libC —— 选择libC的实现
   1. 内存池 —— 降低内存碎片
   1. 字节码存储 —— 将字节码写入flash，加速启动，降低内存占用
4. 示例代码：
   1. [https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/pika_config.c](https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/pika_config.c)
   1. [https://gitee.com/Lyon1998/pikascript/blob/master/package/pikaRTBooter/pika_config.c](https://gitee.com/Lyon1998/pikascript/blob/master/package/pikaRTBooter/pika_config.c)
