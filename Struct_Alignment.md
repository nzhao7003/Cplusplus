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
