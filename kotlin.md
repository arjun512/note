`::`  


`Int::times`  int 的内部方法 times

`fold` 集合fold(起始值，表达式) 表示集合每个元素执行表达式 ，可以用来做集合加法，乘法，阶乘

`launch`  启动一个协程

`suspend` 是一个可挂起函数关键字

`async`  `await` 库函数

`internal` 相当于Java 中 `protected` 的功能，同一模块中的任何地方可见

`static` kotlin 使用 伴生对象的方式呈现,`companion`

###### 数据类的表现

- 主构造函数应该至少有一个参数；

- 主构造函数的所有参数必须标注为 val 或者 var ；

- 数据类不能是 abstract，open，sealed，或者 inner ；

- 数据类不能继承其它的类（但可以实现接口）。
```kotlin
data class User(var age: Int): View.OnClickListener {
    override fun onClick(v: View?) {
        TODO("not implemented") //To change body of created functions use File | Settings | File Templates.
    }
}  

val jane = User( 35)
val (age) = jane //这种声明式取属性
println("$age age")
```
