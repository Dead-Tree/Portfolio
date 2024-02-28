# Over The Wire - Natas
natas1  - gtVrDuiDfck831PqWsLEZy5gyDz1clto - viewing the source code from the website thats it thats the challange. the password is presented to us as a commented text in the source code.

natas2 - ZluruAthQk7Q2MqmDeTiUij2ZvWy2mBi - in this level the right click option is blocked and inorder to see the password which by the hint we can guess it's again is in the source code we need to use view source code browser short cuts. so again the answer is in the source code commented.

natas3 - sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14 - in this level after logging in we will be greeted with a message " there is nothing on this page". but when we expect the source code we can find a image file named pixel. after we opened the same image file location we can find another file containig the password.

natas4 - Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ  - In this level after logging in, in the source code we find a comment not even google will find it this time. So the search engine comes in to play, the robots.txt file. we move to the directory and can find that a directory called s3cr3t is blocked from crawling so we move in to that directory and can get our password. - https://moz.com/learn/seo/robotstxt

natas5 - iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq - on logging in the message we see is that the user natas4 cannot acces the page and only batas5 can access it. So through burp we intercept the request and we can see a referrer header in the request. just changing it to natas5 can get us a password.

natas6 - aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1 - after logging in we can see a message saying authentication declined. so using burp and intercepting a request we an see a loggedin parameter with value set to 0 and by changing it to 1 we can natas6s paswsord.

natas7 - 7z3hEENjQtflzgnT29q7wAvMNfZdh0i9 - by logging in we can see a input box asking us to enter a secret. I tried intercepting through burp for that secret but didnt find anything. There is button for viewing source code. by clicking on that we can see there is a file named secret.inc. we can manually move into that file get the password.

natas8 - DBfUBfqQG69KvJvJ1iAbMoIpwSNQ9bWe - the webpage here is just showing the home and about pages. So, after looking ata the source code we can see a hint stating that the password is ar /etc/nats_webpass/natas8. so the intial home web page has a parameter pointing to home we can change that to our directory(etc/natas_webpass). 

natas9 - W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl - after logging in we can see a input box asking to give a secret. so same as level natas7 there is a sourcecode button and by hitting that we can see the encoded decret in php. I decoded it using the echo base64_decode(strrev(hex2bin('3d3d516343746d4d6d6c315669563362'))); command in a php interactive session.

natas10 - nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu - at the home page we can see a input box with a search filter on it. By seeing the source code we can see a function which is executing the key value if the key value is not equal to " ". So to run multiple commands we can use ; and we do that as ; cat /etc/natas_webpass/natas10.

natas11 - U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK - this a continuation level to level 10. in this level they developed a filter in the function which filters the characters ; and &. so since it is using grep to find out the files we can still search multiple files just by giving a normal character appended with the password location(etc/natas_webpass/natas11). here i used . as a character and got the password.

natas12 - EDXp0pS26wLKHZy1rDBPUZk0RKfLGIR3 - by logging in we are presented with a screen consisting of the source code option and the colour background of the page. by seeing the source code we can find that there are three functions XOR encrypt, load data and save data. by which we can find that the actual cookie value is encoded in json, base64 encoded and xor encrypted, and the condition for validating the cookie are to check for the parameters of the actual cookie data parameter "show cookie" to true and the xor logic helps us to find the actual key which is used to encrypt the cookie.

nata13 - jmLTY0qiPZBbaKc9341cqPQZBJv7MQbY - in this challenge we are provided with a file uploading application saying us to upload a jpg file which is less than 1kb. By looking at the source code we can say that what ever file we uploaded to the website it is generating some random name and random path to the file to upload it the /upload folder and one main take away from the source code is it is not **"filtering the file type of the file we uploaded"** and just uploading it so the application contains **"file inclusion vulnerabilty"**. so, using burpsuite we can intercept the actual behaviour of the website during a file upload and* "we can change the file type too :)"* so by writing a simple php code giving us the password of natas13(<?php  // get the contents of a file, and echo it out.
  echo file_get_contents( "/etc/natas_webpass/natas13" ); 
?>) willsolve this level.

natas14 - Lg96M10TdfaPyVBkJdjymbllQ5L6qdl1 - in this challenge we are greeted with a message stating it only accepts image files. but if we look at the source code it using a php method **"exif_imagetype()"** which checks only for the file signatures in the inintial hexa bits. so all we have to do is a tricking the server that the file we are uploading is a jpg file. by googling we can found out that the signature for a jpg file is **FF D8 FF** by including this in the start of the hexacode of the php file we are uploading we can retrieve the password for natas14 by intercepting and changing the file extension using burp.

natas15 -   - this ca be achieved with a simple sql injection as the user input is not verifying. we can do it in one of the following ways:
All the following combinations work (among many others):

    User: natas15" #
    Pass: empty
    Query:

    SELECT * from users where username="natas15" # and password =""

    User: " or 1 = 1 #
    Pass: empty
    Query:

    SELECT * from users where username="" or 1 = 1 # and password = ""

    User: natas15
    Pass: " or "1"="1
    Query:

    SELECT * from users where username="natas15" and password = "" or "1" = "1"

natas16 - WaIHEacj63wnNIBROHeqi3p9t0m5nhmh - this task explores the blind sql vulnerability and we need to brute force the password we need to find and as we know the password is 32 char long we can do it manually but, takes a lot of time so it can be automated by a python script. so i didn't do it. :(

natas17 - 
