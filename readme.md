`**NOTE**: In Progress, there might be some changes to work on while the development of the project is ongoing`
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

## 1.1. Table of Contents
- [YourQS - Developers' Guide](#yourqs---developers-guide)
  - [Getting Started](#getting-started)
  - [1.1. Table of Contents](#11-table-of-contents)
  - [1.2. Syntax and Naming Standards](#12-syntax-and-naming-standards)
  - [1.3. File Structure](#13-file-structure)
  - [1.3. Models Visualisation](#13-models-visualisation)

## 1.2. Syntax and Naming Standards
The current project is using multiple disciplines and approach from web development world. We have different coding standards for each language that we used in the project. As a developer, you need to study some of the things here to maintain a readable code to ensure the future progress of this project.
- **Pug(HTML)**: - [https://pugjs.org/api/getting-started.html](https://pugjs.org/api/getting-started.html)
- **CSS**: - [http://getbem.com/naming/](http://getbem.com/naming/)
- **SCSS(CSS):** - [https://sass-lang.com/documentation/syntax](https://sass-lang.com/documentation/syntax)
- **Javascript**: - [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
- **Model Definitions** - https://sequelize.org/master/manual/models-definition.html


## 1.3. File Structure

`**The file structure is under construction yet. this part will change constantly while the project is ongoing**`

## 1.3. Models Visualisation
 YourQS Project Scope Form can have a lot of data involved. We created this visualisation in order for the team can visualise its models.

 On the diagram below, shows the visualisation of relationships for each model that we define to our express app.

Each developer must be reminded that these are the foundation of our database.

![Models Visualisation](extras/models-visual.jpg)



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
  - `Exterior` Model
  > All of the models mentioned are belongs to `Project` Model
- An `Interior` Model can only have one: 
  - `WindowAndDoor` Model
  - `InteriorFinish` Model
  - `JoineryAllowance` Model
  - `Plumbing` Model
  - `Electrical` Model
  - `Drainage` Model
  - `Other` Model

  > All of the models mentioned are belongs to `Interior` Model
- An `Exterior` Model can only have one: 
  - `Hard LandScape` Model