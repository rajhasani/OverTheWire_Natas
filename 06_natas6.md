Here we're greeted with an input box, a submit button, and a link to view the source code. Inputting a random test password yields the response *`Wrong secret`*. 

Let's click on that "view sourcecode" link. The `include` statement references a file located at "includes/secret.inc". Let's navigate over to that directory within the subdomain:

**`http://natas6.natas.labs.overthewire.org/includes/secret.inc`**  
```
<?
$secret = "FOEIUWGHFEEUHOFUOIU";
?>
```

Great. Let's plug that into the input box.

*`Access granted. The password for natas7 is jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr`*  
