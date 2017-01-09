# C++判断字符串是否全是数字
## 方法一:判断字符的ASCII范围（数字的范围为48~57）
 #include <iostream>
  using namespace std;  
  bool AllisNum(string str);   
  int main( void )  
  {  
    string str1 = "HelloWorld";  
    string str2 = "1990";  
    if (AllisNum(str1))
    {
      cout<<"str1 is a num"<<endl;  
    }
    else
    {
      cout<<"str1 is not a num"<<endl;  
    }

    if (AllisNum(str2))
    {
      cout<<"str2 is a num"<<endl;  
    }
    else
    {
      cout<<"str2 is not a num"<<endl;  
    }

    cin.get();
    return 0;  
  }
  bool AllisNum(string str)  
  {  
    for (int i = 0; i < str.size(); i++)
    {
         int tmp = (int)str[i];
         if (tmp >= 48 && tmp <= 57)
         {
             continue;
         }
         else
         {
             return false;
         }
     } 
     return true;
 }
## 方法二:使用C++提供的stringstream对象
  #include <iostream>
  #include <sstream>  
  using namespace std;   
  bool isNum(string str);   
  int main( void )  
  {
     string str1 = "HelloWorld";  
     string str2 = "1990";  
     if(isNum(str1))  
     {  
         cout << "str1 is a num" << endl;  
     }  
     else
     {  
         cout << "str1 is not a num" << endl;   
     }  
     if(isNum(str2))  
     {  
         cout<<"str2 is a num"<<endl;  
     }  
     else
     {  
         cout<<"str2 is not a num"<<endl;   
     }   
     cin.get();
     return 0;  
 }   
 bool isNum(string str)  
 {  
     stringstream sin(str);  
     double d;  
     char c;  
     if(!(sin >> d))  
     {
         return false;
     }
     if (sin >> c) 
     {
         return false;
     }  
     return true;  
 }
# CString/string区别及其转化
 利用MFC进行编程时,我们从对话框中利用GetWindowText得到的字符串是CString类型,CString是属于MFC的类.
 而一些标准C/C++库函数是不能直接对CString类型进行操作的.
## 1.CString和string的转化
    string str="Hello";
    CString cstr(str.c_str());//或者CString cstr(str.data());初始化时才行
    cstr=str.c_str();或者cstr=str.data();
    str=cstr.GetBuffer(0); //CString->string
    cstr.format("%s", str.c_str()); //string->CString
    cstr.format("%s", str.data()); //string->CString
    str = LPCSTR(cstr); //CString->string
    /*c_str()和data()区别是：前者返回带'/0'的字符串，后者则返回不带'/0'的字符串*/
## 2.CString和int的转换
    int i=123;
    CString str;
    str.format("%d",i);//int->CString 其他的基本类型转化类似
    i=atoi(str);//CString->int 还有(atof,atol)
## 3.char*和CString的转换
    CStringcstr="Hello";
    char* ptemp=cstr.getbuffer(0);
    char* str;
    strcpy(str,ptemp);//CString->char*
    cstr.releasebuffer(-1);
    char*str="World";
    CStringcstr=str;//char*->CString string类型不能直接赋值给CString
