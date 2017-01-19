# 例一:
    #include <iostream>
    using namespace std;
    struct A
    {
      char a;
      int b;
      double c;
    }S1;
    void main()
    {
      cout << sizeof(S1) << endl;
      cout << sizeof(S1.a) << endl;
      cout << sizeof(S1.b) << endl;
      cout << sizeof(S1.c) << endl;
    }
    输出结果:sizeof(S1) = 16,sizeof(S1.a) = 1,sizeof(S1.b) = 4,sizeof(S1.c) = 8
### 结论:
结构体中元素是按照定义顺序一个一个放到内存中去,但并不是紧密排列的。从结构体存储的首地址开始,每一个元素放置到内存中时,它都会认为内存是以它自己的大小来划分的,因此元素放置的位置一定会在自己字节大小的整数倍上开始(以结构体变量首地址为0计算)。    
### 图1解析:
首先系统会将字符型变量a存入第0个字节（相对地址，指内存开辟的首地址）；然后在存放整形变量b时，会以4个字节为单位进行存储，由于第一个4字节模块已有数据，因此它会存入第二个4字节模块，也就是存入到4~8字节；同理，存放双精度实型变量c时，由于其宽度为8，其存放时会以8个字节为单位存储，也就是会找到第一个空的且是8的整数倍的位置开始存储，此例中，由于头一个8字节模块已被占用，所以将c存入第二个8字节模块。


![1](https://github.com/nzhao7003/Cplusplus/blob/master/image/1.jpg)


# 例二:
    struct B
    {
        char a;
        double b;
        int c;
    }S2;
    
