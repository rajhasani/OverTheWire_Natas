Here we're given 2 links, one to a "Home" page, and the other to an "About" page. Clicking on either shows us that the web server is using PHP to reference files in the domain filesystem and serve those whenever selected. 

Taking a look at the source code, we are given a reminder that the location of the passwords follow the same syntax as the previous OTW wargames; that is, that the password for natas8 is located at `/etc/natas_webpass/natas8`. Since index.php is serving us files from the web sever directory, let's see if we can exploit a simple path traversal vulnerability to access the natas8 password:

**`http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8`**  
*`a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB`*  
