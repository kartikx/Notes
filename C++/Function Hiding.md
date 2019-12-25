 Consider the following example:

``` cpp
  struct B {
    int f( int );
    int f( double );
    int g( int );
  };

  struct D : public B {
  private:
    int g( std::string, bool );
  };

  D   d;
  int i;
  d.f(i);    // ok, means B::f(int)
  d.g(i);    // error: g takes 2 args
``` 

Initially it looks that ```d.g(i)``` should refer to the public method g inherited from ```struct B```, however surprisingly enough, a compiler error is thrown. 
Actually, when we declare a function named g in the derived class D, it automatically __hides__ all functions with the same name in all direct and indirect base classes. Take note that the function is hidden, not __deleted__.
Notice that the compiler did not consider overloading in this case. You defined a function with the same name, but different argument lists, yet the inherited function wasn't considered.

  Of course, there are the two usual ways around the name-hiding problem in Example 2a. First, the calling code can simply say which one it wants, and force the compiler to look in the right scope:
  ```cpp
  D   d;
  int i;
  d.f(i);    // ok, means B::f(int)
  d.B::g(i); // ok, asks for B::g(int)
  ```
Second, and usually more appropriate, the designer of class D can make B::g visible with a using-declaration. This allows the compiler to consider B::g in the same scope as D::g for the purposes of name lookup and subsequent overload resolution:
  ```cpp
  struct D : public B {
    using B::g;
  private:
    int g( std::string, bool );
  };
  ```
Either of these gets around the hiding problem in the original example code.

[Source](http://www.gotw.ca/publications/mill08.htm)
