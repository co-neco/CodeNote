# CodeNote
There is something valueable for me,which took me much time off and brought much experience to me.

### 1.Something about Wreorder warning.
When we write constructor's implemention,we should pay attention to the order that we declare variables.

eg:
class Box {
private:
    int a;
    int b;
public:
    Box(int n):b(n++),a(n++){}
    void show(){
        cout << a << b << endl;
    }
};

There, we write a class called Box.When we define a Box instantiate like this: Box k(3),
how much do you think the value of a and b?
The answer is that a equal to 3 and b equal to 4.
although we write the initializtion like this:b(n++),a(n++),but the order initializing them is the order what we declare them.

### 2.Why can template only be implementated in header file?
When I use a header file to write template class,and the implementation in cpp,there is many errors like this:undefined reference to ....
After that,I look up about much time,but no satisfied answer(which says not including .h to the main cpp).
Last,stackoverflow gives me a perfect answer,so I want to share the URL:http://stackoverflow.com/questions/495021/why-can-templates-only-be-implemented-in-the-header-file

and the reason is that although we write implementation in cpp,the code won't be created by compiling that cpp file.

eg:there are some files.
foo.h
declares the interface of class MyClass<T>
declares the interface of class Box
foo.cpp
defines the implementation of class MyClass<T>
defines the implementation of class Box
bar.cpp
uses MyClass<int>
uses Box

When foo.cpp is compiled,the corresponding code won't be generated.So when compiler compiles bar.cpp and wants to create a MyClass<int>,it can't see MyClass<T>(can only see the interface in foo.h) and create Myclass<int>.However,the Box's code can be created.Because when compiling foo.cpp,the code of Box has already been created.
