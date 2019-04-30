
build.gradle

```groovy
    greendao {
        schemaVersion 1 // 数据库schema版本
    }
```  
- schemaVersion： 数据库schema版本，也可以理解为数据库版本号
- daoPackage：设置DaoMaster 、DaoSession、Dao包名
- targetGenDir：设置DaoMaster 、DaoSession、Dao目录
- targetGenDirTest：设置生成单元测试目录
- generateTests：设置自动生成单元测试用例
##### @Entity注解
- schema：告知GreenDao当前实体属于哪个schema
- active：标记一个实体处于活动状态，活动实体有更新、删除和刷新方法
- nameInDb：在数据中使用的别名，默认使用的是实体的类名
- indexes：定义索引，可以跨越多个列
- createInDb：标记创建数据库表
###### 属性注解
- @Id :主键 Long型，可以通过@Id(autoincrement = true)设置自增长
- @Property：设置一个非默认关系映射所对应的列名，默认是的使用字段名 举例：@Property (nameInDb="name")
- @NotNul：设置数据库表当前列不能为空
- @Transient ：添加次标记之后不会生成数据库表的列
###### 关系注解
- @ToOne：定义与另一个实体（一个实体对象）的关系
- @ToMany：定义与多个实体对象的关系
