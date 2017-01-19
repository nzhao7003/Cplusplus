# 例一:
    #include <iostream>
    using namespace std;
    struct A
    {
      char a;
      int b;
      double c;
    }AA;
    void main()
    {
      cout << sizeof(AA) << endl;
      cout << sizeof(AA.a) << endl;
      cout << sizeof(AA.b) << endl;
      cout << sizeof(AA.c) << endl;
    }
    输出结果:sizeof(AA) = 16,sizeof(AA.a) = 1,sizeof(AA.b) = 4,sizeof(AA.c) = 8
### 结论:
结构体中元素是按照定义顺序一个一个放到内存中去,但并不是紧密排列的。从结构体存储的首地址开始,每一个元素放置到内存中时,它都会认为内存是以它自己的大小来划分的,因此元素放置的位置一定会在自己字节大小的整数倍上开始(以结构体变量首地址为0计算)。    


![1](https://github.com/nzhao7003/Cplusplus/blob/master/image/1.jpg)
