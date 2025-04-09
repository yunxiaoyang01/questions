# 问题
```go
package main  
  
import (  
 "fmt"  
 "reflect"  
 "unsafe"  
)  
  
func main() {  
  
 var s1 []int  
 s2 := make([]int,0)  
 s4 := make([]int,0)  
   
 fmt.Printf("s1 pointer:%+v, s2 pointer:%+v, s4 pointer:%+v, \n", *(*reflect.SliceHeader)(unsafe.Pointer(&s1)),*(*reflect.SliceHeader)(unsafe.Pointer(&s2)),*(*reflect.SliceHeader)(unsafe.Pointer(&s4)))  
 fmt.Printf("%v\n", (*(*reflect.SliceHeader)(unsafe.Pointer(&s1))).Data==(*(*reflect.SliceHeader)(unsafe.Pointer(&s2))).Data)  
 fmt.Printf("%v\n", (*(*reflect.SliceHeader)(unsafe.Pointer(&s2))).Data==(*(*reflect.SliceHeader)(unsafe.Pointer(&s4))).Data)  
}
```
上述代码**nil切片和空切片指向的地址一样吗？这个代码会输出什么？**
# 怎么答
 - nil切片和空切片指向的地址不一样。nil空切片引用数组指针地址为0（无指向任何实际地址）
 - 空切片的引用数组指针地址是有的，且固定为一个值
 
 