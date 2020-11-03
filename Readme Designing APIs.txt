Designin Restful API

	Complete understanding of the business
	
	Decide which functionality to expose
	Decide how to expose it
	Decide best ways to expose it
	Test and (in)validate assumptions
	
	API design is really hard
	

	Strategies
	
		1-Bolt-on strategy
			Apply for existing systems
			
			Benefits
				Brute force appoach 
				It's the fastest way to get something useful
				Takes advantage of existing code and systems
				
			Cons(drawbacks)
				Problems in application/architecture usually affects the API
				
		2-Greenfield Strategy
			Apply for new systems
			
			Benefits
				Generally the API first or mobile first approach
				Takes advantage of new technologíes
				MOtivates the team (they'll work with new techs)
				
				
			Cons(drawbacks)	
				Often requires massive upfront investment before any benefit appear
			
			
		3-Facade Strategy
			Recommended approach mix between bolt-on and greenfield
			Replacing system piece by piece (component by component)
			
			Benefits	
				Ideal for legacy systems as the application remains functional
				
			Drawback
				Can be challenging to have "multiple mindsets" in the system
				Difficulties to try to replicate a behavior

				
	API Modeling tips	

		1-Don't worry about the tools
			Jira, trello, chose whatever the tool fit better to your process/methodology 
			
		2-Have a consistent process/methodology
			Determine an establish a good process (roles, responsabilities, etc)
			
		3-It doesn't count unless it's written down
			Document everything
			Decisions, assumptions
			Deferred tasks
			Everything that might be important in a few months
			
			
	Modeling business process
	
		1-Identify participants
			Who will use the API
				People
				Entities
			Who/what is involved in our business process
				Anyone who starts/initiates an action	
				
			What do we need to know
				Who are they
				Are internal or external
				Are the active or passive participants
				
			Be carefull of your boundaries
				Identify what are you responsible of what third parties or others are.
				
				
		2-Identify activities
		3-Break into steps
		4-Create API definitions
			Creating and groupig methods
				Identify resources (find the nouns)
					i.e cart, items, customers
				Identify verbs
					Read, List, View -> GET
					Create, Add, Checkout, Cancel -> Post, sometimes is used to change status/states and more
					Update -> Put
					Delete, Clear -> Delete
				Identify relationships	
					Independent
						Movies, actors
					Dependent
						Characters in movies
					Associative
						One actor pleys multiple characters
						One character played by multiple actors
				
			
		5-Validate your API
			Use a microframework 
				hapi.js for node
				Sinatra for ruby
				Slim or Silex for PHP
			Accept incoming requests
			Validate methods(verbs) and URL patterns	

			Document the API's 
				List the end points	
				List the parameters
			
		
	
		Not necessary the API match 100%  with the database
		Maybe the business process is differento, so be careful in expose all the DB schema as API'schema
		
		
		
HTTP Headers
		
	curl -I https://api.github.com
	
HTTP Status
		DON'T CREATE CUSTOM STATUS

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
	
Content-Type
	text/html
	application/json
	
Media-type
	format=json


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
	
	6-UNIFORM INTERFACES
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
	
		6.4-HYPERMEDIA AS THE ENGINE OF APPLICATION STATE (HATEOAS)
			Once a client has access to a REST services it should be able to discover all
			available resources and methods through the hyperlinks provided	
			With every returned resource, the service should describe the resources and methods available	
				GET,PUT,PATCH
				
			curl https://api.github.com	
			
	
API design Patterns	
	Authentication (AuthN) - Authorization (AuthZ)
	AuthN -> Who you are	
	AuthZ -> What you can do
	
	API Keys
		Benefits
			Independent of a framework or a programming language
			Easy to add as a header or even to the URL (unsafer)
		Cons(drawbacks)
			The credential will be log everywhere
				Not a secret!
				
	Don't create your own AuthN/AuthZ protocol
				
	
	OAuth 2.0	
		The recommended solution
		Benefits
			Reliable and well established
			Big ecosystem (tools, docs, etc)
			Open source and commercial options
		Cons(drawbacks)
			Complicated and not easy to implement the first time	
			
	
Versioning
	Two ways
		Using Accept Header
			Content negociation
			Establish the markup notation (json or xml)
			Establish the media type (structure of the markup)
			
		Using Resource URL
		
		
Choosing media types and processing content
			
	Collection+JSON
		Designed specifically to deal with groups or collection of resources
		CAn also represent single items as a set of one
		In use and some helper libraries and examples

	Hypertext Application Language (HAL)
		It can also use JSON
		Separates the payload in two parts:
			data
			links

Documentation
	Wikimedia
	Confluence
	Slate
		https://docs.slatejs.org/
		You can create rich text editors
		Easy to configure and deploy	
		
SDK
	If you use http properly and an established JSON media type
		Simple HTTP library
		JSON parser
		That should be enough
		
		
		
			
			
		
		
		

		
	
			
	
	
	

	


	
	
	
	
		