## Session Management

HTTP is a stateless protocol. Therefore, by default there is no user data or other data about previous requests.
To deal with this problem, the proper Session Management is required.

Session Management techniques help to maintain state between HTTP requests.

There are three main Session Management techniques:
- Session variable to set and get data (HttpContext.Session)
- ViewData (called also ViewBad)
- TempData