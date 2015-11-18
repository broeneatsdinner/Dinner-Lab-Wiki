#### PHP Error and Exception Basics
PHP provides two mechanisms to report problems that occur during scription execution. 

The most basic one is the error reporting mechanism.
See [PHP Error Documentation](http://php.net/manual/en/language.errors.basics.php) for more information.

PHP also provides an Exception model that allows problems to be handled (aka caught) within your script.
See [PHP Exception Documentation](http://php.net/manual/en/language.exceptions.php) for more information.

#### DinnerLabException Class
The `DinnerLabException` class extends PHP's built-in `Exception` class, which can be thrown the same way you throw any PHP Exception.

This class also has some static methods to handle errors and uncaught exceptions in PHP.
Here's a brief description of these methods, with more details below.

* `errorHandler()`

This method is called by PHP when non-fatal PHP errors occurs.
Depending on APPLICATION_ENVIRONMENT and error severity will log errors, email errors, and/or display nice error page to user.
* `catchException()`

This method is called by PHP when an uncaught exception is thrown.
Depending on Exception severity, will log exception, mail exception, and/or display nice error page to user.
* `setErrorHandler($errorTypes)`

Registers `errorHandler()` and `catchException()` with PHP. $errorType is bitmask of PHP error types to handle with registered handler. By default is set to E_ALL.

#### Throwing Exceptions
Here's an example exception from `DatabaseFactory->getConnection()`:
```
$this->database = new mysqli($dbhost, $dbuser, $dbpassword, $dbname);
if ($this->database->connect_error) {
    throw new DinnerLabException('Unable to connect to MySQL server on '.$dbhost.': '.$this->database->connect_error, 1045, E_ERROR, __FILE__, __LINE__);
}
```
This throws a new DinnerLabException, which if not caught by calling code, will be caught by `DinnerLabException::catchException()`

#### Triggering an Error

#### Displaying Errors and Exceptions to user

#### Logging of Errors and Exceptions

#### Notification of Errors and Exceptions