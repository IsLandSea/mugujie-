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

Http TCP UDP

HTTP协议的主要特点可概括如下：

1.支持客户/服务器模式。

2.简单快速：客户向服务器请求服务时，只需传送请求方法和路径。请求方法常用的有GET、HEAD、POST。每种方法规定了客户与服务器联系的类型不同。由

于HTTP协议简单，使得HTTP服务器的程序规模小，因而通信速度很快。

3.灵活：HTTP允许传输任意类型的数据对象。正在传输的类型由Content-Type加以标记。

4.无连接：无连接的含义是限制每次连接只处理一个请求。服务器处理完客户的请求，并收到客户的应答后，即断开连接。采用这种方式可以节省传输时间。
5.无状态：HTTP协议是无状态协议。无状态是指协议对于事务处理没有记忆能力。缺少状态意味着如果后续处理需要前面的信息，则它必须重传，这样可能

导致每次连接传送的数据量增大。另一方面，在服务器不需要先前信息时它的应答就较快。

TCP/UDP区别联系

TCP---传输控制协议,提供的是面向连接、可靠的字节流服务。当客户和服务器彼此交换数据前，必须先在双方之间建立一个TCP连接，之后才能传输数据。T

CP提供超时重发，丢弃重复数据，检验数据，流量控制等功能，保证数据能从一端传到另一端。 

UDP---用户数据报协议，是一个简单的面向数据报的运输层协议。UDP不提供可靠性，它只是把应用程序传给IP层的数据报发送出去，但是并不能保证它们能

到达目的地。由于UDP在传输数据报前不用在客户和服务器之间建立一个连接，且没有超时重发等机制，故而传输速度很快 

TCP（Transmission Control Protocol，传输控制协议）是基于连接的协议，也就是说，在正式收发数据前，必须和对方建立可靠的连接。一个TCP连接必须

要经过三次“对话”才能建立起来，我们来看看这三次对话的简单过程：1.主机A向主机B发出连接请求数据包；2.主机B向主机A发送同意连接和要求同步（同

步就是两台主机一个在发送，一个在接收，协调工作）的数据包；3.主机A再发出一个数据包确认主机B的要求同步：“我现在就发，你接着吧！”，这是第三

次对话。三次“对话”的目的是使数据包的发送和接收同步，经过三次“对话”之后，主机A才向主机B正式发送数据。 

UDP（User Data Protocol，用户数据报协议）是与TCP相对应的协议。它是面向非连接的协议，它不与对方建立连接，而是直接就把数据包发送过去！  

UDP适用于一次只传送少量数据、对可靠性要求不高的应用环境。

 

tcp协议和udp协议的差别 

是否连接面向连接面向非连接 

传输可靠性可靠不可靠 

应用场合传输大量数据少量数据 

速度慢快

socket连接和http连接的区别

简单说，你浏览的网页（网址以http://开头)都是http协议传输到你的浏览器的, 而http是基于socket之上的。socket是一套完成tcp，udp协议的接口。

HTTP协议：简单对象访问协议，对应于应用层  ，HTTP协议是基于TCP连接的

tcp协议：    对应于传输层

ip协议：     对应于网络层 

TCP/IP是传输层协议，主要解决数据如何在网络中传输；而HTTP是应用层协议，主要解决如何包装数据。

Socket是对TCP/IP协议的封装，Socket本身并不是协议，而是一个调用接口（API），通过Socket，我们才能使用TCP/IP协议。

http连接：http连接就是所谓的短连接，即客户端向服务器端发送一次请求，服务器端响应后连接即会断掉；

socket连接：socket连接就是所谓的长连接，理论上客户端和服务器端一旦建立起连接将不会主动断掉；但是由于各种环境因素可能会是连接断开，比如说：服务器端或客户端主机down了，网络故障，或者两者之间长时间没有数据传输，网络防火墙可能会断开该连接以释放网络资源。所以当一个socket连接中没有数据的传输，那么为了维持连接需要发送心跳消息~~具体心跳消息格式是开发者自己定义的

我们已经知道网络中的进程是通过socket来通信的，那什么是socket呢？socket起源于Unix，而Unix/Linux基本哲学之一就是“一切皆文件”，都可以用“打开open –> 读写write/read –> 关闭close”模式来操作。我的理解就是Socket就是该模式的一个实现，socket即是一种特殊的文件，一些socket函数就是对其进行的操作（读/写IO、打开、关闭），这些函数我们在后面进行介绍。

