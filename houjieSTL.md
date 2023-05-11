所谓泛型编程（Generic Programming,GP），是指使用templates（模板）为主要工具来编写程序。STL是泛型编程最成功的作品。

STL六大部件：
- 容器（Containers）
- 分配器（Allocators）
- 算法（Algorithms）
- 迭代器（Iterators）
- 适配器（Adapters）
- 仿函式（Functors）

算法复杂度，大 O 记法

1. 序列容器：
    - array，元素数目固定
    - vector，单向增长
    - deque, 双向增长
    - list，双向链表
    - forward-list，单向链表
2. 关联容器;
    - set/multiset，红黑树实现，set元素不能重复，multiset可重复
    - map/multimap，红黑树实现，map中key不能重复

tuple 和 pair 的使用场景,值创建之后**不可更改**
```C++
#include <iostream>
#include <utility>

std::pair<int, int> divide(int dividend, int divisor) {
    int quotient = dividend / divisor;
    int remainder = dividend % divisor;
    return std::make_pair(quotient, remainder);
}

int main() {
    int dividend = 10;
    int divisor = 3;
    std::pair<int, int> result = divide(dividend, divisor);
    std::cout << "Quotient: " << result.first << ", Remainder: " << result.second << std::endl;
    return 0;
}
```

```C++
#include <iostream>
#include <tuple>

// 函数返回多个值
std::tuple<int, std::string, double> getPerson() {
    int age = 25;
    std::string name = "Alice";
    double height = 1.75;
    return std::make_tuple(age, name, height);
}

// 函数参数的传递
void printPerson(const std::tuple<int, std::string, double>& person) {
    int age;
    std::string name;
    double height;
    std::tie(age, name, height) = person;
    std::cout << "Name: " << name << ", Age: " << age << ", Height: " << height << std::endl;
}
```