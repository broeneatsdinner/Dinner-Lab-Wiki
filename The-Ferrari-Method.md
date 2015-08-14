Tables that we ‘know’ we won't use become zzz_tablename and tables that we’re still writing data to, but are being phased out are yyy_tablename.

Reason being: 
- zzz_tablename allows us to know at a quick glance that the table should be deleted with no worries.
- yyy_tablename still slates it in for a table that we should be looking at / comparing to, but will eventually delete as well

Renaming classes:
Add ‘Deprecated’:
- filenames `class.Tickets.php` would become `class.TicketsDeprecated.php`
- class name it would be called `class TicketsDeprecated {}`