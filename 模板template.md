# 模板template

```c++
#include<iostream>
#include<string>

template<typename T>
void Print(T value)
{
	std::cout<< value <<std::endl;    
}

int main()
{
    Print(1);
    print("Hello");
    std::cin.get;
}
    
```

未调用时不创建包含模板的函数

只有调用模板时才创建

typename/class：模板参数类型

Print<type> (T value); 



## 类（template）

```c++
template<typename T, int N>

class Array
{
private:
    T m_array[N];
public:
    int GetSize() const { return N; };
}

int main()
{
    Array<int, 5> array_1;
    std::cout << array_1.GetSize() << std::endl;
}
```

