---
layout: slides
title: "A Hasty Introduction to Web Development"
---
<section markdown="block" class="intro-slide">
# {{ page.title }}

### {{ site.course_number}}-{{ site.course_section }}

<p><small></small></p>
</section>
<section markdown="block">
# We just went over three weeks worth of JavaScript. Now what? 

</section>

<section markdown="block">
## So, What's This Web Development Thing About Anyway?

In this set of slides, we'll cover:

* some definitions / context
* a simplified explanation of a couple of protocols (TCP, HTTP)
* HTML and JavaScript
* client / server
* backend vs frontend development
</section>

<section markdown="block">
## Definitions

### Yeah, some of these might be silly, but let's do this!

__What's the difference between the internet and the web (I'm really asking this).__ &rarr;

* {:.fragment} __the internet__ - global system of interconnected computer networks; a network of networks	
	* {:.fragment} internet's underlying protocol for communication is __TCP/IP__ 
	* {:.fragment} __TCP/IP__ dictates how data should be packetized, addressed, transmitted, routed and received 
* {:.fragment} __the web__ - a collection of interconnected documents (web pages) and other resources (images, video, etc.), retrievable by url and connected by _hyperlinks_
	* {:.fragment} __HTTP__ is the protocol used to allow documents and resources to be requested over a network
</section>

<section markdown="block">
## Other Services

__The web__ is just one of many services available on the internet... __what are some others services and protocols on the internet?__ &rarr;


* {:.fragment} email (SMTP)
* {:.fragment} chat (XMPP, OSCAR, IRC)
* {:.fragment} file transfer (FTP)
* {:.fragment} voice (SIP, Skype protocol)
* {:.fragment} these are all examples of __network protocols__ -  ways of communicating over a network
</section>
<section markdown="block">
## Protocols

Hm. All this talk about protocols but ... __what _exactly_ is a protocol?__ &rarr;

It's a bunch of rules and conventions for communication. Really. That's it.
{:.fragment}

For computers and communication between them, these rules may define:
{:.fragment}

* the format for exchanging messages 
* a meaning (semantics) and syntax for these messages
* the process for synchronizing the communication
{:.fragment}
</section>

<section markdown="block">
## A Protocol Example

Our book described a __simple chat protocol__. For two computers to communicate with this protocol:

1. one computer sends bits that represent the text, '__CHAT?__', to another computer
2. the other computer responds with '__OK!__' to show that it accepts and understands the protocol
3. from there, they can:
	* proceed to send each other strings of text
	* read the text sent by the other from the network
	* display the received text
</section>
<section markdown="block">
## Another Example

Here's what an email interaction may look like (SMTP - Simple Mail Transfer Protocol):

<pre><code data-trim contenteditable>
Client: HELO client.mydomain.com
Server: 250 Hello client.mydomain.com
Client: MAIL FROM:<cooldude@superawesomemail.com>
Server: 250 OK
Client: RCPT TO:<admin@pizzaforyou.com>
Server: 250 OK
</code></pre>

<pre><code data-trim contenteditable>
Client: DATA
Server: 354 Send message content; end with CRLF.CRLF
Client: (email headers and body)
Client: .
Server: 250 OK, message accepted for delivery: queued as (id)
Client: QUIT
Server: 221 Bye
</code></pre>
</section>

<section markdown="block">
## A Slightly Closer Look at TCP/IP

__A simplified description of communication over TCP/IP (Transmission Control Protocol/Internet Protocol):__

1. a computer (the _server_) must be listening on a particular port (a number assigned to a listener, to allow for multiple listeners on a single computer)
2. most protocols specify which port should be used by default
	* __what's the default port for HTTP?__ &rarr; <span class="fragment">80</span>
	* __and HTTPS?__ &rarr; <span class="fragment">443</span>
3. another computer (the _client_) can connect to the listening machine using the specified port number
4. if the server can be reached and is listening, a connection is created
5. the connection serves as a two-way pipe so that data can flow in both directions
6. once the data is successfully transmitted, it can be read and used by the machine it was sent to
</section>

<section markdown="block">
# TCP/IP is the underlying protocol of the internet; other protocols are built on top of it
</section>

<section markdown="block">
# We're Interested in the Web, and Makin' Web Pages
</section>

<section markdown="block">
## The Web

__What was our definition of the web again?__ &rarr;

A collection of interconnected documents (web pages) and other resources (images), retrievable by url and connected by _hyperlinks_.
{:.fragment}

</section>
<section markdown="block">
## It All Starts With a URL

Each document or resource on the web is retrievable by a name, a __URL__ (Universal Resource Locator). __What are the parts to a URL?__ &rarr;

* {:.fragment} __scheme/protocol__ - http (er, browsers accept schema-less)
* {:.fragment} __domain or actual ip address__ - pizzaforyou.com
* {:.fragment} __port__ (optional) - 80 (default if http)
* {:.fragment} __path__ - /search
* {:.fragment} __query_string__ (optional) - ?type=vegan
* {:.fragment} __fragment_id__ (optional) - #topresult

<br>
<code>scheme://domain:port/path?query_string#fragment_id</code>
{:.fragment}

<code>http://pizzaforyou.com:80/search?type=vegan#top_result</code>
{:.fragment}
</section>
<section markdown="block">
## Domains and IP Addresses

__Each machine connected to the Internet gets a unique IP address.__

We can map domains to IP addresses through DNS (Domain Name System). 

