在 C++ 中，`map` 是标准模板库（Standard Template Library, STL）中的一个关联容器，它提供了一种存储键值对（key-value pairs）的方式。`map` 基于红黑树（一种自平衡二叉搜索树）实现，因此它能够保持元素的有序性，按照键（key）的顺序进行排序。

`map` 的主要特点包括：

1. **有序性**：`map` 中的元素按照键的顺序进行排序，这使得你可以进行高效的范围查询和迭代。

2. **唯一性**：`map` 中的键必须是唯一的。如果你尝试插入一个已经存在的键，`map` 会拒绝这个插入操作，除非你使用 `insert` 方法的返回值来检查插入是否成功。

3. **快速查找**：由于底层的二叉搜索树结构，`map` 提供了对元素的快速查找、插入和删除操作，时间复杂度通常为 O(log n)。

4. **类型要求**：`map` 的键类型必须支持比较操作，通常需要重载 `<` 运算符。值类型可以是任何类型，但通常与键类型不同。

`map` 的基本操作包括插入、查找、删除和遍历。以下是一些使用 `map` 的示例：

```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    // 创建一个 map，键类型为 std::string，值类型为 int
    std::map<std::string, int> wordCount;

    // 插入键值对
    wordCount["apple"] = 1;
    wordCount["banana"] = 2;
    wordCount["cherry"] = 3;

    // 查找元素
    auto search = wordCount.find("banana");
    if (search != wordCount.end()) {
        std::cout << "Found 'banana' with count " << search->second << std::endl;
    } else {
        std::cout << "Did not find 'banana'" << std::endl;
    }

    // 删除元素
    wordCount.erase("apple");

    // 遍历 map
    for (const auto& pair : wordCount) {
        std::cout << pair.first << ": " << pair.second << std::endl;
    }

    return 0;
}
```

在这个例子中，我们创建了一个 `map`，其中存储了单词及其出现次数。我们使用 `find` 方法来查找特定的键，并使用 `erase` 方法来删除键。最后，我们通过范围基于的 for 循环来遍历整个 `map`。

`map` 是 C++ 中非常有用的数据结构，它在需要有序存储和快速查找的场景中特别有用。