# 记录

## 对文件中的markdown的理解
1. ucore 操作系统lab1对Makefile进行解析(1) : [link](https://blog.csdn.net/weixin_35834894/article/details/108822091) 
2. ucore 操作系统lab1对Makefile进行解析(2) : [link](https://blog.csdn.net/weixin_35834894/article/details/108822938) 

## 指令记录
1. which    
Linux which命令用于查找文件。   
which指令会在环境变量$PATH设置的目录里查找符合条件的文件。
    + 例如：查找qumu命令的路径： which qumu

2. makefile中的call指令
+ 含义：调用makefile中定义的函数，并传递参数
+ 用法：```$(call funname, param1, param2,...)```    
    makefile as below：
    ```makefile
    define target
	    echo $0 
	    echo $1
	    echo $2
    endef
 

    all:
	    $(call target,hello, world)
 

    clean:
	    $(call target,clean)	
    ```

3. makefile中的call指令
+ 含义：过滤函数，过滤掉不符合要求的字符串
+ 用法：    
    ```$(filter PATTERN…,TEXT)```     
    过滤掉字串“TEXT”中所有不符合模式“PATTERN”的单词    
    makefile as below： 
    ```makefile
    sources := foo.c bar.c baz.s ugh.h 
    foo: $(sources) 
    cc $(filter %.c %.s,$(sources)) -o foo 
    ``` 
    输出：foo.c, bar.c, baz.s

4. makefile中的if指令
+ 含义：通过判断条件，返回对应的数据
+ 用法：    
    ```$(if CONDITION, THEN-PART, ELSE-PART)```     
    如果CONDITION为ture，返回THENPART，若为false，返回ELSE_PART     
    makefile as below：
    ```makefile
    SUBDIR += $(if $(SRC_DIR),$(SRC_DIR),/home/src) 
    ```
    如果“SRC_DIR”变量值不为空，则将变量“SRC_DIR”指定的目录作为一个子目录；否则将目录“/home/src”作为一个子目录