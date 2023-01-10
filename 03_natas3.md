***There is nothing on this page***

This time, there appears to really not be anything. Looking at the page source, we are instead greeted with a comment this time, telling us:

**`<!-- No more information leaks!! Not even Google will find it this time... -->`**  

Not even Google will find it this time? Meaning that it has been *willfully excluded* from being crawled/indexed by search engines? Well, information on those links can be found in a site's `robots.txt` file. Let's see if one exists for this subdomain:

**`natas3.natas.labs.overthewire.org/robots.txt`**  
*`User-agent: *`*  
*`Disallow: /s3cr3t/`*  

So the robots.txt file has explicitly disallowed search engines from indexing a directory located at /s3cr3t/:

**`natas3.natas.labs.overthewire.org/s3cr3t/`**  

Here we see another users.txt file:

*`natas4:tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm`*  
