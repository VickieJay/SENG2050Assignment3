# SENG2050Assignment3
Currently we've decided to use MVC to model and attempt to split the workload of the assignment.
## Models  
### User  
#### Member variables  
username : String  
password : String  
role : Enum (client, staff)  
email : String  
#### Member methods  

### Issue  
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

### Comment  
#### Member variables  
uniqueID : int  
value : String  
dateSubmitted : dateTime  
issueID : int  
replyTo : int //default NULL  

#### Member methods

## Views
All these pages will use a jsp to determine the display and frontend of the page.  
- Login  
- Home  
- Issue List  
- View Issue  
- Create Issue  
- Knowledge Base  
- View Article  

## Controllers
Not sure how to split up controllers usefully or if it is even necessary. 
At the very least each page has a corresponding controller servlet.