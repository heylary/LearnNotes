# 1. 基础架构：sql查询语句如何执行

![img](D:\WorkData\MarkdownData\assets\0d2070e8f84c4801adbfa03bda1f98d9.png)

**MySQL可以分为Server层和存储引擎层两部分。**

##  Server层

Server层包括连接器、查询缓存、分析器、优化器、执行器等

### 连接器

连接器负责跟客户端建立连接、获取权限、维持和管理连接

### 查询缓存

MySQL拿到一个查询请求后，会先到查询缓存看看，之前是不是执行过这条语句，但不建议使用查询缓存

query_cache_type设置成DEMAND，这样对于默认的SQL语句都不使用查询缓存

### 分析器

分析器先会做“词法分析”,判断你输入的字符代表SQL语句中的什么

再做“语法分析”，判断你输入的语句是否满足MYSQL的语法

### 优化器

优化器是在表里面有多个索引的时候，决定使用哪个索引

### 执行器

如果有权限，就打开表继续执行。打开表的时候，执行器就会根据表的引擎定义，去使用这个引擎提供的接口。



##  存储引擎层

存储引擎层负责数据的存储和提取，不同的存储引擎共用一个**Server层**

# 2. 日志系统：sql更新语句如何执行

