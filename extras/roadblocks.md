## Roadblocks:
- Setup our own starter files 
	> We created and designed our own architectural/starter files needed for this project:
		> using Sequelize connecting with MSSQL
		> connecting different plugins needed for this project
			> connect-session-sequelize
		> seperate configurations for production and development

- Can't connect Sequelize to MSSQL properly
	> Further setup is needed like: SQL 
		> Researched on net: Enable TCP / IP for SQL Server
			> it is still doesn't proceed from our configuration
		> Ended up solution: Enable SQL Authetication

- Sequelize doesn't detect instanceMethod / classMethods created from models
	> Researched on internet - nothing works.
	> Ended up Solution : Patch Sequelize to : 5.15.2 and use findOne selection