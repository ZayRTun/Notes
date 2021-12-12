**Home**
- [Home](../index.md)
---

# PHP Upload file size setting
By default, PHP file upload size is set to maximum 2MB file on the server, but you can increase or decrease the maximum size of file upload using the PHP configuration file (php.ini), this file can be found in different locations on different Linux distributions.  

# finding all `php.ini` files
```bash
sudo find / -name php.ini
```
## You need to change in both the `php.ini` in `cli` and `apache2` directories as below.

```bash
code /etc/php/7.4/apache2/php.ini
code /etc/php/7.4/cli/php.ini
```

To increaes file upload size in PHP, you need to modify the upload_max_filesize and post_max_size variable’s in your php.ini file.

```bash
upload_max_filesize = 10M
post_max_size = 10M
```  

Once you have made the above changes, save the modified php.ini file and restart the web server using following commands on your respective Linux distributions.
```bash
// --------------- SystemD ---------------
systemctl restart nginx
systemctl restart httpd		
systemctl restart apache2	

// --------------- Sys Vinit ---------------
service nginx restart
service httpd restart		
service apache2 restart
```
