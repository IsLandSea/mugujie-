# mugujie-
去了蘑菇街面试，先不管结果怎么样吧，记录下被问到的问题。

1：assin 与 weak 的区别

assign: 简单赋值，不更改索引计数

对基础数据类型 （例如NSInteger，CGFloat）和C数据类型（int, float, double, char, 等） 适用简单数据类型

此标记说明设置器直接进行赋值，这也是默认值。在使用垃圾收集的应用程序中，如果你要一个属性使用assign，且这个类符合NSCopying协 

议，你就要明确指出这个标记，而不是简单地使用默认值，否则的话，你将得到一个编译警告。这再次向编译器说明你确实需要赋值，即使它是可拷贝的。

weak比assign多了一个功能，当对象消失后自动把指针变成nil

2：CALayer 的子类 

CALyer CAGradientLayer CATiledLayer CAShapeLayer CATextLayer CAEmitterLayer CAReplicatorLayer CAScrollLaye

3：autoReleasePool 的作用

如果能够真正的理解autorelease，那么才是理解了Objective 

c的内存管理。Autorelease实际上只是把对release的调用延迟了，对于每一个Autorelease，系统只是把该Object放入了当

前的Autorelease pool中，当该pool被释放时，该pool中的所有Object会被调用Release。

实际上对于 [NSString stringWithFormat:1.0] 这类构造函数返回的对象都是autorelease的。

4:MVC

模型层 (Model) ：存储数据并且定义如何操作这些数据

视图层 (View) ：负责模型层的可视化展示，并且负责用户的交互，一般来说都是继承自 UIView 

控制器 (Controller) ：控制器是整个系统的掌控者，它连接了模型层和数据层，并且把数据在视图层展示出来，监听各种事件，负责数据的各种操作。不

妨猜猜在我们的项目中哪个是控制器？啊哈猜对了：ViewController 这个类就是。

模型层通知控制器层任何数据的变化，然后控制器层会刷新视图层中的数据。视图层可以通知控制器层用户的交互事件，然后控制器会处理各种事件以及刷

新数据。

之所以这样做，是为了将代码更好的分离和重用。理想状态下，视图层应当和模型层完全分离。如果视图层不依赖任何模型层的具体实现，那么就可以很容

易的被其他模型复用，用来展示不同的数据。
