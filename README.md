# OOP-THU
OOP Material &amp; QA





## L2-封装与接口-2019
PPT第13页，```struct { char *name; } anon_u;```只定义了一个指针变量，未使用new分配空间，无法```struct { char name[17]; } anon_u; ```,可修改为```struct { char name[17]; } anon_u;```
