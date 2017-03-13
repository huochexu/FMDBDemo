# FMDBDemo
使用分类的方式，对fmdb三方进行封装，目标:1.整洁代码，2.降低三方藕合
1.Sqlite 语句
 1>创建表:create table if not exists test1(field1 text,field2 text,field3 text);
 
2>新增数据:insert into test1(field3,field2,field1) values('efgdfgd','2sfdgsfd222','fdfsd');

3>删除数据:delete from test1 where field1='2222' and field2='aaaaa21';

4>修改数据:update test1 set field3='aaaaaa',field4='aaaaaa' where field1='2222' and field2='aaaaa21'

5>查找数据:select * from test1 where field1='2222'

6>增加新字段:alter table test1 add column field10 text;

7>查找表:select * from tableName;

fmdb详细用法:

 1.初始化:  FMDatabase *fmdb= [FMDatabase databaseWithPath:databasePath];
 
2.打开数据库:[fmdb open]

3.更新数据方法:[fmdb executeUpdate:SQlite语句];

4.查找数据的方法:[fmdb executeQuery:SQlite语句];

5.获取表中所有字段的方法:

     FMResultSet *rs = [fmdb getTableSchema:tableName];
    NSMutableArray *titles = [NSMutableArray array];
    while ([rs next]) {
        NSString *title = [rs stringForColumn:@"name"];
        [titles addObject:title];
    }
    
6.判断是否存在某个表的方法:[fmdb columnExists:字段名 inTableWithName:表名]

7.判断表中是否拥有某个字段的方法:FMResultSet *rs = [fmdb getTableSchema:tableName]; 返回为nil则没有


8.采用分类的方式来对FMDB进行封装，来降低藕合度
