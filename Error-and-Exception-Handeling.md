#### PHP Error and Exception Basics
PHP provides two mechanisms to report problems that occur during script execution. 

The most basic is the error reporting mechanism.
See [PHP Error Documentation](http://php.net/manual/en/language.errors.basics.php) for more information.

PHP also provides an Exception model that allows problems to be handled (aka caught) within a script.
See [PHP Exception Documentation](http://php.net/manual/en/language.exceptions.php) for more information.

#### DinnerLabException Class
The `DinnerLabException` class extends PHP's built-in `Exception` class, which can be thrown in the same manner as any PHP Exception (see interface `Throwable`).

This class also has static methods that modify how PHP handles errors and uncaught exceptions.
Here's a brief description of these methods, with more details in subsequent sections.

* `errorHandler()`

    This method is called by PHP when non-fatal errors occur.
    Depending on APPLICATION_ENVIRONMENT and error severity, it will log errors, email errors, and/or display nice error page to user.
* `catchException()`

    This method is called by PHP when an uncaught exception is thrown.
    Depending on Exception severity, will log exception, mail exception, and/or display nice error page to user.
* `setErrorHandler($errorTypes)`

    Registers `errorHandler()` and `catchException()` with PHP. `$errorTypes` is bitmask of PHP error types to handle with registered handler. By default is set to E_ALL.
* `shutdownFunction()`

    This method is called by PHP after a script finishes execution, including when a fatal error occurs. This method will detect fatal errors in production and do a header redirect to a static error html page if they occur. It also logs and emails these errors. 

* `registerShutdownFunction()`

    Registers `shutdownFunction()` with PHP.

#### Throwing Exceptions
To throw an exception, create a new `DinnerLabException` object with the following parameters and throw it.

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