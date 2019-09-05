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

## Setup

Prequisites for our web application:
1. Node 10.16.x
2. Git
3. MSSQL 2017 Developer Edition & Install SMSS
    >Note: We provided an installer for you. you can download it [here]()
4. Visual Studio Code (can be any text editor that you preferred)

> After Installing MSSQL, We will enable SQL Authentication
1. Open MSSQL **opening on start button image will be placed here
2. A modal will appear ** image here
3. put "." as a Server Name and click Connect Button
4. Right Click on SQL Instance "." > Click Properties ** image here
5. A popup window will appear > under "Select a Page" list click "Security" and follow these configuration.


## 1.1. Table of Contents

- [YourQS - Developers' Guide](#yourqs---developers-guide)
  - [Getting Started](#getting-started)
  - [Setup](#setup)
  - [1.1. Table of Contents](#11-table-of-contents)
  - [1.2. Syntax and Naming Standards](#12-syntax-and-naming-standards)
  - [1.3. File Structure](#13-file-structure)
  - [1.4. Models Visualisation](#13-models-visualisation)
  - [1.5. Setup](#13-models)
## 1.2. Syntax and Naming Standards

The current project is using multiple disciplines and approach from web development world. We have different coding standards for each language that we used in the project. As a developer, you need to study some of the things here to maintain a readable code to ensure the future progress of this project.

- **Pug(HTML)**: - [https://pugjs.org/api/getting-started.html](https://pugjs.org/api/getting-started.html)
- **CSS**: - [http://getbem.com/naming/](http://getbem.com/naming/)
- **SCSS(CSS):** - [https://sass-lang.com/documentation/syntax](https://sass-lang.com/documentation/syntax)
- **Javascript**: - [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
- **Model Definitions** - https://sequelize.org/master/manual/models-definition.html

## 1.3. File Structure

`**The file structure is under construction yet. this part will change constantly while the project is ongoing**`

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
