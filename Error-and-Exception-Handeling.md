#### PHP Error and Exception Basics
PHP provides two mechanisms to report problems that occur during scription execution. 

The most basic one is the error reporting mechanism.
See [PHP Error Documentation](http://php.net/manual/en/language.errors.basics.php) for more information.

PHP also provides an Exception model that allows problems to be handled (aka caught) within your script.
See [PHP Exception Documentation](http://php.net/manual/en/language.exceptions.php) for more information.

#### DinnerLabException Class


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