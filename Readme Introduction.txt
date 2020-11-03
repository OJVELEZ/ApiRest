REST Representation State Transfer
	Group of software architecture, design contraints that bring efficcient, reliable and scalable systems
	
	REST allows to create 
		Single page aplications
			Send an URI to the server
			Only loads/modify the data that changed it doen's have to load the entire page again
			
		Native Apps	
			
	Everything is controlled by an API	
	
	
API Application Program Interface

	Set of features and rules that exist inside a software program enabling interaction between the software and other items (software or Hardware)
	
	GET
	PUT
	DELETE
	

The Rest is the librarian and the API is the language


URI
	Universal Resource Identifier
		Sequence of character that identify a virtual or physical resource
		Provides a simple and extensible means for identifying a resource
	
	Examples of URI's	
	
		https://restful.dev/posrt/5
		ftp:///server/files/doc1.txt
		mailto:ovelez@beto.com
		tel:1111
		urn:library:names_authors:mrh
		library:names:authors:mrh


URN
	Universal resource name
	It's also a subset of URI
	The difference between URL and URN, it's that URN is an unique name identifier, like the name of a person
		A lot Oscar
		But only one Oscar J Velez R
		The people can have the secureness that are talking with the appropiate one
		But they don't know where I am localed
		To find me it's necessary the URL
			The URL provides the exact physical location
		
		URN = linkedin.com/in/ojvelez/
			Unique name
			
			host
				linkedin.com
				DNS conversion to an	
					IP address
			
			resource path		
				/in/ojvelez/
				
			default resources
				if you put a folder automatically will look for:
					index.html
					default.htm
			
			Optional	
				URL query
					?id=11445
					ate the end of the URN
				
			
		URL = https://www.linkedin.com/in/ojvelez/
			How: by http
			Provides the IP using DNS
			
		BOTH THE URN AND URL ARE URI			
					
		
URL
	Universal Resource Locator
		Subset of URI
		Identifies a resource and explain how to access that resource providing	an explicit method
			https
			http
			ftp
			
	PROTOCOL + URN
		 https://www.linkedin.com/in/ojvelez/

			
	All the URL's are URI's
	But not all URI's are URL's



SIX CONTRAINTS OF REST
	1-CLIENT-SERVER architecture
		Client manage the UI
		Server manage data storage
		Rest server
			Client1
			Client2
			Client3
		Serves the data without worry and know about the technologies of the client	
		In conclusion, we have a complete separation between the content (data) and it's presentation and interaction
	
	2-STATELESSNESS
		No client context or informacion, aka State, can be stored on the server between request (only if the client asks for it)
		Stateless
		The client is responsible for keeping track its own session state 
		All requests sent from a client must be self-contained and complete
		Client
			Server here it's state 1 give me state 2
		Server:
			I don't care, here the state you want
		The server can store information in database or others of the data sended by the client for an specific time
		For example:
			The client ask to the server to store an authentication token for a set period of time
			To allow authentication requests
			
	3-CACHEABILITY
		All REST responses must be clearly marked as cacheable or not cacheable
		The server deliver the data and marked it as cacheable or not
			Server: Keep it for 5 days and after forget it
			Client: ok
	
	4-LAYERED SYSTEMS
		The system must be designed so the client cannot know and shouldn't care whete it's connected directly to
		the server or to an intermediary like a CDN, mirror, ELB, API Gateway, etc
		Ensures scalability and improves the security overall
	
	5-CODE ON DEMAND
		Servers are allowed to transfer executable code like javascript and compiled componentes to clients
		It's an uncommon use
		Server provides source code to the client and the client executes it
	
	6-UNIFORM INTERFACE
		6.1-RESOURCE IDENTIFICATION IN REQUEST
			Must use URI
			The URI request must specify what resource it is looking for 
			And what format the reponse should use
				Client:
					Give me post #4 in Json Format
				Server: 
					Here you go
		
		6.2-RESOURCE MANIPULATION THROUGH REPRESENTATIONS
			Once a client has a representation of a resource, it can modify or delete the resource
		
		6.3-SELF-DESCRIPTIVE MESSAGES
			Sending a receiveing data, each representation must describe its own data format
	
		6.4-HYPERMEDIA AS THE ENGINE OF APPLICATION STATE
			Once a client has access to a REST services it should be able to discover all
			available resources and methods through the hyperlinks provided	
			With every returned resource, the service should describe the resources and methods available	
				GET,PUT,PATCH
	
		
Rest doesn't depends of HTTP, however, most of the services use this protocol, for example the Restful
It's possible to create a rest service using ftp or smtp
HTTP -> RESTful API
	Service using Http
	The service accomplish the six constraints
	That converts the service in RESTful API
	
	
Limits
		Who can access what
		Which capabilities are granted
		How many requesdt the can make in a set time period
		For example Twitter API
		
		
