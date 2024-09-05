---
layout: post
title: "LEKIR - LFI2RCE"
date: 2024-09-03
categories: [write-up, blog]
excerpt: "Write up for Lekir LFI2RCE Vulnerability"
---

# LEKIR - LFI2RCE

## General Idea
Local File Inclusion (LFI) is a vulnerability that allows an attacker to include files on a server through the web browser. When combined with other vulnerabilities, such as Remote Code Execution (RCE), it can lead to severe security issues. 

In this write-up, we'll explore how LFI can be leveraged to achieve RCE, often referred to as LFI2RCE.

## Understanding LFI
LFI occurs when a **web application allows users to include files from the server using user input.** This can happen if the application improperly handles file paths provided by the user. For example, a web application might have a feature to include different views or templates based on user input:

> php
> Copy code
> <?php
> $page = $_GET['page'];
> include($page . '.php');
> ?>
> If the application doesn't properly sanitize the input, an attacker could manipulate the page parameter to include arbitrary files from the server.

## Symptoms
1. Inclusion Point In Parameter
![Inclusion Point URL](/assets/images/LEKIR-LFI2RCE/1.png)
As we can see here, The inclusion point in this picture is `page=page1.php`

2. Trying to access root directory
I'll try to access root directory by using '/../../../etc/passwd' in the parammeter
![/../../../etc/passwd](/assets/images/LEKIR-LFI2RCE/2.png)
As we can see here, we gained unathorized access to sensitive files in the server.
We can confirm that is website is exposed to LFI vulnerability.

## Exploiting LFI to Achieve RCE
Now we can move to the next stage, **Exploit The Vulnerable**

1. Clone Payload From Github
We can use the following payload to exploit the vulnerability: `page=php://filter/convert.base`
Using this tools from synacktiv, we can gain remote code execution! But this payload only works on ubuntu server from my testing

Clone From Github [php_filter_chain_generator.py](https://github.com/synacktiv/php_filter_chain_generator)

2. Crafting Our Custom Payload
We can use the following command to generate our custom payload:
![command to generate base64 encoded payload](/assets/images/LEKIR-LFI2RCE/3.png)
> python3 php_filter_chain_generator.py --chain '<?php system("ls"); ?>  '
`you can adjust the payload as you wish`

Next you will get the result:
![Result](/assets/images/LEKIR-LFI2RCE/4.png)

3. Use The Payload On Our Target
Now, We just need to copy our payload paste on target web's parameter
![payload](/assets/images/LEKIR-LFI2RCE/5.png)
As we can see,we are successfully executed our malicious payload
Now we are able to see the list of files and directory
`The result might be different depends on your payload`

## LFI Prevention Tips:

### Sanitize Inputs: 
Ensure all user inputs are validated and sanitized to prevent malicious file paths and commands.

### Use Whitelists: 
Restrict file inclusion to a predefined set of safe files.

### Secure Code Practices: 
Avoid executing user-supplied data or untrusted code.