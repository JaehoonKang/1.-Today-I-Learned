# TIL_0515 HTTP

### Today's **Challenge**

- What is `HTTP`?

- Basic `Express`

## HTTP

- `Between Web Browser and Web Server`, a protocol is needed as a way of communicating back and forth

- Since 1999, HTTP 1.1 version still continues in use: means of communication can be `text`

- Recently, `HTTP/2` appeared in a purpose of a better speed and so many more reasons. 

- HTTP/2 is securely protected so no one can hack into a server

- As opposed to HTTP, `binary code` is exchaged as means of communication

    - when communicated in a form of `text`, it is more convenient to human eyes. However, it requires storage and more

    - However, regarding `binary code`, for computers, it is more understandable and readable so a rapid speed increase is possible to achieve

<br>

### What is important in `HTTP`

- `If there is no request, no response`

- In Web browser, once `HTML` is competely loaded or read, there comes a next step (i.e. response or request)

- Usually, out of 8 HTTP methods, `get` and `post` are two most methods

- `get` is to request data and `post` is register data

- Perent Encoding: I typed 'banana' on a browser, but it shows me different value than 'banana' as in the following

`https://www.google.co.kr/search?q=%EC%95%84%EB%82%98%EB%B0%94%EB%8B%A4&oq=%EC%95%84%EB%82%98%EB%B0%94%EB%8B%A4&aqs=chrome..69i57j0l5.2335j0j7&sourceid=chrome&ie=UTF-8`

<br>

### Response Status

- You may see `404 not found` or `Successful 200` messages 

- There are different status for indicating whether a response is successfully or unsuccessfully complete.


## Express

- Flexible Nodejs web application Framework 


