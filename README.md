# Express.js Route Parameter Error Handling Bug

This repository demonstrates a common error in Express.js route handlers: failure to handle errors when parsing route parameters.  Specifically, the `/users/:id` route attempts to parse `req.params.id` as an integer without error checking. If the ID is not a valid number, the application will crash.

The `bug.js` file contains the buggy code, while `bugSolution.js` provides a corrected version with robust error handling.

## Bug

The issue lies in the lack of error handling for invalid user IDs. If a non-numeric ID is passed, `parseInt(userId)` will return `NaN`.  Subsequent attempts to use `NaN` in comparisons will not work as expected. 

## Solution

The solution adds checks to ensure that `userId` is a valid number before attempting to find the user. This prevents crashes and provides a more graceful response to the client.