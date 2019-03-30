# OOP-THU
OOP Material &amp; QA





### L2-封装与接口-2019
PPT第13页，```struct { char *name; } anon_u;```只定义了一个指针变量，未使用new分配空间，从该指针地址开始读入可能会出错```cin >> as[0].id.name; ```,可修改为```struct { char name[17]; } anon_u;```



### L3-创建与销毁-2019
PPT第26页，```Test t2 = t1;```调用了拷贝构造函数来构造t2，故不会使得count++;

PPT第32页， 常量静态数据成员和静态数据成员一样，满足访问权限的任意函数均可访问，~~但都不能修改~~, 常量静态数据成员不能被修改

PPT第39页， 尽量少用全局对象，不推荐例子中
```
void foo() {
    input.doSomething();
}
Input input;
int main() {
	foo();
}
```
input的定义应在foo函数之前。

### L4-引用与复制-2019
第42页std::move的描述有误，具体参见https://www.zhihu.com/question/50652989

```
class Complex {
public:
    string Name;
    Complex(string s="empty"):Name(s){}
    ~Complex(){printf("del %s\n",Name.c_str());}
};
Complex Func(Complex c){
    Complex tmp("tmp");
    return tmp;
}
```
在开启返回值优化(RVO)时，tmp变量是否被析构取决于调用，若函数返回值用于赋值的话不会被析构。

不会被析构：
```
int main(){
    Complex a=Func(Complex("c"));
    a.Name="a";
}
```
程序输出:
```
del c
del a
```

会被析构：
```
int main(){
    Complex a;
    Func(Complex("c"));
    a.Name="a";
}
```
程序输出:
```
del tmp
del c
del a
```
感谢小教员@董博文的注解


### L5-组合与继承-2019
第20页相对于最初原版本(少数人下载了最初版本)，新增基类构造函数的参数默认值不会被派生类继承。默认值会导致产生多个构造函数版本，但都会被派生类继承。
基类构造函数只定义：```Base(int i, int j=1) {}``` 能让 ```Derive obj(356); Derive obj2(356,789);```编译通过                            


