- #架构
- 参考资料
	- [[游戏架构设计]]
- {{renderer code_diagram,mermaid}}
	- ```mermaid
	  erDiagram stroke:#eeeeee
	      CAR ||--o{ NAMED-DRIVER : allows
	      CAR {
	          string allowedDriver FK "The license of the allowed driver"
	          string registrationNumber
	          string make
	          string model
	      }
	      PERSON ||--o{ NAMED-DRIVER : is
	      PERSON {
	          string driversLicense PK "The license #"
	          string firstName
	          string lastName
	          int age
	      }
	  ```
-