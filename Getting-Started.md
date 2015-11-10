Let's get down to brass tacks.

<a name='installation'/>
## Installation
### GitHub

The easiest way to install the Dinner Lab repository is via the GitHub Desktop (GUI) application. Notes here.

Directory structure:  

```
/path/to/web/dinnerlab # the DOCUMENT_ROOT of the repository
/path/to/web/logs # "one up" from the DOCUMENT_ROOT
```

***

<a name='application-environment'/>
## Application Environment
### The Big Red Button

Your application environment is set in one file, located in `_/php/globalsConfig.BIG_RED_BUTTON.php`. Depending on the branch that you're working off of, the BIG RED BUTTON should be set automatically. Here are the proper configurations for it:

Branch `develop`
"development" environment
Points to `dinnerlab_development` database

Branch `release`
"development" environment
Points to `dinnerlab_development` database

Branch `master`
"production" environment
Points to `dinnerlab_production` database
