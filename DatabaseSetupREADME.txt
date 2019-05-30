/**
 Initial database setup for SENG2050 Assignment 3
 
 You may need to check for any whitespace or tabs I accidently added if copying and pasting from here.
 
 If using the MySQL databases created for us on the uni computers then you won't need to create a database.
 Just follow the first steps in the Lab 06 & 07 worksheet. If you are using your own local MySQL, then 
 create a database using the following command.
*/
	
	CREATE database Assignment3;

/**
 Use the following command to create a table for user accounts. 
 
 This table stores the account information needed to login to the system. Each username needs to be unique.
 Passwords can just be stored in plaintext for now (not sure if they need to be hashed or anything). Value in
 the corresponding 'role' column is the accounts authorisation that is assigned to them upon logging in.
*/

	CREATE table users (
	username VARCHAR(20) PRIMARY KEY,
	password VARCHAR(20),
	role ENUM('client', 'staff')
	);

/**
 Use the following command to add two accounts to the users table.
 
 One each for 'client' and 'staff' roles. For simplicity, usernames for these accounts are their roles and
 their passwords are just 'password'.
*/

	INSERT INTO users VALUES ('staff', 'password', 'staff'),
				 ('client', 'password', 'client');

/**
 Use the following command to create a table to store data relating to submitted issues.
 
 'Title' must be unique. 'submittedBy' is set to the username of the user who submitted the issue. 'description' is
 the explanation of the issue, which I have set as (for now) VARCHAR(256) meaning it can be a maximum of 256 characters in
 length. This is something we need to make sure of during input validation. 'subCategory' should also be an ENUM once we
 have determined what they are. 'knowledgeBase' is set a Boolean however -> "Bool, Boolean: These types are synonyms for 
 TINYINT(1). A value of zero is considered false. Non-zero values are considered true." This needs to be considered when
 executing queries that update this value.
*/

	CREATE table issues (
	title VARCHAR(50) PRIMARY KEY,
	submittedBy VARCHAR(20),
	description VARCHAR(256),
	dateSubmitted datetime,
	dateResolved datetime,
	category ENUM('network', 'software', 'hardware', 'email', 'account'),
	subCategory VARCHAR(20),
	state ENUM('new', 'in progress', 'completed', 'resolved'),
	knowledgeBase Boolean
	);

/**
 Use the following command to create a dummy entry for an issue.
 
 'dateResolved' is initially set to null and 'knowledgeBase' is initially set to 0 (false).
*/

	INSERT INTO issues VALUES ('this is the title of the issue', 'client', 'this is the description of the issue', '2019-05-27 14:09:25', null, 'network', 'subcategory', 'new', 0);

/**
 Use the following command to create a table to store extra information about a user account.
 
 'username' maps to 'username' in users table. This table may be useful for the contact client etc. features.
*/

	CREATE table userinfo (
	username VARCHAR(20) PRIMARY KEY,
	firstName VARCHAR(20),
	lastName VARCHAR(20),
	email VARCHAR(256),
	phone int
	);

/**
 Use the following command to create a dummy entry for user account with username 'client'.
*/

	INSERT INTO userinfo VALUES ('client', 'john', 'doe', 'johndoe@gmail.com', 0123456789);

/**
 Use the following command to create a table containing comments created by a user.
 
 'issueTitle' maps to 'title' in 'issues' table. 'submittedBy' maps to 'username' in 'users' table. 'body' is the
 actual comment made by the user and like 'description' in the 'issues' table will need to ensured not to exceed the
 character limit set here.
*/

	CREATE table comments (
	issueTitle VARCHAR(50),
	submittedBy VARCHAR(20),
	body VARCHAR(256),
	dateSubmitted datetime
	);

/**
 Use the following command to create a dummy entry in the 'comments' table.
*/

	INSERT INTO comments VALUES ('this is the title of the issue', 'client', 'this is the body of the comment', '2019-05-27 14:55:34');

/**
 Connecting to a database with Java Database Connectivity (JDBC) is explained in Lecture 5a and Lab 06 and 07 worksheet.
*/
