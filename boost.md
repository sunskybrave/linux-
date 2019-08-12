boost::function与boost::bind 的使用  
https://blog.csdn.net/pangyemeng/article/details/72865413    
手把手教你实现boost::bind  
https://blog.csdn.net/li123128/article/details/79957338  

最详细的资料  
Boost C++ 库     
https://www.cnblogs.com/lidabo/p/9294874.html   

boost安装  
https://www.cnblogs.com/cnxkey/articles/8887529.html  

```c++
#include <iostream>
#include <boost/filesystem.hpp>
#include <boost/bind.hpp>
#include <boost/function.hpp>

class Calculator {
    public:
        Calculator(){}
        int add(int a, int b) {
            return a + b;
        }
};

int add(int a, int b) {
    return a + b;
}

int main() {
    //绑定普通函数
    int a =boost::bind(add,1,1)();
    std::cout<<a<<std::endl;
    a = boost::bind(add, _1, _2)(2, 2);
    std::cout<<a<<std::endl;
    Calculator caltor;
    //绑定类成员函数
    a = boost::bind(&Calculator::add, &caltor, 3, 3)();
    std::cout<<a<<std::endl;
    a = boost::bind(&Calculator::add, _1, _2,_3)(&caltor,4,4);
    std::cout<<a<<std::endl;
    return 0;
}
```
