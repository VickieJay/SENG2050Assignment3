# SENG2050Assignment3
Currently we've decided to use MVC to model and attempt to split the workload of the assignment.
## Models
###User
#### Member variables
username : String
password : String
role : Enum (client, staff)
email : String
#### Member methods

###Issue
#### Member variables
uniqueID : int
title : String
submittedBy: String //Username
description : String //size?
dateSubmitted : Datetime
dateResolved : Datetime
category : Enum
subcategory : Enum //optional?
state : Enum
knowledgeBase : Boolean
#### Member methods

###Comment
#### Member variables
uniqueID : int
value : String
dateSubmitted : dateTime
issueID : int
replyTo : int //default NULL

#### Member methods