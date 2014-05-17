# Parsing HTTP Responses

When you make a request to a server, you get back a response which is essentially a text file in a predictable format.

Your mission is to create a class called HttpResponse (test-driven) that can parse these HTTP responses. Every HTTP response is setup in the same way:

* The first line contains the status code
* There is a blank line in between the list of headers and the body

This class must:

* Take a string when it is initialized. This string is a valid HTTP response. Examples below.
* Have a `headers` method that returns a hash of headers, where the strings are keys
* Have a `body` method that returns the entire body (and nothing else)
* Have a `status_code` method that returns an integer representing the status code

Note the following:

* Use the Sample HTTP Responses below to setup your tests and expectations
* You do not have to have your class return a "live" HTTP response

If you finish that before the warmup is done, please

* add a method named `response_json` that will return a Ruby hash of the body if the Content-Type is json (returns nil otherwise)
* update the `headers` method to return a hash with all lowercase symbols - so `:content_type` instead of `"Content-Type"`
* create a method that will save the HTML to a file in the `/tmp` directory and open it it in the browser if the content type is `text/html`

## Sample HTTP Responses

### A 200 response with HTML

    HTTP/1.1 200 OK
    Server: nginx/1.4.6 (Ubuntu)
    Date: Tue, 06 May 2014 02:17:16 GMT
    Content-Type: text/html
    Last-Modified: Sun, 27 Apr 2014 04:03:41 GMT
    Transfer-Encoding: chunked
    Connection: keep-alive
    Content-Encoding: gzip

    <!DOCTYPE html>
    <html lang="en">
    <head><meta charset="utf-8" />
      <meta name="description" content="should i test private methods?" />
      <meta name="keywords" content="test,private,methods,oo,object,oriented,tdd" />
      <title>Should I Test Private Methods?</title>
    </head>
    <body>
      <div style='font-size: 96px; font-weight: bold; text-align: center; padding-top: 200px; font-family: Verdana, Helvetica, sans-serif'>NO</div>
      <!-- Every time you consider testing a private method, your code is telling you that you haven't allocated responsibilities well.  Are you listening to it? -->
    </body>
    </html>

### A 301

    HTTP/1.1 301 Moved Permanently
    Server: nginx/1.6.0
    Date: Tue, 06 May 2014 02:18:40 GMT
    Content-Type: text/html
    Content-Length: 184
    Location: http://www.pivotaltracker.com/

    <html>
    <head><title>301 Moved Permanently</title></head>
    <body bgcolor="white">
    <center><h1>301 Moved Permanently</h1></center>
    <hr><center>nginx/1.6.0</center>
    </body>
    </html>

### 200 response with JSON

    HTTP/1.1 200 OK
    Server: nginx
    Date: Tue, 06 May 2014 02:15:51 GMT
    Content-Type: application/json; charset=utf-8
    Transfer-Encoding: chunked
    Connection: keep-alive
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET, POST

    {"coord":{"lon":-0.13,"lat":51.51},"sys":{"message":0.0346,"country":"GB","sunrise":1399350122,"sunset":1399404728},"weather":[{"id":721,"main":"Haze","description":"haze","icon":"50n"},{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"base":"cmc stations","main":{"temp":286.24,"humidity":83,"pressure":995,"temp_min":284.82,"temp_max":287.59},"wind":{"speed":3.77,"deg":220.5},"clouds":{"all":88},"dt":1399339749,"id":2643743,"name":"London","cod":200}

# Setup

* Fork
* Clone
* Turn on TravisCI for the fork by
  visiting https://travis-ci.org/profile/<github user name>, clicking the "Sync now" button
  and scrolling down to find the repository to build.
* Create a new branch for your work using `git checkout -b v1`
* Implement specs and code
* Push using `git push -u origin v1`

## Further Practice

This warmup can be completed multiple times to increase your comfort level with the material.
To work on this from scratch, you can:

1. Add an upstream remote that points to the original repo `git remote add upstream git@github.com:gSchool/text-centering.git`
1. Fetch the latest from the upstream remote using `git fetch upstream`
1. Create a new branch from the master branch of the upstream remote `git checkout -b v2 upstream/master`
1. Implement specs and code
1. Push using `git push -u origin v2`

Each time you do the exercise, create a new branch. For example the 3rd time you do the exercise the branch
name will be v3 instead of v2.
