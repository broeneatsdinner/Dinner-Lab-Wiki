#### PHP Error and Exception Basics
PHP provides two mechanisms to report problems that occur during script execution. 

The most basic is the error reporting mechanism.
See [PHP Error Documentation](http://php.net/manual/en/language.errors.basics.php) for more information.

PHP also provides an Exception model that allows problems to be handled (aka caught) within a script.
See [PHP Exception Documentation](http://php.net/manual/en/language.exceptions.php) for more information.

#### DinnerLabException Class
The `DinnerLabException` class extends PHP's built-in `ErrorException` class, which can be thrown in the same manner as any PHP Exception (see interface `Throwable` and [Error Exception documentation](http://php.net/manual/en/class.errorexception.php)).

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
To throw an exception, create a new `Exception` object with the following parameters and throw it.
```
/**
 * string $message [optional] The message to throw of exception. 
 * int $code [optional] The Exception code, which is interpreted by DinnerLabException::catchException() 
 *                      as PHP ERROR severity. So you can throw exceptions that can be ignored.
 * Exception $previous [optional] The previous exception used for the exception chaining.
 */
new Exception($message, $code, $previous);
```

Here's an example exception from `DatabaseFactory::getConnection()`:
```
$this->database = new mysqli($dbhost, $dbuser, $dbpassword, $dbname);
if ($this->database->connect_error) {
    throw new Exception('Unable to connect to MySQL server on '.$dbhost.': '.$this->database->connect_error, 1045);
}
```
This throws a new Exception, which if not caught by calling code, will be caught by `DinnerLabException::catchException()`

#### Triggering an Error
See PHP `trigger_error()` function.

#### Displaying Errors and Exceptions to user
Placeholder to describe how errors are outputted.

#### Logging of Errors and Exceptions
Placeholder to describe how errors and exceptions are logged.

#### Notification of Errors and Exceptions
Placeholder to describe how error and exceptions notify us.

#### Known Error Codes and Behavior
| Code | Description | Stops Execution |
| ------ | ------ | ------ |
|E_ERROR|PHP Error|Yes|
|E_WARNING|PHP Warning|No|
|E_PARSE|PHP Parsing Error|Yes|
|E_NOTICE|PHP Notice|No|
|E_CORE_ERROR|PHP Core Error|Yes|
|E_CORE_WARNING|PHP Core Warning|No|
|E_COMPILE_ERROR|PHP Compile Error|Yes|
|E_COMPILE_WARNING|PHP Compile Warning|No|
|E_USER_ERROR|User Error|Yes|
|E_USER_WARNING|User Warning|Yes|
|E_USER_NOTICE|User Notice|No|
|E_STRICT|PHP Runtime Notice|No|
|E_RECOVERABLE_ERROR|PHP Recoverable Error|Yes|
|E_DEPRECATED|PHP Deprecated|No|
|E_USER_DEPRECATED|User Deprecated|No|
|E_ALL|All Errors|Yes|
|1045|DB Access Denied|Yes