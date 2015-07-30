# Errors

The Vitae API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Invalid or malformed request
401 | Unauthorized -- Invalid or expired access token
403 | Forbidden -- The requested object is not allowed to be accessed
404 | Not Found -- The requested object could not be found
405 | Method Not Allowed -- You tried to access an invalid method
406 | Not Acceptable -- You requested a format that isn't json
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
