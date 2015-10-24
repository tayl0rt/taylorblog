title: "MongoDB backup from local and restore on remote"
date: 2015-10-24 12:27:50
tags:
---

###Backing up and restoring local mongo to remote, and then connecting remote mongo to MeteorUP... in a nutshell

####So to fill you in...
I found myself feeling that I had too much going on locally, and hadn't taken the journey into remote hosting of really any kind... This is obviously important from a DevOps standpoint, and an important skill we can all have. Whether you are just getting your feet wet, or are a seasoned developer - you will always find yourself referencing stackoverflow, google, tech documentation, etc. So these are my notes from the task of migrating a DB from local to remote (mongodb), and then adding my mongo url into MeteorUP, so that my test meteor application successfully connected to the remote mongodb for it's data! Let's begin.

#####Installing/running mongo in relation to mongo itself, and also Meteor.js
Mongo Documentation was very helpful in understanding the differences in the mongo versions (2.4, 2.6, 3.0). Meteor JS info is available as well - Mongo runs it’s own separate instance on it’s own port. Your main source of help on this topic are going to be the [Mongodb docs] (https://docs.mongodb.org/manual/), and google/stackoverflow because everyone's mongo version and meteor configs, etc, are possibly going to vary. 

#####Start to get into setting up users, and learn about users and roles
Had to use the admin db in mongo - type in the mongo shell: 

    use admin 

and [Create an Administrative User with Unrestricted Access](https://docs.mongodb.org/manual/tutorial/add-admin-user/), and then was able to use:

    show dbs
     
[and create a user inside any database](https://docs.mongodb.org/manual/tutorial/manage-users-and-roles/) using: 

    use databaseName 
    
with it’s own set of control/privileges.

#####Configure mongo to accept remote connections if not already
So far have taken the comment approach (less secure) where you comment out the bind_ip line in mongod.conf file. This may be a good starting point [here](http://www.mkyong.com/mongodb/mongodb-allow-remote-access/).

#####Back up and restore mongo from local to remote
Refer to the [MongoDB documentation for mongodump / mongorestore](https://docs.mongodb.org/manual/tutorial/backup-and-restore-tools/). I did have success using mongodump and mongorestore! These next pieces of code were key:

Terminal command: 

	mongorestore —host hostname --port 27017 —username username —password password -d database -c collection /path/to/backup/file.ext
MONGO_URL for connecting mup to remote mongo instance:

	"MONGO_URL" : "mongodb://username:password@servername:port/database"
	
#####Re-deploy test Meteor App with a remote mongodb connected
Include the above "MONGO_URL" in your mup.json file and at this point remember to double check node, mongo, and phantomJS booleans and adjust as necessary!

#####And finally -
Run 
	mup [ reconfig / setup / deploy ] 
as needed, Success!

###Here are a few more links I want to leave for support on this issue - 
[MeteorUP](https://github.com/arunoda/meteor-up)

[StackOverflow page on Mongodb Error 18 - Auth fails](http://stackoverflow.com/questions/18216712/cannot-authenticate-into-mongo-auth-fails)

[StackOverflow page on Mongodb Error 111](http://stackoverflow.com/questions/24899849/connection-refused-to-mongodb-errno-111)

Those may be useful along the way, even if just to get the old brain workin'. 

###Take care for now!
