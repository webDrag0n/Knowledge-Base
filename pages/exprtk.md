- #C++ #math #evaluation
- [Github repo](https://github.com/ArashPartow/exprtk)
- [官方网站](http://www.partow.net/programming/exprtk/index.html)
- ## 踩坑
	- symbol_table.add_variable() 引用传值
		- symbol_table.add_variable(var_name, var_val) 采用引用传值，需要添加多个变量时不可以用同一个变量覆盖，如：
		  ```c++
		  //错误示例
		  double var_val = 0;
		  symbol_table.add_variable("name0", var_val);
		  var_val = 1;
		  symbol_table.add_variable("name1", var_val);
		  ```
		- 在不确定需要增加的数量时可以采用vector的不同element存储var_val并传入