* both IP Addresses and domains are acceptable in a URL.
* on OSX, Linux (and windows), there's a file that allows you to map names to ip addresses (before using dns)
* typically <code>/etc/hosts</code> or <code>hosts.txt</code>
* <code>localhost</code> maps to <code>127.0.0.1</code>... which essentially is _your_ computer

</section>

<section markdown="block">
## HTTP

To retrieve documents on the web, we use __HTTP__ (Hyper Text Transfer Protocol). The computer/application asking for the document is the __client__ or _user-agent_, and the computer responding to requests for documents is the __server__.

* generally, the __server__ is going to be some sort of web server, like Apache or Nginx
* __the user-agent is going to be__ &rarr; <span class="fragment">some sort of browser, like Chrome or Safari</span>

<br>
__HTTP is a request-response protocol, a very basic communication method between computers:__

* the client sends a request for some data 
* the second computer responds to the request

</section>
<section markdown="block">
## HTTP Continued

The interaction between your browser and a web server goes something like this:

* the browser attempts to connect to the address of the server
* if the server is listening and _reachable_, a TCP connection is made between the server and the client on port 80 (the default port for HTTP traffic)
* the browser sends a request message
* on the same connection, the web server gives back a response message
</section>
<section markdown="block">
## A Request Message

A request consists of:

* __a request line ...__  which includes a request method and a path - <code>GET /teaching HTTP/1.1</code>
* __request headers__ <code>Host: jvers.com</code>, <code>User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:12.0) Gecko/20100101 </code>
* __an empty line__
* __an optional body__

<br>
[Here's a list of request header fields](http://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Request_fields).
</section>

<section markdown="block">
## Request Methods

Here's a list of available [request methods](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods). A __request method__ (sometimes called a _verb_) tells the server what action perform on the identified resource. __A couple of common ones are ...__ &rarr;

* __GET__ - retrieve specified resource/data without any other effect... (reading data)
	* data is passed through query string parameters / url
* __POST__ - requests that the server accept the data in the request for storage (creating data)
	* data is passed in body of request
{:.fragment}
</section>

<section markdown="block">
## A Response Message

A response consists of:

* __a status-line ...__ which includes a status code and reason - <code>HTTP/1.1 200 OK</code>
* __response header fields__ - <code>Content-Type: text/html</code>
* __an empty line__
* __an optional message body__ - usually an HTML document!

<br>
[And of course, a list of response header fields](http://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Response_fields).
</section>

<section markdown="block">
## Status Codes

The status code that a server responds with is a numeric code that indicates the result of the request. __Some typical status codes are__ &rarr;

* __200 OK__ - request was successful!
* __404 Not Found__ - resource was not found, but may be available again in the future
* __500 Server Error__ - generic server error
{:.fragment}
</section>

<section markdown="block">
## Status Codes Continued

__There are 5 different classes of status codes__ &rarr;

* __1xx__ - __Informational__, request received
* __2xx__ - __Success__, request was received, understood and accepted
* __3xx__ - __Redirection__, additional action must be taken to complete request
* __4xx__ - __Client Error__
* __5xx__ - __Server Error__
{:.fragment}
</section>

<section markdown="block">
## A Sample Interaction

A request:

<pre><code data-trim contenteditable>
GET /teaching/ HTTP/1.1
Host: jvers.com
Connection: keep-alive
Cache-Control: max-age=0
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/37.0.2062.120 Safari/537.36
Accept-Language: en-US,en;q=0.8
</code></pre>
</section>

<section markdown="block">
## A Sample Interaction Continued

A response:

<pre><code data-trim contenteditable>
HTTP/1.1 200 OK
Date: Thu, 18 Feb 2016 15:23:39 GMT
Server: Apache/2.2.15 (Red Hat)
Accept-Ranges: bytes
Content-Length: 163
Content-Type: text/html; charset=UTF-8
Set-Cookie: STATICSERVERID=s3; path=/
Cache-control: private
.
.
.
(html)
</code></pre>
</section>


<section markdown="block">
# Some Tooling (in increasing order of ease-of-use)
</section>

<section markdown="block">
## netcat

__nc__ is a commandline utility for TCP connection and communication through UDP. It can take a host and port as arguments:

<pre><code data-trim contenteditable>
nc cs.nyu.edu 80
</code></pre>

Then... start typing! Let's try to retrieve the root document (<code>/</code>).

<pre><code data-trim contenteditable>
GET / HTTP/1.1
Host: cs.nyu.edu
</code></pre>

Or... the document <code>/home/index.html</code>

<pre><code data-trim contenteditable>
GET /home/index.html HTTP/1.1
Host: cs.nyu.edu
</code></pre>
</section>

<section markdown="block">
## curl

__curl__ is a command line tool to transfer data to and from a server. The -I flag retrieves headers only.
<pre><code data-trim contenteditable>
# get the response headers for google.com only
curl -I google.com

# get the response headers for www.google.com only
curl -I www.google.com

# get the entire response (including body)
curl www.google.com
</code></pre>
</section>

<section markdown="block">
## Chrome 

View &rarr; Developer &rarr; Developer Tools

...Network

...(specific request)

...view source

</section>
<section markdown="block">
# Let's try using nc, curl and Chrome to get some status codes!
</section>
<section markdown="block">
## Clients and Servers

So... web development can mean a lot of things. Broadly speaking: 

* you can be developing for the client (writing HTML, client side JavaScript applications)
* ...or for the server (server-side code that manipulates and retrieves data)

<br>
We'll be dealing with server-side development first...
</section>
