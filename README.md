# sqlinjection
Exploiting SQL Injection vulnerability

# AIM:
To exploit SQL Injection vulnerability using Multidae web application in Metasploitable2

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode


### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

SQL Injection is a sort of infusion assault that makes it conceivable to execute malicious SQL statements. These statements control a database server behind a web application. Assailants can utilize SQL Injection vulnerabilities to sidestep application safety efforts. They can circumvent authentication and authorization of a page or web application and recover the content of the whole SQL database. 
Identify IP address using ifconfig in Metasploitable2
#OUTPUT
<img width="1141" height="487" alt="Screenshot 2026-09-05 082719" src="https://github.com/user-attachments/assets/3da84251-5a20-4e1a-924f-a795fac30882" />


Use the above ip address to access the apache webserver of Metasploitable2 from kali/parrot linux. In Kali Linux use the ip address in a web browser.
##  OUTPUT
<img width="1150" height="629" alt="Screenshot 2026-09-05 082800" src="https://github.com/user-attachments/assets/8ed96384-95fa-42a5-bbbd-a8653b68e6eb" />



Select Multidae from the menu listed as shown above. The page is displayed as below:
##  OUTPUT

<img width="1117" height="706" alt="Screenshot 2026-09-05 082822" src="https://github.com/user-attachments/assets/4ff1b9df-fc1c-4d6a-8010-01d5ef7ad773" />


Click on the menu Login/Register and register for an account
##  OUTPUT
<img width="1116" height="660" alt="Screenshot 2026-09-05 082842" src="https://github.com/user-attachments/assets/bdc31c41-0734-4308-9c9e-1f3302a1e79f" />



Click on the link “Please register here”
##  OUTPUT

<img width="1096" height="686" alt="Screenshot 2026-09-05 082901" src="https://github.com/user-attachments/assets/de94c00a-798a-4336-82fb-9c3806ecd339" />


Click on “Create Account” to display the following page:
##  OUTPUT
<img width="1103" height="695" alt="Screenshot 2026-09-05 082920" src="https://github.com/user-attachments/assets/a58cd716-81e1-427a-b142-69f6221399b0" />


The login structure we will use in our examples is straightforward. It contains two input fields (username and password), which are both vulnerable. The back-end content creates a query to approve the username and secret key given by the client. Here is an outline of the page rationale:


($query = “SELECT * FROM users WHERE username=’$_POST[username]’ AND password=’$_POST[password]’“;).
 For the username put “ganesh” or “anything” and for the password put (anything’ or ‘1’=’1) or (admin’ or ‘1’=’1) then try to log in, and you’ll be presented with an admin login page.
##  OUTPUT

<img width="1059" height="683" alt="Screenshot 2026-09-05 082940" src="https://github.com/user-attachments/assets/e99a35d7-0ed9-4699-83fa-95bc571bc522" />


Click “Login”. The logged in page will show as below:
##  OUTPUT

<img width="1078" height="595" alt="Screenshot 2026-09-05 082957" src="https://github.com/user-attachments/assets/c04b10f2-d593-4a3e-a438-376916362c02" />


If error faced in registration follow the following steps in metasploitable 2:


This issue is caused by a misconfiguration in the config.inc located in the /var/www/mutillidae folder on Metasploitable 2 VM.

Edit config.inc
Edit config.inc file located in /var/www/mutillidae folder on Metasploitable 2 by typing the following commands [one at the time]:
cd /
sudo nano /var/www/mutillidae/config.inc
Type msfadmin when prompted for the root password. 
Once nano opens config.inc file, look for the line $dbname = ‘metasploit’ as shown in Figure  below:
##  OUTPUT

<img width="1137" height="629" alt="Screenshot 2026-09-05 083104" src="https://github.com/user-attachments/assets/66be0624-7fb7-4cb8-8159-1f201b62649c" />

Replace ‘metasploit’ with ‘owasp10’ and make sure the lines end with semicolon ; as shown in Figure
##  OUTPUT

<img width="1122" height="109" alt="Screenshot 2026-09-05 083128" src="https://github.com/user-attachments/assets/ed41f34e-f4bb-44f5-b72b-749ecde02c5e" />



Save and exit the config.inc
Save than exit the config.inc file by typing CTRL+X keys on your keyboard and the Y [Enter] when prompted to save the file
Restart the Apache server
To restart Apache, type the following command in the terminal. Alternatively, you can just reboot Metasploitalbe 2 VM.
sudo /etc/init.d/apache2 reload
##  OUTPUT

<img width="1106" height="679" alt="Screenshot 2026-09-05 083151" src="https://github.com/user-attachments/assets/0e84bf8d-d822-4b2e-8f4b-4949bd5d03ae" />



