**1. vector<int>::size_t and Templates**

 You've probably seen this in a lot of good code:

   ```cpp
    vector<int>::size_t x;
   ```
          
 ```size_type``` is a (static) member type of the type ```vector<int>```.
  Usually, it is a typedef for ```std::size_t```, which itself is usually a typedef for ```unsigned int``` or ```unsigned long     long```.
 
 So in the above declaration, we have declared x to be a variable that is suitable to hold the size of a vector.
 
 
 
 You may further wanna typedef ```vector<int>::size_t``` , for ease.
 
 For eg. when using template functions:
 ```cpp
		template<class T>
		T findMedian(vector<T> x){
		typedef typename vector<T>::size_t vec_size;
		vec_size size = x.size();
		...
		}
 ```
 
 
 To understand where and why we use [typename](https://stackoverflow.com/questions/610245/where-and-why-do-i-have-to-put-the-template-and-typename-keywords)
 
Also when we use template functions, we restrict the use of that function by only those data types that conform to any constraints imposed by operators used within that function definition.
 