- go中使用Goroutine来实现并发concurrently。
- Goroutine是Go语言特有的名词。区别于进程Process，线程Thread，协程Coroutine，因为Go语言的创造者们觉得和他们是有所区别的，所以专门创造了Goroutine。
- Goroutine是与其他函数或方法同时运行的函数或方法。Goroutines可以被认为是轻量级的线程。与线程相比，创建Goroutine的成本很小，它就是一段代码，一个函数入口。以及在堆上为其分配的一个堆栈（初始大小为4K，会随着程序的执行自动增长删除）。因此它非常廉价，Go应用程序可以并发运行数千个Goroutines。

> Goroutines在线程上的优势。
> 
> 1. 与线程相比，Goroutines非常便宜。它们只是堆栈大小的几个kb，堆栈可以根据应用程序的需要增长和收缩，而在线程的情况下，堆栈大小必须指定并且是固定的
> 2. Goroutines被多路复用到较少的OS线程。在一个程序中可能只有一个线程与数千个Goroutines。如果线程中的任何Goroutine都表示等待用户输入，则会创建另一个OS线程，剩下的Goroutines被转移到新的OS线程。所有这些都由运行时进行处理，我们作为程序员从这些复杂的细节中抽象出来，并得到了一个与并发工作相关的干净的API。
> 3. 当使用Goroutines访问共享内存时，通过设计的通道可以防止竞态条件发生。通道可以被认为是Goroutines通信的管道。