# Reset Mutillidae database
Refresh the page then clicking on the Reset DB menu option to reset the Mutillidae database [Figure ]. Click OK when prompted.
##  OUTPUT

<img width="1106" height="679" alt="Screenshot 2026-09-05 083151" src="https://github.com/user-attachments/assets/b74bfc20-b6a9-46c9-bb1c-fbcf5c216d3b" />




# Test the new configuration
Alright. Now is time to test if we managed to fix the database issue. Go ahead and register a new account on the Mutillidae webpage.

 The Mutillidae database error no longer appears 
#OUTPUT

<img width="1120" height="726" alt="Screenshot 2026-09-05 083218" src="https://github.com/user-attachments/assets/6231baac-12e7-40b7-b84e-44abe78f6b9b" />


Now after logging out you will see the login page. In the login page give ganesh’ # (myusername). You can see the page now enters into the administrator page as before when giving the password.
#OUTPUT
<img width="1108" height="801" alt="Screenshot 2026-09-05 083238" src="https://github.com/user-attachments/assets/b467980f-e9e4-4cee-868e-c9507ba7c9c0" />


Click the login button and you will see it enter into the administrator page.
#OUTPUT
<img width="1130" height="676" alt="Screenshot 2026-09-05 083258" src="https://github.com/user-attachments/assets/3be03df1-6ac9-4df5-9937-abfb29436003" />



## Union-based SQL injection

UNION-based SQL injection assaults enable the analyzer to extract data from the database effectively. Since the “UNION” operator must be utilized if the two inquiries have precisely the same structure, the attacker must craft a “SELECT” statement like the first inquiry. 
we will be using the “User Info” page from Mutillidae to perform a Union-Based SQL injection attack. Go to “OWASP Top 10/A1 — Injection/SQLi — Extract-Data/User Info” 

After logging out, Now choose the menu as shown below:
##  OUTPUT
<img width="1142" height="679" alt="Screenshot 2026-09-05 083319" src="https://github.com/user-attachments/assets/382c06a6-9f48-4153-a7f1-c4af761ba441" />



From this point, all our attack vectors will be performed in the URL section of the page using the Union-Based technique.There are two different ways to discover how many columns are selected by the original query. The first is to infuse an “ORDER BY” statement indicating a column number. Given the column number specified is higher than the number of columns in the “SELECT” statement, an error will be returned.
##  OUTPUT
<img width="1092" height="725" alt="Screenshot 2026-09-05 083341" src="https://github.com/user-attachments/assets/5a9bfdda-a499-454c-9f6c-1336c6e50df1" />



Since we do not know the number of columns, we start at 1. To find the exact amount of columns, the number is incremented until an error related to the “ORDER BY” clause is returned. In this example, we incremented it to 6 and received an error message, so it means that the number of columns is lower than 6.

The browser url of this info page need to be modified with the url as below:
##  OUTPUT
<img width="1126" height="717" alt="Screenshot 2026-09-05 083403" src="https://github.com/user-attachments/assets/46fcbb66-45ba-4332-b269-078129859d92" />




After adding the order by 6 into the existing url , the following error statement will be obtained:
##  OUTPUT

<img width="1138" height="664" alt="Screenshot 2026-09-05 083420" src="https://github.com/user-attachments/assets/52b53666-2b7c-49a7-b399-2a29e59c8267" />



When we ordered by 5, it worked and displayed some information. It means there are five columns that we can work with. Following screenshot shows that the url modified to have statement added with ordered by 5 replacing 6.
#OUTPUT

<img width="1144" height="699" alt="Screenshot 2026-09-05 083438" src="https://github.com/user-attachments/assets/3f476dcc-49d6-4aa9-8dd6-23e91c4e8557" />



 As it is having 5 columns the query worked fine and it provides the correct result
##  OUTPUT

<img width="1089" height="665" alt="Screenshot 2026-09-05 083457" src="https://github.com/user-attachments/assets/c664385e-415c-423c-b1e4-d58a422b3a1f" />



Instead of using the "order by" option, let’s use the "union select" option and provide all five columns. Ex: (union select 1,2,3,4,5).
##  OUTPUT

<img width="1131" height="728" alt="Screenshot 2026-09-05 083518" src="https://github.com/user-attachments/assets/a5fa39a1-9615-4c1f-9b38-7c12985dc0de" />


As given in the screenshot below columns 2,3,4 are usable in which we can substitute any sql commands to extract necessary information.
##  OUTPUT

<img width="1120" height="727" alt="Screenshot 2026-09-05 083536" src="https://github.com/user-attachments/assets/9318ea9f-a3f1-4045-a09a-72f4f0dcd283" />


## RESULT:
The SQL Injection vulnerability is successfully exploited using the Multidae web application in Metasploitable2.
