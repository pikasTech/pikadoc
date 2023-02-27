# 紧凑型内存池

## 概述

PikaPython 内置了供小资源芯片使用的紧凑型内存池，默认不开启。

紧凑型内存池可以将内存碎片从通常的 20~30% 降低至 5% 以下。

【注意】 紧凑型内存池会降低运行速度。

## 开启方式

【注意】 需要内核版本不低于 v1.9.0

### 开启用户配置

参考 [配置文档](%E4%BC%98%E5%8C%96%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E3%80%81%E9%85%8D%E7%BD%AE%20libc.html)

### 加入配置项

```
/* pika_config.h */
#define PIKA_POOL_ENABLE 1
#define PIKA_POOL_SIZE 0x1900
```

其中 `PIKA_POOL_ENABLE` 表示开启紧凑型内存池，`PIKA_POOL_SIZE` 表示内存池的大小，内存池从 heap 中预先申请内存，请确保 heap 能够申请到该大小。

参考 [bsp/stm32g030c8/Booter/pika_config.h](https://gitee.com/Lyon1998/pikapython/blob/master/bsp/stm32g030c8/Booter/pika_config.h)

### 内存池初始化

在 `pikaScriptInit()` 或者 `newRootObj()` 之前初始化内存池。 

``` C
mem_pool_init();
```

参考：[bsp/stm32g030c8/Booter/main.c](https://gitee.com/Lyon1998/pikapython/blob/master/bsp/stm32g030c8/Booter/main.c)

## 释放内存池

如果需要释放内存池，调用

``` C
mem_pool_deinit();
```


# 打断脚本运行

调用 `pks_vm_exit()` 可以强制打断正在运行的脚本（在死循环中也可以打断），可以放在中断函数里。

> [注意]
> 
> 需要内核版本不低于 `v1.11.0`
> 
> 打断运行的脚本之后，只是退出的 VM 的运行，根对象仍然可以继续使用，不会被释放，如果需要释放内存，则应对根对象执行 `obj_deinit()`。
