Namespaces may be used to provide the functionality of interfaces in C++. You can have a namespace that contains function declaraions, and all namespaces that you'd want to use these functions, could provide their own implementations to it!

  ``` cpp
  namespace Parser {
  double give(bool);
  }  // namespace Parser

  namespace useParser1 {
  using namespace Parser;
  double give(bool b) { return 1.0; }
  }  // namespace useParser1

  namespace useParser2 {
  using namespace Parser;
  double give(bool b) { return 2.0; }
  }  // namespace useParser2
  
  int main(){
    double d1 = useParser1::give(true); //returns 1.0
    double d2 = useParser2::give(false); //returns 2.0
   }
```

You may keep the name of the namespace that implements the functions, to be the same as the original namespace, because at the time of compilation, the compiler will merge the two namespaces. So you can keep the (interface) namespace and (implementer) interface in separate files with the same name.