http://reqres.in/
	RESTful API (use http and respect the 6 constraints)
	For tests/POCS
	To test you can wirte in a browser the URL for example
		https://reqres.in/api/users
		It returns a list of user in json format, but not weel formatted as postman
		
	Good Redst clients
		Postman
		Insomnia  (Insomnia.rest)
		VS Code (rest Client)
			create an *.http file
			GET https://reqres.in/api/users
				Send request or Right click
			To add another service in the same file
				###
				

		
		
Methods Resource URI
	Methods are the standard http operators
		GET
		POST
		PUT
		PATCH
		DELETE
		OPTIONS
		HEAD
		
	URI
		
	When you consume a method of a Restful API it returns:
		Header
			Content-Type: application/json; charset=utf-8
			Cache-Control: max-age=14400
			Age: 4751
			Authorization: Basic "!#REDFDSAFDSFasd
			Host:appsite.dev
			Server: cloudflare
			
	When you send a message to a RESTful API
		You have to establish a header, similar to the return
		Usually the client or programming language manages a lot of this automatically
		
Discovery
	What resources and methods are available
	OPTIONS URI
	

Resource
	The key abstraction of information in REST is a resource.
	Any information that can be named can be a resource.
	A document or image, a temporal service, a collection of other reources, etc...
	
	When you consume a service you ask for a resource
		Resource collection
			"All red books"
			Bookcase/books/red
				The data contained at the end of the URI is the resource
		Resource singleton	
			"Red book number 4"
			Bookcase/books/red/4
				The data contained at the end of the URI is the resource
			
			
Representation
	REST components perform actions on a resource by using a representation
	to capture the current or intented state of that resource and
	transfering that representation between components
	
	Representation -> Copy of the resource in that specific moment
	That representation can be modifed to fit specifications
	
	
Methods (aka verbs)
		GET
			Get the specifed resource
				200 OK
				404 Not found
			I want to get what is at the end of the URI
			Each time you use browser you are using GET
		POST
			Create a new resource and add it to a collection
			Send data 
			200 Created
			401 Unathorized
			409 Conflict (if the resource already exists)
			404 Not found
		PUT
			Update (all the content except the ID) an existing singleton resource based on Identifier
			If the ID dones not exists, in some cases the resource it's created
			200 OK
			401 Unathorized
			404 Not found			
			405 Method Not Allowed
		PATCH
			Modify (only a part/patch) an existing singleton resource based on Identifier
			MOdify not replaced the resource
			Requires an authentication header
			200 OK
			401 Unathorized
			404 Not found			
			405 Method Not Allowed			
		DELETE
			Delete a singleton resource based on ID
			200 OK
			401 Unathorized
			404 Not found	
		OPTIONS
			Get the options and description (methods and more) of the communication for the target resource
			200 OK
		HEAD	
			Just the response headers from the resource
			200 OK
			404 Not found				
			
		TRACE 
			Create a loopback for the request message
			200 OK
		
	In general POST, PUT, PATCH	in some APIS are the same in aother are very different	
			
Head Section
	Used not for user, intead is used for the Rest Client 
	It will vary, depends on the method and the type of resource
	Usually the first line of the header:
		HTTP/1.1 200 OK
		Protocol + http status message/code
	After Metadata
		Date
		Server
		Content type (application/json; charset=UTF-8)
		transfercoding
		caching

HTTP Status Messages/Codes
		All the status in: https://es.wikipedia.org/wiki/Anexo:C%C3%B3digos_de_estado_HTTP
		1XX Information
			Not very uncommon
			Information about status of the servers or services

		2XX Success
			200 OK
			201 Created
			202 Accepted
			204 No content

		3XX Redirection (move from the original URL)
			301 	Moved permanently
			302/303 Found at this other URL
			307 	Temporary redirect
			308 	Permanent redirect (Resume incomplete)
		
		4XX Client Error
			400 Bad request (format or paramethers are wrong)
			401 Unauthorized
			403 Forbidden
			404 Not found
			405 Method not allowed myabe you are tryng to use a method post that only receives get
			
		5XX Server Error
			500 Internal server error
			502 Bad gateway
			503 Service unavailable

Authorization/Authentication
	When you use methods like OPTIONS or HEAD, they return:
		Access-Control-Allow-Origin: *
		Access-Control-Allow-Methods: GET,HEAD,PUT,PATCH,POST,DELETE
		Which and what methods are allowed and from where
		
	You can send user and password using Authorization header
		HEAD https://reqres.in/api/users
		Authorization: Basic ovelez 1234	
		
		In the real world you will use JWT
		
		When you login using the authorization header is usual than the Access-Control-Allow-Methods increase
			more methods will be allowed
		
GET https://reqres.in/api/users?id=1
		
		
		
		
			
		
			
			

	
	
			
	
			
		
	
	

	



	
	

		
	
	
	
	
	