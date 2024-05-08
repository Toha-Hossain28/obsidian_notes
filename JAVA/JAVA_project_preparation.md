
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

## Create Delete Employee REST API

#### Same as before
`EmployeeService.java` -> `EmployeeServiceImpl.java` -> `EmployeeController.java`
Using DELETE request


# Create and Setup React APP
1. install node js
2. create a folder
3. open with vs code 
4. in the terminal : `npm create vite@latest project_name`
5. `cd project_name`
6. `npm install`
7. `npm run dev`
8. change the port to 3000
![](IMGS/createAndSetupReact.png)

## React app project structure
#### package.json
##### Stores all the dependencies

#### vite.config.js
##### Development server details and plugins

#### node_modules folder
##### stores the node modules
#### public folder
##### stores all the static files


### New jsx file
![](IMGS/helloWorldJSX.png)
### Using the jsx
![](IMGS/usingJSX.png)


## Adding Bootstrap using NPM
- In the terminal `npm install bootstrap --save`
- import CSS file in main.jsx 
```js
import 'bootstrap/dist/css/bootstrap.min.css'
```

## List Employee Feature React front-end implementation
![](IMGS/frontEndImplementationSteps.png)

![](IMGS/ListEmployeeComponentJSX.png)
### Inside app.jx

![](IMGS/EmployeeListinAppJSX.png)

## Connect front-end with REST API
using Axios
`npm install axios --save`

![](IMGS/EmployeeServiceJS.png)

### List employee component JSX
![](IMGS/frontToBack.png)


## Adding Header and Footer
#### Header
![](IMGS/HeaderComp.png)

#### Footer 
![](IMGS/FooterComp.png)

# Configure Routing

![](IMGS/RoutingSteps.png)

- `npm install react-route-dom --save`
- import this in `App.jsx`
```js
import {BrowserRouter} from 'react-router-dom'
```

![](IMGS/routing.png)
## Add employee route and navigate 
![](IMGS/addEmployeeInAppJSX.png)

#### Change in LIstEmployeeComponent (button add and navigator)
![](IMGS/addEmployeeInList.png)

## Add Employee form
![](IMGS/addEmployeeFormSteps.png)

