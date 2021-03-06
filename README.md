## Nex
A mini Multi-Threaded ProxyServer + HTTPserver in python using socket programming

[![Build Status](https://travis-ci.org/pinkeshbadjatiya/Nex.svg?branch=master)](https://travis-ci.org/pinkeshbadjatiya/Nex)
[![Coverage Status](https://coveralls.io/repos/github/pinkeshbadjatiya/Nex/badge.svg?branch=master&bust=1)](https://coveralls.io/github/pinkeshbadjatiya/Nex?branch=master)

### Instructions
- `settings.conf` file contains all the settings related to the server. Change them as per your need before running the server
- Run `python server.py` to initialize the server.
- `tests/` directory includes all the sample files that are used for nose2-testing.
- `public_html` is the server directory that is used by the server to host the codes.
- `error_pages` contains all the templates of various error codes.
- `other_templates` contains other templates used for rendering by the Nex server.

### Notes
- All the essential directories must be present in the appropriate location as mentioned in the configuration file.

### Features Supported
- Proper status_codes if file found or not ...
- Mimetype taken into account of returned file
- Variable injection in template
- Listing contents of Directory with details about the files.
- HOST validation
- 403 forbidden, 404 not found etc error codes handled
- Separate configuration file for server  
- Client mapping with IPv4 address
- Threading between clients and locks and complete private data(using local variables for each thread)
- Tests written using nose2 and integrated in Travis-CI
- Thread safe logging and colored logging.
- Audio/Video/Image rendering
- URL encoding/decoding
- py2 and py3 support (partial support for py3 for now)
- Can be used as a proxy server by just changing the server config file.  
- All the directories can be relative as well as absolute in settings.conf

## settings.config
- `MAX_REQUEST_LEN` - Max number of bytes we receive at once for proxy server.    
- `SERVER_NAME` - Server Name, "Nex - Simple HTTP server/v.0.3",
- `SERVER_SHORT_NAME` - Server short name, "Nex/v.0.2",
- `HOST_NAME` - Current host name. (Default: "0.0.0.0"),
- `BIND_PORT` - The port to which the server will bind itself. (Default: 12345),
- `PROXY_SERVER` - If true then the server acts as a proxy server. Else like a normal http-webserver. (Default: "true"),
- `MAX_CLIENT_BACKLOG` - Max no of client requests that can be queued. (Default: 50),
- `MAX_REQUEST_LEN` : Max no of bytes that can be received by the server in a single request. (Default: 999999),
- `HOST_ALLOWED` : [ '*' ]
- `BLACKLIST_DOMAINS` : [ "blocked.com" ]
- `PUBLIC_HTML` : "./public_html"
- `ERROR_DIR` : "./error_pages"
- `OTHER_TEMPLATES` : "./other_templates"
- `STATUS_STRING` : Contains all the status codes with their status strings.

### TODO
- Do not read the whole file in memory. Read in chunks and send. Systems crashes when big files are accessed.
- Update tests based on the new config file.
- Tests for all the errors returned
- Allow ranged sending of file that supports seeking of video.
- Checking the presence of all the configuration/essential directories before forking the server thread.
- Separate error pages from actual functions and break the flow if error to respond error funcs.
- Split server class into multiple ones.(PEP8)
- Respect more headers
- Close the pending sockets in the threads too, this sometimes results in the blocking of the main server thread.(http://voorloopnul.com/blog/a-python-proxy-in-less-than-100-lines-of-code/)  
- Use the argument parsing using `argparse`.  
- Check why do we get blank requests.  

### Contribute  
- I have mentioned a lot of TODO's above, just send a PR.  
- Any other bug fix or update is also appreciated.  
