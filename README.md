# subquest
### Fast, Elegant subdomain scanner using nodejs
![logo](https://raw.github.com/skepticfx/subquest/master/etc/logo.png)

## Status
[![Build Status](https://travis-ci.org/skepticfx/subquest.svg?branch=master)](https://travis-ci.org/skepticfx/subquest)

## Installation

`sudo npm install -g subquest`

## Usage

```
  Usage: subquest [options] <domain to scan>
  Examples:
	subquest google.com
	subquest facebook.com -s 8.8.8.8 -r 20 -d top_50
	subquest twitter.com -s 8.8.8.8 -d all

  Options:

    -h, --help               output usage information
    -V, --version            output the version number
    -b, --bingSearch         use Bing search to list all possible subdomains
    -s, --server [ip]        specify your custom DNS resolver
    -r, --rateLimit [limit]  set the Rate Limit [Default value is 10]
    -d, --dictionary [type]  set the dictionary for bruteforcing [top_100]
```

## Using it in your modules

`npm install subquest`


```js
var subquest = require('subquest');
console.log('Scanning the sub domains of ea.com with 4 requests at a time.');
subquest
  .getSubDomains({
    host: 'ea.com', // required
    rateLimit:'4',
    dnsServer:'4.2.2.2',
    dictionary: 'top_200'
    })
  .on('end', function(arr){
    console.log(arr); // array of subdomains.
  })
```

This scans ea.com for the list of all subdomains using the top_200 dictionary.

## Want to add a new entry to Subquest's dictionary?

Add your list of subdomain names to the `./dictionary/all.txt` file and send a pull request.

## Credits
* Domain dictionary from Sub-Brute by Rook, https://github.com/TheRook/subbrute
