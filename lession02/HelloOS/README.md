# 02 | 几行汇编几行C：实现一个最简单的内核

该方案来自https://github.com/vizv/learn_os，与课件中使用VirtualBox不同，使用Docker和QEMU配合工作。

在我的实验中，apk出现了更新的错误：

> ERROR: https://dl-cdn.alpinelinux.org/alpine/edge/main: Permission denied

按 <https://github.com/alpinelinux/docker-alpine/issues/98> 中提供的解决方案，替换`https`为`http`。

```
RUN sed -i 's/https/http/' /etc/apk/repositories
```

![diff](/img/lession02_diff.png)