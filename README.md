# Testing-Web-Applications-for-Vulnerabilities
## Web Application 1: Your Wish is My Command Injection
Complete the following steps to set up the activity:

Access Vagrant and open a browser.

Navigate to the webpage http://192.168.13.25Links to an external site. and select the "Command Injection" option.

Alternatively, access the webpage directly at this page: http://192.168.13.25/vulnerabilities/exec/Links to an external site.
<img width="455" alt="image" src="https://github.com/Carlbro31/Testing-Web-Applications-for-Vulnerabilities/assets/127357666/1dd3d4b6-4543-48f1-9a8d-7d640877ddf8">

This page is a new web application built by Replicants in order to enable their customers to ping an IP address. The webpage will return the results of the ping command to the user.

Complete the following steps to move through the intended purpose of the web application.

Test the webpage by entering the IP address 8.8.8.8. When you press "Submit" the results should display on the web application, as the following image shows

<img width="446" alt="image" src="https://github.com/Carlbro31/Testing-Web-Applications-for-Vulnerabilities/assets/127357666/b8e4d056-ad9b-4e7e-9823-fad78351bc8f">

Behind the scenes, when you select "Submit," the IP that you typed in the field is injected into a command that is run against the Replicants web server. The specific command that runs on the web server is ping <IP>, and in this case, 8.8.8.8 is the field value that was injected into that command.

This process is no different than if we went to the command line and typed the command ping 8.8.8.8, as the following image shows

![image](https://github.com/Carlbro31/Testing-Web-Applications-for-Vulnerabilities/assets/127357666/5f69ea37-696b-4a00-94e2-0f6f48ce3527)

Test whether you can manipulate the input to cause an unintended result.

On the same webpage, enter the following command (payload) in the field: 8.8.8.8 && pwd

This command uses two ampersands to add a second command to the original request:

pwd is the second command. It will display the directory location where the command is run on the Replicants webserver.

This is no different than running ping 8.8.8.8 && pwd on the command line.

Press Enter. Note that the ping results include the results of the second pwd command, as the following image shows:

![image](https://github.com/Carlbro31/Testing-Web-Applications-for-Vulnerabilities/assets/127357666/8171f5f7-a909-40e8-b5d2-c2bb2d36d659)

This type of injection attack is called command injection, and it depends on the web application taking user input to run a command against an operating system.

Now that you've determined that Replicants's new application is vulnerable to command injection, you are tasked with using the dot-dot-slash method to design two payloads that will display the contents of the following files:

/etc/passwd

/etc/hosts
