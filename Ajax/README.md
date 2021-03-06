# Introduction
This exercise was designed to familiarize with the Ajax and Deferred technologies. 

# Task Description
Given the [*initial_template.html*](initial_template.html) web page as a starting point, which contains an image (empty - no `src` attribute defined), a text field and a submit button, you'll need to write a Javascript function that manages the authentication protocol (as human - captcha system) to the server [http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php](http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php).

The server provides three different APIs for the authentication:
1. [http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php?callback=?&getIdentifier](http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php?callback=?&getIdentifier): returns/generates a new `session ID` as a Json object (e.g. `{"id" : 464495}`);

2. [http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php?callback=?&getImage&id=\<sessionid\>](http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php?callback=?&getImage&id=<sessionid>): returns a CAPTCHA image name associates with the passed `session ID` as a Json object (e.g. `{"url" : "captcha//rD6gM4.png", "id" : "464495"}`, so if the returned captcha name is `captcha//rD6gM4.png`, you can get/view the image by visiting the following URL: [http://www.dais.unive.it/~cosmo/esercitazione3/captcha//rD6gM4.png](http://www.dais.unive.it/~cosmo/esercitazione3/captcha//rD6gM4.png));

3. [http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php?callback=?&sendCode&id=\<sessionid\>&code=\<captcha_code\>](http://www.dais.unive.it/~cosmo/esercitazione3/captcha.php?callback=?&sendCode&id=<sessionid>&code=<captcha_code>): by passing the `session ID` and the `captcha code` entered by the user to the server you can check the authentication result.

   The server will send back a JSON object like `{"auth" : true}` in case of successful authentication, or `{"auth" : false}` otherwise (failed).
 
The Javascript code will have to manage all the steps of the authentication protocol using Deferred objects and Promises. The protocol behaves as described by the following steps:

1. Request for the session key to the server;
2. Request for the CAPTCHA image associated with the session key;
3. Waiting for the user to enter the CAPTCHA code and confirm it by clicking on the "OK" button;
4. Sending the code to the server for verification;
5. If the authentication is successful the system must print the phrase "Successful authentication", otherwise (failed) it must be restarted from point 1.

# Result/Testing
You can run the developed application by opening the `final_result.html` through a browser. The expected result should be equals to the one represented in the following GIF:

<p align="center">
  <img src="https://github.com/FabioDainese/Languages_for_Web_and_Networking_Applications/blob/master/Ajax/Images/result.gif" alt="GIF result">
</p>
