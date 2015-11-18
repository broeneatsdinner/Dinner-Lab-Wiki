#### PHP Error and Exception Basics
PHP notifies

##### DinnerLabException Class


#### Throwing Exceptions
Here's an example exception from `DatabaseFactory->getConnection`:
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