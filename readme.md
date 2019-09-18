# YourQS - Developers' Guide

## Getting Started

Hello Aspire2 Students / Developers!

You probably landed on the **QS Collector project** from YourQS.

Here are some requirements for you to study before you start to dive into this project.

- Node.js
- Express.js
- Sequelize with support of MS SQL
- HTML / CSS / Javascript
- ES6
- Bootstrap 4


## Table of Contents

- [YourQS - Developers' Guide](#yourqs---developers-guide)
  - [Getting Started](#getting-started)
  - [Table of Contents](#table-of-contents)
  - [Machine Environment Setup](#machine-environment-setup)
  - [1.1 Installation of QS Collector](#11-installation-of-qs-collector)
  - [1.2. Coding Standards - Syntax and Naming Standards](#12-coding-standards---syntax-and-naming-standards)
  - [1.3. File Structure](#13-file-structure)
    - [1.3.1 Top-level directory structure of our QS Collector](#131-top-level-directory-structure-of-our-qs-collector)
    - [1.3.2 File Naming Convention for Controllers](#132-file-naming-convention-for-controllers)
    - [1.3.3 File Naming Convention for Views](#133-file-naming-convention-for-views)
    - [1.3.4 File Naming Convention for Models](#134-file-naming-convention-for-models)
  - [1.4. Models Visualisation](#14-models-visualisation)
  - [1.5 Extra Configurations / Setup](#15-extra-configurations--setup)
    - [1.5.1 MSSQL - SETUP](#151-mssql---setup)
    - [1.5.3 Database - Setup](#153-database---setup)
    - [1.5.4 Enable Login Access using SQL Authentication](#154-enable-login-access-using-sql-authentication)

## Machine Environment Setup

Prequisites for our web application:
1. Node 10.16.x
2. Git / Github
3. MSSQL 2017 Developer Edition & Install SMSS
    > **Note**:<br> We provided an installer for you and we prepare how you should set it up using `instructions.txt`. you can download it [here](https://drive.google.com/open?id=18WV9k-uKgz79c869GAs4QrJlXtV4Tm5S)
    
    > **After your setup is complete:** Please proceed [here](#151-mssql---setup) then [here](#153-database---setup)
4. Visual Studio Code (can be any text editor that you preferred)


## 1.1 Installation of QS Collector

1. Clone the [qs-collector](https://github.com/yourqs-team/qs-collector) repository on github.
2. Open the project on `Visual Studio Code`
3. duplicate `.env.sample` and rename the duplicated file into `.env`
4. follow these environment variables [here](https://gist.github.com/roaldjap/cb7f621d905231cd106637f5f7263e2e)
5. duplicate `config.json.sample` and rename the duplicated file into `config.json`
6. based on your setup of the database on SQL Server, you should match the credentials on `config.json`
7. run `npm install` - to install dependencies of our web application.
8. run `node_modules/.bin/sequelize db:migrate` - to migrate the database schema to your MSSQL server
  
  > **NOTE**: if you have error: failed to connect to localhost:1433.	
- please enable your tcp port by following instructions [here](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port?view=sql-server-2017)
  
- then, restart computer
  
> **NOTE**: if you have error: failed to login as 'some_user_here':

- please enable SQL Authentication & Grant Access on your user by following instructions [here](#154-enable-login-access-using-sql-authentication)
- To make sure everything is working, change your password on your 'sa' user on SQL Management Studio

9. On `.env` file, set your environment variable `SEQUELIZE_FORCE_SYNC_SCHEMA="ON"` and run 'npm start' and follow the instructions indicated <br><br>**OR** &nbsp;&nbsp;proceed on next step.

10.  Set your `SEQUELIZE_FORCE_SYNC_SCHEMA="OFF"` on your environment variables(/.env).

11.  run `node_modules/.bin/sequelize db:seed:all` - to initialize all initial data needed for the app to open
	More information about sequelize migrations [here](https://sequelize.org/master/manual/migrations.html)
12. run `npm start` - to start application

## 1.2. Coding Standards - Syntax and Naming Standards

The current project is using multiple disciplines and approach from web development world. We have different coding standards for each language that we used in the project. As a developer, you need to study some of the things here to maintain a readable code to ensure the future progress of this project.

- **Pug(HTML)**: - [https://pugjs.org/api/getting-started.html](https://pugjs.org/api/getting-started.html)
- **CSS**: - [http://getbem.com/naming/](http://getbem.com/naming/)
- **SCSS(CSS):** - [https://sass-lang.com/documentation/syntax](https://sass-lang.com/documentation/syntax)
- **Javascript**: - [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
- **Model Definitions** - https://sequelize.org/master/manual/models-definition.html

## 1.3. File Structure

### 1.3.1 Top-level directory structure of our QS Collector

    .
    ├── bin/                   # bin/ folder contains `www` which holds the server file to run `app.js`
    ├── config/                # config/ folder should contain database configuration(config.json).
    ├── controllers/           # managing the data of the application that comes from `views` to `models` and vice versa.
    ├── handlers/              # used for handling node modules and plugins that can be reused on other JS files
    ├── migrations/            # contain `sequelize` scripts for database schema
    ├── models/                # contain models we define in `sequelize` -
    ├── public/                # contain static files such as image/js/sass(css)/plugins
    ├── routes/                # contain index.js where it contains different routes for your `contollers`
    ├── seeders/               # contain scripts for generating initial data for our application
    ├── views/                 # contain your .pug(html) files / Front End
    .env.sample               # should be duplicated as `.env` and fill your environment variables/credentials
    .gitignore                # contains ignored files in git
    app.js                    # This is we invoke and initialize our `express` app / node modules and run it. 
    helpers.js                
    package-lock.json
    package.json              # scripts / dependencies for our app.
    webpack.config.json       # use it as a compiler for our static files like `sass`
  
  Our file structure was based on typical express app. Initially it was generated using `express-generator` and we architect and structured node modules needed for the development that was enlisted on inside `package.json`


### 1.3.2 File Naming Convention for Controllers
  Our `controllers/` was based on features that we implement. We define it like this `(feature)Controller.js`
  The following examples below our current features that we have on our `qs-collector` app.
  ```
  ├── controllers
        ├─ changePasswordController.js
        ├─ changeProfileController.js
        ├─ dashboardController.js
        ├─ loginController.js
        ├─ pdfGenController.js
        ├─ registerController.js
        ├─ sampleController.js          
        ├─ userController.js            # Update User Profile Feature
  ```

  inside of each controller uses different ES6 functions. we used async / await functions to avoid nested then() / catch() OR try() / catch() method chains.

  We call these methods inside `routes/index.js`. When we say `routes` we are referring to only one file. we strictly put it inside in one file for us to visualise the overall RESTful API that we used in our `qs-collector` app.

### 1.3.3 File Naming Convention for Views
  Our `views/` usually consisted a lot of webpages but using `.pug` we are able to minimize the pain of reading HTML Enclosure tags and make it readable for the incoming developers of `qs-collector`.

  Usually we call these pages coming from our `controllers` inside a function `res.render('pug_filename') - without the .pug`


  ```
    ├── views/ 
        ├─ dashboard/                 # Consists of Dashboard Components that we call in `dashboard-layout`
        ├─ email-templates/           # Email Templates that we use for email notifications
        ├─ mixins/                    # Some reusable templates that we can use to other pages
        ├─ modals/                    # modals that we can use
        ├─ pdf-templates/             # All PDF Related templates
        - dashboard-layout.pug        # Main layout for our dashboard
        - editProject.pug
        - editUser.pug
        - error.pug                   # Not Found Pages - 404 / Error Catcher.
        - forgotPasswordForm.pug
        - index.pug
        - layout.pug                  # Main layout for register / login feature.
        - login.pug
        - projects.pug
        - register.pug
  ```

### 1.3.4 File Naming Convention for Models
  We name our `models/` based on ERD that we have on [Models Visualisation](#14-models-visualisation).
  ```
    ├── models 
        ├─ Allowance_and_Insurance.js 
        ├─ Drainage.js
        ├─ Electrical.js
        ├─ Exterior.js
        ├─ Hard_landscaping.js
        ├─ index.js                      # Don't touch / edit this. We use this index.js to connect to our config/index.js dynamically.
        ├─ Interior_finish.js
        ├─ Interior_trim.js
        ├─ Joinery_allowance.js
        ├─ Manpower.js
        ├─ Other.js
        ├─ Plumbing.js
        ├─ Proffessional_service.js
        ├─ Project.js
        ├─ role.js
        ├─ Safety_requirement.js
        ├─ sessions.js                   # used to save sessions to our server side. mostly using currently in login & logout feature
        ├─ Site_arrangement.js
        ├─ Temporary_service.js
        ├─ users.js
        ├─ Windows_and_door.js  
  ```

## 1.4. Models Visualisation

YourQS Project Scope Form can have a lot of data involved. We created this visualisation in order for the team can visualise its models.

On the diagram below, shows the visualisation of relationships for each model that we define to our express app.

Each developer must be reminded that these are the foundation of our database.

<img src="extras/models-visual.jpg" style="max-width: 100%;">
<img src="extras/ERD.jpg" style="max-width: 100%;">

In a nutshell, the diagram above shows:

- A `User` can have a `Role`.
- A `User` can have multiple `Project`s
- A `Project` contains of sub-models and each of the project it can only have one:
  - `Manpower` Model -> **People And Pricing**
  - `SiteArrangement` Model
  - `SafetyRequirement` Model
  - `AllowanceAndInsurance` Model
  - `TemporaryService` Model
  - `ProfessionalServicesAllowance` Model
  - `Interior` Model
    - An `Interior` Model can only have one:
      - `WindowAndDoor` Model
      - `InteriorFinish` Model
      - `JoineryAllowance` Model
      - `Plumbing` Model
      - `Electrical` Model
      - `Drainage` Model
      - `Other` Model
  - `Exterior` Model
    - An `Exterior` Model can only have one: - `Hard LandScape` Model
      > All of the models mentioned are belongs to `Project` Model.

We designed this model architecture so that, it can be modular if some section of the project scope form needs modification.The team decided not to put it on a JSON datatype because of the limitation of MSSQL Database that was integrated to our app.

## 1.5 Extra Configurations / Setup
### 1.5.1 MSSQL - SETUP
Assuming we have successfully installed MSSQL. We will enable SQL Authentication for enable us to connect any web application to this database environment.
   1. Open MSSQL
      <br>
      <img src="extras/screenshots/open-sql.png">
   2. A modal will appear
   3. put `.` as a `Server Name` and click `Connect` Button
   4. Right Click on SQL Instance "." > Click Properties.
      <br>
      <img src="extras/screenshots/2-sql.png">
   5. A popup window will appear > under "Select a Page" list click "Security" and follow these configuration.
      <br>
      <img src="extras/screenshots/3-sql.png">

### 1.5.3 Database - Setup
  1. Create a new database.
  <img src="extras/screenshots/4-sql.png">
  2. Put your desired `Database Name`
  <img src="extras/screenshots/5-sql.png">
  3. On options set your `Collation` as `SQL_Latin1_General_CP1_CS_AS`
  <img src="extras/screenshots/6-sql.png">

### 1.5.4 Enable Login Access using SQL Authentication
   1. On right-clicking on Security/*user_name*
   2. Click Properties
   3. Go on Status and configure based on this image:
   <img src="extras/screenshots/7-sql.png">