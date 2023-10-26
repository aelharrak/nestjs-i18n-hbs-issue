
## Sumary :

* [Project architecture and overview](#overview)

* [Prerequisite](#prerequisite)
  * [Git](#git)
  * [Node Js](#node)
  * [Yarn](#yarn)
  * [Mongodb](#mongodb)
  
* [Setup Project](#setup-project)
  * [Clone project](#clone)
    * [Front-end](#front)
        * [Directory structure ](#front-struct)  
        * [Description of each repository ](#front-desc)          
        * [setup project ](#front-setup)  
        * [install dependencies ](#front-dependencies) 
        * [Start project](#front-Start)  
        * [access to project](#front-access) 
    * [Back-end](#back)
        * [Directory structure ](#back-struct)  
        * [Install dependencies ](#back-Install)  
        * [Start project ](#back-Start)  
        * [access to project ](#back-access)  
    * [Mongodb](#Mongodb)
        * [Database installation](#Mongodb-installation)
        * [start mongodb service](#Mongodb-service)
        * [use mongo shell](#Mongodb-shell)
        * [Database configuration ](#Mongodb-configuration)
    
## Project architecture / overview

Frameworks list


Database :

     - MongoDB
     
Third party :

    - keycloak
      
## Requirement

#### 1.Git:

Download and install the latest stable version (currently: 2.39.2)

> Windows : https://git-scm.com/download/win

> Linux/Unix : https://git-scm.com/download/linux

> macOS : https://git-scm.com/download/mac
     

#### 2.Node js:

Note : v16

    https://nodejs.org/en/blog/release/v16.18.1

Check that the installation is successful by running:

    node -v
    npm -v

#### 3.Mongodb database:
     https://www.mongodb.com/try/download/enterprise

#### 4.Yarn :

Yarn is a package manager that doubles down as project manager.
Whether you work on one-shot projects or large monorepos,
 as a hobbyist or an enterprise user, 
we've got you covered.

    npm install --global yarn


## Clone project:

```git
  git clone ssh://git-codecommit.eu-west-3.amazonaws.com/v1/repos/arch_pilote
```

#### 1. Directory structure :

```
arch_pilote
│  ├─ log
│  │  └─ debug
│  │  └─ info
│  ├─ public   
│  │  ├─ assets
│  │  │  └─ css
│  │  │  └─ js
│  │  │  │  └ app.js
│  │  │  │  └─ ...
│  │  │  └─ fonts
│  │  │  │  └─ ...
│  │  │  └─ images
│  │  │  │  └─ ...
│  │  │  └─ js
│  │  │  │  └─ ...
│  │  │  └─ json
│  │  │  │  └─ ...
│  │  │  └─ lang
│  │  │  │  └─ ...
│  │  │  └─ libs
│  │  │  │  └─ ...
│  ├─ src
│  │  ├─ authentication
│  │  │  └─ base.css
│  │  ├─ common
│  │  │  └─ middleware
│  │  │    ├─   logger.middleware.ts
│  │  │    └─ http-exception.filter
│  │  └ app.controller.spec.ts
│  │  └ app.controller.ts
│  │  └ app.module.ts
│  │  └ app.service.ts
│  │  └ main.ts
│  ├─ views
│  │  └─ errors
│  │  ├─ 401.hbs
│  │  ├─ 404.hbs
│  │  └─ 500.hbs
│  │  └─ layouts
│  │  │  └─ template.hbs
│  │  └─ partials
│  │  │  ├─  header.hbs
│  │  │  ├─  footer.hbs
│  │  │  └─ ...
│  │  ├─ index.hbs
│  ├─ .env
│  ├─ .eslintrc.js
│  ├─ .prettierrc
│  ├─ nest-cli.json
│  ├─ package.json
│  ├─ postcss.config.js
│  ├─ README.md
│  ├─ tailwind.config.js
│  ├─ tailwind.sh
│  ├─ tsconfig.build.json
│  ├─ tsconfig.json
│  └─ ...
```


#### 2. Description of each repository:


##### public/assets/cfg/index.js file : 
    to load environment variables like db, port, keycloak, ...

###### Note: /!\ Make sure keycloak is started and configured before starting the front end project, otherwise you will get an empty page with a loader !

##### assets : 
    In this directory, we are going to store all assets files. (Here we want to save fonts, icons, images, styles etc.

##### layouts (Handlebars files): 
```
A Handlebars layout is an HTML page used to set underlying meta-data or general structure for other HTML pages in the application. 
It acts as a container with a placeholder which you can inject dynamic data into.
```
##### partials (Handlebars files):
```
A partial refers to a piece of HTML pre-saved because it appears across several HTML files. For example, navbars and footers. 
You can store that content in one file and include it when necessary.

As with your static and HTML files, you’ll also have to set a partials directory in your app.engine configuration object.
```
You can access a partial using the partial call syntax. In double curly braces, enter a greater than symbol (>) followed by the name of the partial.

For example:
```
{{> nameOfPartial}}  
```
    
#### 3. setup project :

into project folder execute the following cmd :
```bash
$ yarn install
```

####  4. Running the app

```bash
# development
$ yarn run start

# watch mode
$ yarn run start:dev

# production mode
$ yarn run start:prod
```


#### 5: access to project:
The first page load is the dashboard it's an example with the default implemented template ( Velzon - Admin & Dashboard )

## Frontend 

 > http://localhost:5000 

## test : backend 

 > http://localhost:5000/home

result on the browser :
    
    {
      "code": 200,
      "message": "message here !"
    }

## Test

#### unit tests
```bash

$ yarn run test

 PASS  src/app.controller.spec.ts
  AppController
    root
      ✓ should return 200 (7 ms)
      ✓ should return message here ! (1 ms)

Test Suites: 1 passed, 1 total
Tests:       2 passed, 2 total
Snapshots:   0 total
Time:        1.679 s, estimated 2 s
Ran all test suites.
Done in 1.97s.

```

#### test coverage
```

$ yarn run test:cov

$ jest --coverage
 PASS  src/app.controller.spec.ts
  AppController
    root
      ✓ should return 200 (7 ms)
      ✓ should return message here ! (2 ms)

---------------------------|---------|----------|---------|---------|-------------------
File                       | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
---------------------------|---------|----------|---------|---------|-------------------
All files                  |   20.27 |        0 |      30 |   17.74 |                   
 src                       |   28.84 |      100 |    37.5 |      25 |                   
  app.controller.ts        |    90.9 |      100 |   66.66 |   88.88 | 16                
  app.module.ts            |       0 |      100 |       0 |       0 | 1-59              
  app.service.ts           |     100 |      100 |     100 |     100 |                   
  main.ts                  |       0 |      100 |       0 |       0 | 1-49              
 src/common/middleware     |       0 |        0 |       0 |       0 |                   
  http-exception.filter.ts |       0 |        0 |       0 |       0 | 1-20              
  logger.middleware.ts     |       0 |      100 |       0 |       0 | 1-8               
---------------------------|---------|----------|---------|---------|-------------------
Test Suites: 1 passed, 1 total
Tests:       2 passed, 2 total
Snapshots:   0 total
Time:        5.246 s
Ran all test suites.
Done in 5.56s.


```

### Mongodb
#### Database installation
      sudo apt-get install mongodb

Note: click on Y to allow the installtion 

next :

      sudo apt-get update

#### start mongodb service

      sudo service mongodb start

#### use mongo shell

execute the following CMD on your terminal

      mongo

to display all installed databases 

      show dbs;

create / switch to the database :

      use mydbexample 

to check the used database :

      db;

use collection :

      db.collectionname.function({"key","value"})

#### Database configuration :

the configuration of the mongodb database name, host and port should be managed in the .env file

note: enable option MongoDB when the system boots

      sudo systemctl enable mongodb

## Creat a new Ressource
#### Generating a new resource
To create a new resource, simply run the following command in the root directory of your project:

    nest g resource nameHere


    // choose  REST API  click enter

nest g resource command not only generates all the building blocks (module, service, controller classes) but also an entity class, DTO classes as well as the testing (.spec) files.


> HINT : To avoid generating test files, you can pass the --no-spec flag, as follows: nest g resource nameHere --no-spec


### More ... :

> /!\ : To check your modules are exposed please verify in the console, otherwise you got 404 when you try to call any new Module :

```
amine@amine-VivoBook-ASUSLaptop-X421EAY-K413EA:~/dev/EldoSoft_Stack_NodeJS_Model$ yarn start
 yarn run v1.22.19
 $ nest start
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [NestFactory] Starting Nest application...
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] AppModule dependencies initialized +23ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] MongooseModule dependencies initialized +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] HttpModule dependencies initialized +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] ThrottlerModule dependencies initialized +0ms
 http://localhost:7777
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] ConfigHostModule dependencies initialized +1ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] WinstonModule dependencies initialized +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] ConfigModule dependencies initialized +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] AuthenticationModule dependencies initialized +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] HelloModule dependencies initialized +1ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] MongooseCoreModule dependencies initialized +8ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] MongooseModule dependencies initialized +4ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [InstanceLoader] Test3Module dependencies initialized +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RoutesResolver] HelloController {/dashboard}: +14ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/dashboard, GET} route +1ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/dashboard/test3, GET} route +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/dashboard/test, GET} route +1ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RoutesResolver] Test3Controller {/test3}: +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/test3, POST} route +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/test3/:id, PUT} route +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/test3, GET} route +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/test3/:id, GET} route +1ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [RouterExplorer] Mapped {/test3/:id, DELETE} route +0ms
 [Nest] 1108750  - 03/21/2023, 12:15:38 PM     LOG [NestApplication] Nest application successfully started +2ms
 Application is running on : 5050
```


## Stay in touch
> Website - eldo.fr (https://eldo.fr)
## 
# nestjs-i18n-hbs-issue
