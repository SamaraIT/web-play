# Requirement
Create valilla Javascript that will send front logs, stored in session storage, to backend. Do not use Angular.

# Use case
1. fetch backend URL by sending XHR request (GET)
2. after URL is successfully read, read session storage
3. send data from session storage to backend (POST)
4. clear session storage
5. after button is clicked disable it for 2 seconds

# Local showcase
* install [live server](https://www.npmjs.com/package/live-server) or something else to start app  
```
$ live-server --port=4000
```

## Why do I need server?
Because request to fetch `app-config.json` does not work (CORS) when you just move index.html in browser.  
E.g. in Chrome:  
`Cross origin requests are only supported for protocol schemes: http, data, chrome, chrome-extension, https.`

# Example of backend as Spring app
This application is not provided. This is just front part, but you can do backend on your own.  
You would get error like `OPTIONS http://localhost:8099/front-logs net::ERR_CONNECTION_REFUSED`
```
@RestController
@RequestMapping('/front-logs')
@Slf4j
class FrontLogsControllerController implements ControllerTrait {

  @PostMapping()
  def storeLogs(@RequestBody LogData logData) {
    log.info(logData.log)
    return [success: true, result: "Front logs stored."]
  }

}

class LogData {
  String log
}
```

# Resources
## web storage
https://www.w3schools.com/html/html5_webstorage.asp

## Javascript - disable button and reenable it after 5 seconds
```
function submitPoll(id) {
	document.getElementById("votebutton").disabled = true;
	setTimeout(function () {
		document.getElementById("votebutton").disabled = false;
	}, 5000);
}
```

https://stackoverflow.com/questions/15207177/disable-button-with-timeout?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa