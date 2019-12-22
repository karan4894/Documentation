#######################
Information Gathering
#######################



**What is Web ?**
	- Web is the common name for the World Wide Web, a subset of the Internet consisting of the pages that can be accessed by a Web browser.

**What is difference between Web and Internet ?**
	- Internet refers to global network of servers that make the information sharing that happens over Web via web pages.

	- Web is just one of the ways that information is shared over Internet.

	- There are different web browsers, like Mozilla, Google-Chrome etc.

**What is Website ?**
	- Website is a group of globally accessible, interlinked web pages which have single domain name.
	- It can be maintained by an individual, business ,or organization.
	- Website can be static or Dynamic

**What is Web Application ?**
	- Web application is a client-side and server-side software application.
	- A web application is a software or a program which is accessible using any web browser.
	- Its front end is created using languages like HTML,CSS,Java script etc which is supported by major browsers.
	- Web application involves FRONT END - BACK END - SERVER SIDE SCRIPTING -- ALSO known as Middle layer.

**What is Web service ?**
	- Web service is a standardized way or medium to propagate communication between the client and server applications i.e different  web applications on World Wide Web.

	- Web services provide a common platform that allows multiple applications built on various programming languages to have ability to communicate with each other.

	- Web service is any piece of software that makes itself available over the Internet and uses a standardized XML messaging system.

	- So basically A. Web app --- Web service --- B. Web app communicate.

	- Web service is a standardized medium to propagate communication between the client and server application on the World Wide Web.

	- The main component of a web service is the data which is transferred between the client and and the server and that is XML.
	- XML (Extensible Mark up Language) is a counterpart to HTML and easy to understand the intermediate language that is understood by many programming languages.

	- So when Web applications talk to each other they talk in XML,
	- Web service is a collection of APIs working together to perform a particular task.



**What is XML ?**
	- XML stands for extensible markup language.
	- XML is a mark up language much like HTML.
	- XML was designed to store DATA.
	- Its a W3C Recommendation.

	- It has following 4 things.
	- Sender, Receiver , Header , Message - body.
	- Sender and Receiver information is stored in HEADER.

**Different Web Service protocols ?**
	- SOAP
	- REST

**What is API ?**
	- API stands for Application Programming Interface.
	- An API is exactly an interface between your device or application and Web Services that you are trying to communicate with.

**How can you access Web Service**?
	- Web service can be accessed using a transport protocol.
	- HTTP is a far more popular transport to send a request and get a response to and forth from a web service.

**SUMMARY**
	- Web service is a standardized medium to propagate communicate between client and server application on world wide web.
	- Its a piece of a software over the network , which defines set of protocols to communicate between web application.

	- So to make friends with any other web application, you first need to know, 
		- Do they provide Web service.
		- Check their WSDL document - i.e Web service definition Language.
		- Check their APIS - SOAP or REST
		- Access one using a scripting language.
		- Mostly python will help to achieve the task
		- Access functions and job done.

**What is difference between asynchronous and synchronous communication ?**
	- Synchronous means things are getting done in sequential order.
	- Other one wont start unless already running process is finished.
	- Asynchronous means things wont wait for process to finish and can start new process or proceed with further execution.


**What is HTTP ?**
	- HTTP is a protocol designed to transfer information between computers over WWW( World Wide Web).
	- Information transferred can be anything like, document, file , image videos etc between computers over Internet.

**What is a Framework ?**
	- Frame work or software frame work is a platform for developing software applications.
	- It takes care of everything the protocols, templates , static , scripting and all properly.

**What is GET and POST method ?**
	- GET method used only for retrieve data from the given server using a given URI.
	- A POST request is used to send data to the server, for example, customer information, file upload, etc. using HTML forms.

	- So we are Using form POST and GET in API


	
*GIT - HUB


**What is version control ?**
	- Version control is the management of changes to to documents, computer programs, large websites and other collections of information.
	- These changes are usually termed as Versions.
	- It keeps older version and newer version of projects intact.

**Git ? **
	- Git is a version control tool.
	- Distributed Version control system
	- Distributed computing is a field of computer science that studies distributed systems.
	- A distributed system is a system whose components are located on different networked computers, which communicate and coordinate their actions by passing messages to one another.
	- Flow chart 
	- Workstation --Commit and update --> Git --push and pull--> Repository(server)
	- Workstation --> Local Repo --> Server Repo.
	- Git pushes files on central server

** Centralized systems ? **
	- Centralized systems are systems that use client/server architecture where one or more client nodes are directly connected to a central server.
	- Where client sends the request to the server and gets the response back.  E.g Wiki pedia

** Decentralized systems ? **
	- Every node makes its own decision. The final behavior of the system is the aggregate of the decisions of the individual nodes.
	- You can say Bitcoins as one example.
	- Decentralized system - like bit coins , where no single entity or organization owns bit coin network.The network is a sum of all the nodes who talk to each other for maintaining the amount of bit coin every account holder has.
	- Final system is aggregate of all the decisions of individual nodes.


** Distributed System ? **
	- In distributed systems components of computer are located on different network and they have a common communication link.
	- eg : Google search - Many computers are connected to give response back, not necessary that main server has to reply.

	** Features of GIT **
		- Compatible 
		- Distributed 
		- Branching
		- Lightweight 
		- Speed 

** Git hub commands ? **
	- git init
	- git remote add origin " link " -- Added Central repo to local repo--e.g Read me
	- git pull origin master
	- git status 
	- make changes 
	- Git add file name / git add -A
	- Git commit -m "" / git commit -a " message"

	- git branch branch name
	- git checkout branch name - for going into that branch
	- now going in destination, you can merge
	- in master branch -- git merge first branch / branch name

	- Re-base does the same work as merging, so no need to worry.
	- git push origin master
	- git push origin branch name 
	- Done git 


	