- #C++ #math #evaluation
- [Github repo](https://github.com/ArashPartow/exprtk)
- [官方网站](http://www.partow.net/programming/exprtk/index.html)
- ## 踩坑
	- symbol_table.add_variable(var_name, var_val) 采用引用传值，需要添加多个变量时不可以用同一个变量覆盖，如：
	  ```c++
	  //错误示例
	  double var_val = 0;
	  symbol_table.add_variable(var_name, var_val);
	  symbol_table.add_variable("name2)
	  ```