
## Initialize the project
- go to [springInitializer](https://start.spring.io/)
- ![SpringInitializer](IMGS/SpringInit.png)
- Download, extract and open with IntellijIDEA

## Connecting MySQL database
![Connect DB](IMGS/ConnectingDatabase.png)


## Create employee JPA entity

- Create a package under main package named `entity`
- inside the package create a `java class file` named `Employee`
![JPA_entity_creation](IMGS/Employee_entity_JPA.png)

## Creating Employee repository

![EmployeeRepository](IMGS/EmployeeRespository.png)

## Creating EmployeeDto and EmployeeMapper

### EmployeeDto
![EmployeeDto](IMGS/EmployeeDto.png)

### EmoloyeeMapper
![EmployeeMapper](IMGS/EmployeeMapper.png)

## Build add Employee REST API

### Creating service layer and Create Employee Method
![](employeeService.png)
![](EmployeeServiceImpl.png)
### Add Employee REST controller
![[EmployeeController.png]]

## Create get Employee REST API
#### same as create employee
`EmployeeService.java` -> `EmployeeServiceImpl.java` -> `EmployeeController.java` 
Using GET request

## Create getAllEmployee REST API
#### same as before
`EmployeeService.java` -> `EmployeeServiceImpl.java` -> `EmployeeController.java` 
Using GET Request

## Create Update Employee REST API
#### Same as before
`EmployeeService.java` -> `EmployeeServiceImpl.java` -> `EmployeeController.java`
Using PUT request