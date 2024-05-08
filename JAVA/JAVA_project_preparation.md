
## Initialize the project
- go to [springInitializer](https://start.spring.io/)
- ![SpringInitializer](/IMGS/SpringInit.png)
- Download, extract and open with IntellijIDEA

## Connecting MySQL database
![Connect DB](/IMGS/ConnectingDatabase.png)


## Create employee JPA entity

- Create a package under main package named `entity`
- inside the package create a `java class file` named `Employee`
![JPA_entity_creation](/IMGS/Employee_entity_JPA.png)

## Creating Employee repository

![EmployeeRepository](/IMGS/EmployeeRespository.png)

## Creating EmployeeDto and EmployeeMapper

### EmployeeDto
![EmployeeDto](/IMGS/EmployeeDto.png)

### EmoloyeeMapper
![EmployeeMapper](/IMGS/EmployeeMapper.png)

## Build add Employee REST API

### Creating service layer and Create Employee Method
![](/IMGS/employeeService.png)
![](/IMGS/EmployeeServiceImpl.png)
### Add Employee REST controller
![](/IMGS/EmployeeController.png)

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
![](/IMGS/createAndSetupReact.png)

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
![](/IMGS/helloWorldJSX.png)
### Using the jsx
![](/IMGS/usingJSX.png)


## Adding Bootstrap using NPM
- In the terminal `npm install bootstrap --save`
- import CSS file in main.jsx 
```js
import 'bootstrap/dist/css/bootstrap.min.css'
```

## List Employee Feature React front-end implementation
![](/IMGS/frontEndImplementationSteps.png)

![](/IMGS/ListEmployeeComponentJSX.png)
### Inside app.jx

![](/IMGS/EmployeeListinAppJSX.png)

## Connect front-end with REST API
using Axios
`npm install axios --save`

![](/IMGS/EmployeeServiceJS.png)

### List employee component JSX
![](/IMGS/frontToBack.png)


## Adding Header and Footer
#### Header
![](/IMGS/HeaderComp.png)

#### Footer 
![](/IMGS/FooterComp.png)

# Configure Routing

![](/IMGS/RoutingSteps.png)

- `npm install react-route-dom --save`
- import this in `App.jsx`
```js
import {BrowserRouter} from 'react-router-dom'
```

![](/IMGS/routing.png)
## Add employee route and navigate 
![](/IMGS/addEmployeeInAppJSX.png)

#### Change in LIstEmployeeComponent (button add and navigator)
![](/IMGS/addEmployeeInList.png)

## Add Employee form
![](/IMGS/addEmployeeFormSteps.png)

![](/IMGS/employeeComponentImpl.png)

## Add Employee connect to REST API
![](/IMGS/AddEmployeeRESTConnect.png)

![](/IMGS/employeeComp.png)

![[empService2.png]]![[appafterForm.png]]

## Add Employee form validation
![[formValidationSteps.png]]

**EmployeeComponent.jsx**
```jsx
import React, { useState } from 'react'
import { createEmployee } from '../services/EmployeeService'
import { useNavigate } from 'react-router-dom'

const EmployeeCompont = () => {

    const [firstName, setFirstName] = useState('')
    const [lastName, setLastName] = useState('')
    const [email, setEmail] = useState('')
    const navigator = useNavigate()

    const [errors, setErrors] = useState({
        firstName: '',
        lastName: '',
        email: ''
    })

    function saveEmployee(event) {
        event.preventDefault();

        if(validateForm()){
            const employee = {firstName, lastName, email};
            // console.log(employee);

            createEmployee(employee).then((response) => {
                console.log(response.data);
                navigator('/employee');
            }).catch((err) => {
                console.log(err);
            });
        }

        
    }

    function validateForm() {
        let valid = true;

        const errorsCopy = {... errors};

        if(firstName.trim()){
            errorsCopy.firstName = '';
        } else {
            errorsCopy.firstName = "First name is required";
            valid = false;
        }

        if(lastName.trim()){
            errorsCopy.lastName = "";
        } else {
            errorsCopy.lastName = "Last name is required";
            valid = false;
        }

        if(email.trim()){
            errorsCopy.email = "";
        } else {
            errorsCopy.email = "Email is required";
            valid = false;
        }

        setErrors(errorsCopy);
        return valid;
    }


  return (
    <div className='container'>
        <br /> <br />
        <div className="row">
            <div className="card col-md-6 offset-md-3 offset-md-3">
                <h2 className="text-center">Add Employee</h2>
                <div className="card-body">
                    <form >
                        <div className="form-group mb-2">
                            <label  className="form-label">First Name</label>
                            <input 
                                type="text" 
                                placeholder='First name'
                                name='firstName'
                                value={firstName}
                                onChange={(event) => setFirstName(event.target.value)}
                                className={`form-control ${ errors.firstName ? 'is-invalid':'' }`}
                             />
                             { errors.firstName && <div className='invalid-feedback'> { errors.firstName }</div>}
                        </div>

                        <div className="form-group mb-2">
                            <label  className="form-label">Last Name</label>
                            <input 
                                type="text" 
                                placeholder='Last name'
                                name='lastName'
                                value={lastName}
                                className={`form-control ${ errors.lastName ? 'is-invalid':'' }`}
                                onChange={(event) => setLastName(event.target.value)}
                             />
                            { errors.lastName && <div className='invalid-feedback'> { errors.lastName }</div>}
                        </div>

                        <div className="form-group mb-2">
                            <label  className="form-label">Email</label>
                            <input 
                                type="text" 
                                placeholder='abc@def.com'
                                name='email'
                                value={email}
                                className={`form-control ${ errors.email ? 'is-invalid':'' }`}
                                onChange={(event) => setEmail(event.target.value)}
                             />
                            { errors.email && <div className='invalid-feedback'> { errors.email }</div>}
                        </div>

                        <button className='btn btn-success' onClick={saveEmployee}>Submit</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
  )
}

export default EmployeeCompont
```
