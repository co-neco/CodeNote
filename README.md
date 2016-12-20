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
