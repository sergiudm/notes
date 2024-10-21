# 1.data layout
## 1.1 AoS and SoA
### 1.1.1 intro:
AOS（Array of Structures）和SOA（Structure of Arrays）是两种不同的数据结构布局方式，它们描述了结构体（`struct`）在内存中的存储方式。
#### AOS（Array of Structures）
AOS，即结构体数组，是一种数据布局方式，其中结构体类型的数组被存储在内存中。每个结构体成员按照其在结构体定义中的顺序存储，结构体数组的每个元素都是结构体的一个实例。
例如：
```c
struct person {
    char name[50];
    int age;
    float height;
};
struct person employees[10];
```
在这个例子中，`employees`是一个包含10个`person`结构体的数组。如果`person`结构体有10个这样的实例，那么整个数组将占用10倍于`person`结构体大小的内存。
#### SOA（Structure of Arrays）
SOA，即数组结构体，是一种不同的数据布局方式，其中结构体的成员被存储为数组。每个结构体成员都是一个数组，且这些数组可能在内存中连续存储。
例如：
```c
struct person {
    char name[50];
    int age[10];
    float height[10];
};
struct person employees;
```
在这个例子中，`employees`是一个`person`结构体，其中`name`是字符数组，`age`和`height`是整数和浮点数数组。如果`employees`结构体中有10个这样的实例，那么整个结构体将占用`name`数组大小的内存加上`age`和`height`数组大小的内存。
#### 选择AOS或SOA
选择AOS或SOA取决于数据的使用方式。AOS通常更简单，因为它直接映射到结构体的字段。SOA可能在某些情况下更高效，特别是当数组的长度很大，且结构体的其他字段占用很少或没有内存时。SOA还可以通过减少结构体的大小来减少内存碎片。
在实际编程中，选择哪种布局方式通常取决于特定的应用需求和优化目标。

## 2.

