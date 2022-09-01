- #架构
- 参考资料
	- [[游戏架构设计]]
- {{renderer code_diagram,mermaid}}
	- ```mermaid
	  erDiagram
	  CUSTOMER ||--o{ ORDER : places
	  ORDER ||--|{ LINE-ITEM : contains
	  CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
	  ```
-