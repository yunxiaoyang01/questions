# 问题
字符串转成byte数组，会发生内存拷贝吗？
# 怎么答
字符串转成切片，会产生拷贝。严格来说，只要是发生类型强转都会发生内存拷贝。那么问题来了。  
频繁的内存拷贝操作听起来对性能不大友好。**有没有什么办法可以在字符串转成切片的时候不用发生拷贝呢？**
# 代码实现
```go
package main  
  
import (  
 "fmt"  
 "reflect"  
 "unsafe"  
)  
  
func main() {  
 a :="aaa"  
 ssh := *(*reflect.StringHeader)(unsafe.Pointer(&a))  
 b := *(*[]byte)(unsafe.Pointer(&ssh))    
 fmt.Printf("%v",b)  
}
```
# 解释
- `StringHeader` 是`字符串`在go的底层结构。
- 