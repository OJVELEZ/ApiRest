HTTP
	Hyper text transfer Protocol
	
	Protocol: Set of rules that allow communication and information exchange
	Hypertext: web documents
	
	It's Plain lenguage and human readable
	
	It's a stateless protocol, is NOT sessionless
		Each request is unique
		No request connected with another request
		If cliente/server need to share state it should be sended in the headers of the request
	
	Allow Sessions
		Stored states shared between the browser and the server
		Cookies: Browser and server exchange information where the visitor is in the sequence	
			When you reload the page the browser send the cookie to the server
				"Last time we spoke the lasr picture we saw was the third"
			
		
	HTTP Headers
		Can carry additional information
			What type of cliente sent the request
			Server configuration
			Time and date of the response
			Duration of data storage
			Cookies
			
	
	It's based on request/response pairs
	
	Versions
		Http/1.1 (30-20% percent of the web transactions)
			Uncompressed headers
			Transfer one file at a time
			No default encryption
			
		Http/2 (70-80% percent of the web transactions)
			It's faster and more secure
			It uses compression algoritms
			It requires an encrypted connection 
	
	
		when it's https, it uses http/2 and when it fails, the http/1.1 unencrypted is used

	Terminology
		Browser
		User Agent - Applicatio acting as an user, tipically a browser
		TCP Transmission Control Protocol
			One of the main internet protocols
			Email
			FTP
			Remote administration
		Proxy
			Software or HArdware the acts as a middle person between clients and servers
		Method/verb
			get,post,put,patch,head,options,delete
			
		IP, URL, DNS, Server
		
	Connection
		First the browser opens a TCP connection 
			If it's https, TSL certificates are exchanged
			Only the PC and the server can decrypt the transmitted data
		Browser send a message to the server using a method (get, put, or another)	
			It can contain header with cookies, authentication data, etc
		
		Server execute the requested actions and returns a response to the browser
			Return the resources (html, javascript, CSS)
			
		The TCP connection is closed	
		
		Http/2 allows multiple transaction over the same TCP connection at the same time
			It's possible one request and several responses with all the resources needed

		
			
Methods HTTP
		GET
		POST
		PUT
		PATCH
		DELETE
		OPTIONS
		HEAD
		TRACE

Status					
		1XX Information

		2XX Success

		3XX Redirection
		
		4XX Client Error
			
		5XX Server Error			
			
			
Headers

	User-Agent:
		Browser, Operative System
		Mozilla/5.0 (windows...)
	Authorization:
		basic username password (base64)
	Cookie:
		The server send the cookie to the browser
		the next time the browser connects, sends the cookie back to the server
			Hi, remember me?
			
	Cache-control:
		save the resource/data for specific period of time
		improve perfomance
		The browser won't receive new files, until cleared or expired
		max-age:31536000
		max-age:no-store
		max-age:14400
			For each file
			
			
	curl -I https://api.github.com		
			
			
		
	Host:

	Content-type:
		application/json1
		
		
	link:
		push files to the client before they're requested
		
	
	ctr-shift-i
		network
		in chrome ctr-r
		select
		
		
Payload
	The content returned by the server additional to the header
		Html
		Javascript
		Json
		XML
		etc
		
		