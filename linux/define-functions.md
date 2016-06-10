#Defining customized functions

To define functions the ~/.bashrc file hase to be modified. 
Example:

```bash
[...]
mygrants()
{
  mysql -B -N $@ -e "SELECT DISTINCT CONCAT(
    'SHOW GRANTS FOR \'', user, '\'@\'', host, '\';'
    ) AS query FROM mysql.user" | \
  mysql $@ | \
  sed 's/\(GRANT .*\)/\1;/;s/^\(Grants for .*\)/## \1 ##/;/##/{x;p;x;}'
}

export mygrants
[...]
``` 

The function can be used after the session has been restarted.
