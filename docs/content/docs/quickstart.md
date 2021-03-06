+++
title = "Quickstart"
draft = false
date = "2018-01-29T22:04:42Z"

+++
# Installation
First you need to make sure that RIF is properly installed.
Follow the instructions on the 
[installation page]({{< relref "docs/installation.md" >}}) before completing
this guide.

# Making Your First Request
To get started, we will be making a simple GET request to
[httpbin.org/get](http://httpbin.org/get). This endpoint returns the details
of GET requests back to the client as JSON.

We will be passing in a URL parameter called `message` that is parameterised
using RIFs variable templating feature.

Open your editor of choice and save the following file to your computer
as `gethttpbin.rif`:
```
rif_version: 0
url: "http://httpbin.org/get?message=hello%20$(place)"
method: "GET"
variables:
  place:
    type: "string"
    default: "world"
```

Next, open your terminal in the same location and run RIF,
passing in the file you just created:
```
$ rif ./gethttpbin.rif
```

If all goes well you should see something like the following:
```
{
  "args": {
    "message": "hello world"
  }, 
  "headers": {
    "Accept-Encoding": "gzip", 
    "Connection": "close", 
    "Host": "httpbin.org", 
    "User-Agent": "RIF/0.2.0"
  }, 
  "origin": "<YOUR IP ADDRESS>", 
  "url": "http://httpbin.org/get?message=hello world"
}
```

## Variable Templating

Now let's use RIF's variable templating feature to override our welcome message.
Paste the following command into your terminal:
```
$ rif ./gethttpbin.rif place=universe
```

You should now see that the response has changed:
```
{
  "args": {
    "message": "hello universe"
  }, 
  "headers": {
    "Accept-Encoding": "gzip", 
    "Connection": "close", 
    "Host": "httpbin.org", 
    "User-Agent": "RIF/0.2.0"
  }, 
  "origin": "<YOUR IP ADDRESS>", 
  "url": "http://httpbin.org/get?message=hello universe"
}
```

Congratulations! You have just made and executed your first `.rif` file!

# Where next?
Why not check out the 
[RIF File Format]({{< relref "docs/fileformat.md" >}}) documentation?
