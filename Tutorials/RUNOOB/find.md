## 语法
```sh
find path -option [-print] [-exec -ok command] {} \;
```

## 实例
查找文件（默认递归）  
```
find / -name '*.h'
```

查找全名
```
find . -wholename './*/20*' -type d
```
