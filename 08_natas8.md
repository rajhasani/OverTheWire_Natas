Here we're given an input field similar to that in natas6; there is a secret we have to input, and a link to view the source code. Let's take a look at that link first; within the source code, we see the following function:

```
<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}
?>
```

Based on the above, we see the following:
* The contents of our input are defined as the variable $secret
* The contents of $secret have to match the contents of $encodedSecret to grant us access
* The contents of $encodedSecret have been given to us
* Our input goes through several functions before being recognized in the `if()` statement as $secret

Lets take a look at these functions. Methodically speaking, our input is first encoded in base64, then that string is reversed using `strrev()`, and is then converted into hexadecimal output. We can reverse-engineer the given solution ($encodedSecret) using these functions to derive the correct input; therefore, we need to convert the given contents of $encodedSecret from hexadecimal to binary, then reverse that output, then decode that output using base64.

**`raj@arch:~$ vim natas8`**  
**`raj@arch:~$ cat natas8`**  
*`3d3d516343746d4d6d6c315669563362`*  
**`raj@arch:~$ xxd -r -p natas8 natas8bin; cat natas8bin | rev | base64 -d`**  
*`oubWYf2kBq`*   

Now that we have our derived secret, let's plug that into the input field:

*`Access granted. The password for natas9 is Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd`*  
