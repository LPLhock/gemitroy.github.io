# JVM

## Memeory Model 

#### JVM Runtime memory

* 方法区
  * Pre 1.8（PermGen） = 类信息、常量池、静态变量、JIT编译后的代码
  * After 1.8 （MetaSpace），在JVM外（本地内存）；字符串常量池移到堆内
* 堆（Heap/xms&xmx）= Yong\(eden&survivor\) + Old
* 程序计数器（PC）
* 本地方法栈（Native Stack）
* 虚拟机栈（JVM Stack）

![](../../.gitbook/assets/jvm-runtime.png)

### Memory analysis

-verbose:gc

jmap

visualVM

### Reordering

code might be reordered at compile time

## 垃圾回收算法

#### 对象标记判断算法

* 引用计数算法
* 可达性分析：GC Roots引用链，如无引用，则被第一次“标记”；finalized\(\)能让对象自我拯救

#### 垃圾收集算法

* 分代回收：Minor GC/Major GC/Full GC
* 标记-清除：效率不稳定，内存空间碎片化
* 标记-复制：对象存活率高时复制多，效率低，一般用于新生代，将其分为1  较大的Eden和2 small Survivor
* 标记-整理：将存活对象向内存一端移动，然后直接清理边界以外内存

#### 垃圾回收器

* Serial, Parallel
* CMS
* G1
* ZGC - all concurrently

#### Misc

finalize\(\): called by gc when gc

## 类加载

#### 加载 - 连接 - 初始化

#### 类加载器



