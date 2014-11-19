## CSE509 - Hands-on Exercise (2/2)

Summary
-------
In this hands-on exercise, you have to locate and exploit a CSRF vulnerability and an XSS vulnerability in a file manager written in PHP.

Preparation
-----------
You can obtain the code of this application from github.com, either by cloning the repository into your Apache directory:

	git clone https://github.com/nikifor/cse509_ho2.git

or just downloading the ZIP file from github and extracting the files.

In either case, give world-readable and world-writable permissions to the *gallery-images* folder, so that your webserver can create new directories and files in that folder.

Setup two locally resolvable domains:

* victim.com
* attacker.com

and connect *victim.com* (using an Apache virtual host) to the directory where you earlier unzipped (or cloned) the file-manager PHP files. Similarly, create a site *attacker.com* from where you will be launching your attacks.

At the end of this process, you should be able to type in your browser **victim.com** and see the file manager and **attacker.com** and see your own soon-to-be-malicious page.

***All attacks have been tested using Chrome. Use another browser at your own risk!***


Part 1 (Points 7/10)
------

The file manager has a CSRF vulnerability which allows attackers to create directories simply by luring the user to a malicious website.

Create such a page under *attacker.com* which, when visited, will create 5 directories (hacked0, hacked1,...,hacked4) in the *gallery-images* folder.

Part 2 (Points 3/10)
------

The file manager has an XSS bug which manifests when the user tries to see the contents of a folder that does not exist. Create a file *a.js* with the contents:

	alert("Hacked!");

and then construct a URL for victim.com which when visited will dynamically fetch the *http://attacker.com/a.js* file and pop-up the alert for the user.

For this part, instead of trying to inject scripts in the traditional way, inject them using an img HTML tag, e.g.

	<img src=x onerror='javascript:alert(1);'>