一。什么是TCP连接的三次握手

第一次握手：客户端发送syn包(syn=j)到服务器，并进入SYN_SEND状态，等待服务器确认；
第二次握手：服务器收到syn包，必须确认客户的SYN（ack=j+1），同时自己也发送一个SYN包（syn=k），即SYN+ACK包，此时服务器进入SYN_RECV状态；
第三次握手：客户端收到服务器的SYN＋ACK包，向服务器发送确认包ACK(ack=k+1)，此包发送完毕，客户端和服务器进入ESTABLISHED状态，完成三次握手。

握手过程中传送的包里不包含数据，三次握手完毕后，客户端与服务器才正式开始传送数据。理想状态下，TCP连接一旦建立，在通信双方中的任何一方主动关闭连接之前，TCP 连接都将被一直保持下去。断开连接时服务器和客户端均可以主动发起断开TCP连接的请求，断开过程需要经过“四次握手”（过程就不细写了，就是服务器和客户端交互，最终确定断开）

二。利用Socket建立网络连接的步骤

建立Socket连接至少需要一对套接字，其中一个运行于客户端，称为ClientSocket ，另一个运行于服务器端，称为ServerSocket 。

套接字之间的连接过程分为三个步骤：服务器监听，客户端请求，连接确认。

1。服务器监听：服务器端套接字并不定位具体的客户端套接字，而是处于等待连接的状态，实时监控网络状态，等待客户端的连接请求。

2。客户端请求：指客户端的套接字提出连接请求，要连接的目标是服务器端的套接字。为此，客户端的套接字必须首先描述它要连接的服务器的套接字，指出服务器端套接字的地址和端口号，然后就向服务器端套接字提出连接请求。

3。连接确认：当服务器端套接字监听到或者说接收到客户端套接字的连接请求时，就响应客户端套接字的请求，建立一个新的线程，把服务器端套接字的描述发给客户端，一旦客户端确认了此描述，双方就正式建立连接。而服务器端套接字继续处于监听状态，继续接收其他客户端套接字的连接请求。

三：优化TableView

1:在苹果的开发文档里面已经描述了重用cell的流程，在这就没有必须再重复了。
但重要的事情是：在UITableView的dataSource中实现的tableView:cellForRowAtIndexPath:方法，需要为每个cell调用一次，它应该快速执行。所以你需要尽可能快地返回重用cell实例。
不要在这里去执行数据绑定，因为目前在屏幕上还没有cell。为了执行数据绑定，可以在UITableView的delegate方法tableView:willDisplayCell:forRowAtIndexPath:中进行。这个方法在显示cell之前会被调用。

2:使用类方法，并基于传入的宽度及显示的数据来计算高度值:

重用cell实例：对于特殊类型的cell，你应该只有一个实例，而没有更多。
不要在cellForRowAtIndexPath:方法中绑定数据，因为在此时cell还没有显示。可以使用UITableView的delegate中的tableView:willDisplayCell:forRowAtIndexPath:方法。
快速计算cell高度。对于工程师来说这是常规工作，但你将会为优化复杂cell的平滑滑动所付出的耐心而获取回报。

优化UITableView中绘制数据操作的小结：

减少iOS执行无用混合的区域：不要使用透明背景，使用iOS模拟器或者Instruments来确认这一点；如果可以，尽量使用没有混合的渐变。
优化代码，以平衡CPU和GPU的负载。你需要清楚地知道哪部分渲染需要使用GPU，哪部分可以使用CPU，以此保持平衡。
为特殊的cell类型编写特殊的代码。

优化的目标是很明确的：如果在主线程中执行这些操作，则会让你不能很快地返回cell。
在后台加载图片，在相同的地方处理圆角，然后将处理后的图片指定给UIImageView。
立刻显示文本，但在后台定位#号，然后使用属性字符串来刷新显示。
在你的cell中，需要具体情况具体分析，但主要的思想是在后台执行大的操作。这可能不止是网络代码，你需要使用Instruments来找到它们。

是异步化UI的实现清单：

找到让你的cell无法快速返回的瓶颈。
将操作移到后台线程，并在主线程刷新显示的内容。
最后一招是设置你的CALayer为异步显示模式(即使只是简单的文本或图片)—这将帮你提高FPS。



