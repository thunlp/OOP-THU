# OOP-THU
OOP Material &amp; QA





### L2-封装与接口-2019
PPT第13页，```struct { char *name; } anon_u;```只定义了一个指针变量，未使用new分配空间，从该指针地址开始读入可能会出错```cin >> as[0].id.name; ```,可修改为```struct { char name[17]; } anon_u;```



### L3-创建与销毁-2019
PPT第26页，```Test t2 = t1;```调用了拷贝构造函数来构造t2，故不会使得count++;

PPT第32页， 常量静态数据成员和静态数据成员一样，满足访问权限的任意函数均可访问，~~但都不能修改~~, 常量静态数据成员不能被修改


