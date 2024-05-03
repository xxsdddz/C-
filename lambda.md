## lambda

匿名函数（不通过函数定义）

函数指针（）

**[capture] (variable) {body}**

```c++
#include <iostream>
#include <vector>

void Read(const std::vector<int>& values, void(*func)(int))
{
    for (int value : values)
        func(value);
}

int main()
{
    std::vector<int> values = { 1,4,2,7,5 };
    Read(values, [](int value) {std::cout << "values:" << value << std::endl;});
    std::cin.get();
}
```

or

```c++
auto lambda = [](int value){std::cout << "value:" << value << std::endl;};
Read(values, lambda);
```

### 捕获[]

传入外部变量

[=] : 按值全部捕获传入 

[&] ：按引用全部捕获传入

[&a] / [a]

允许函数对捕获变量修改：mutable

[&] (int value) mutable {std::cout  <<  "value:" <<  a  <<  std::endl;};



**!!! lambda捕获变量时不能使用原始函数指针（**它不能简单地转换为一个函数指针，因为函数指针不携带任何状态信息。）**

1.std::function (#include < functional >)

```c++
void Read(const std::vector<int>& values, std::function<void(**type)>& func)
```

2.直接传递lambda表达式；

3.模板

```c++
template<typename Callable>

void callFunction(Callable&& func) 
{
    func(); // 完美转发Callable对象
}
```



查找

```c++
#include <algorithm>
std::vector<int> values= {1, 2, 5, 4, 7};
auto it = std::find_it(values.begin(), values.end(), [](int value){return value > 3;});
std::cout << *it << std::endl;
```



