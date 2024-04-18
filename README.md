# Library Management System App

## the title of your app

Library Management System

## a simple description of your app

This application is a library management system that implements CRUD operations. Specifically, it realizes the management of borrowed books, can add and delete the records of book borrowing and returning, and can also modify the records of book borrowing. As well as help people search for books, so that people can quickly find the books they want to find. Also, I added a simple flask-login module to the system for user login and logout. (Username: 11, password: 22)

## a link to the deployed copy of your app

[link](https://i6.cims.nyu.edu/~ws2406/7-web-app-WeijiaLinaSun/flask.cgi)

## the full names, NYU Net IDs, and links to GitHub accounts of any collaborators with whom you worked on this app

I did this assignment independently and did not collaborate with other students.

### Notes:

During the completion of this assignment, I successfully met the requirements locally and ensured that all functions were operating correctly. However, when attempting to deploy the program to the server, I encountered some unforeseen technical issues. Specifically, the program generates the following error when running on the server, as shown in the picture.

I have made every effort to resolve this issue, including modifying the flask.cgi file:

```python
class ProxyFix(object):
    def __init__(self, app):
        self.app = app

    def __call__(self, environ, start_response):
        environ['SERVER_NAME'] = ""
        environ['SERVER_PORT'] = "80"
        environ['REQUEST_METHOD'] = "GET"
        environ['SCRIPT_NAME'] = ""
        environ['PATH_INFO'] = "/"
        environ['QUERY_STRING'] = ""
        environ['SERVER_PROTOCOL'] = "HTTP/1.1"
        return self.app(environ, start_response)

if __name__ == '__main__':
    app.wsgi_app = ProxyFix(app.wsgi_app)
    CGIHandler().run(app)
```

After these changes, I can now access the homepage index, but I am unable to access other routes, such as create, read, etc. It then reports a 404 error:

Object not found!
The requested URL was not found on this server. The link on the referring page seems to be wrong or outdated. Please inform the author of that page about the error.
If you think this is a server error, please contact the webmaster.
Error 404

I also changed the path of the Python interpreter in flask.cgi to the one in my own .venv, along with the libraries, which then reported an API error.

Additionally, I modified app.py to run with `app.run(host='0.0.0.0', port=5000, debug=True)`, but this also resulted in errors.

Despite these efforts, I was unable to fully resolve the issue before the deadline. Therefore, I am requesting that you consider the effort I have put into the parts of the assignment I was able to complete and grant me some sympathy points. I am fully aware of the importance of fulfilling all assignment requirements, and I sincerely apologize for not fully meeting them this time. I will continue to seek solutions, including visiting office hours and researching relevant materials, to ensure I avoid similar issues in future learning and assignments. Thank you for your understanding and support. Please consider my request, and I look forward to your lenient guidance.
