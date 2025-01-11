# Phishing-Analysis-Fundamentals

THM: https://tryhackme.com/r/room/phishingemails1tryoe

Task 1
Introduction

Spam and Phishing are common social engineering attacks. In social engineering, phishing attack vectors can be a phone call, a text message, or an email. As you should have already guessed, our focus is on email as the attack vector. 

![p1-split-view](https://github.com/user-attachments/assets/35017a61-b26e-45d3-8761-81cd85398913)


Task 2
The Email Address

The invention of the email dates back to the "1970s" for ARPANET. Yep, probably before you were born. Definitely, before I was born. :)

So, what makes up an email address?

User Mailbox (or Username)
@
Domain
Let's look at the following email address, billy@johndoe.com.

The user mailbox is billy
@ (thanks Ray)
The domain is johndoe.com
To simplify this even further, think about the street on which you live on.

You can think of your street as the domain. 
The recipient's first/last name, along with the house number in this scenario, represents the user mailbox. 

Email dates back to what time frame?

```
1970s
```


Task 3
Email Delivery

There are 3 specific protocols involved to facilitate the outgoing and incoming email messages, and they are briefly listed below.

SMTP (Simple Mail Transfer Protocol) - It is utilized to handle the sending of emails. 
POP3 (Post Office Protocol) - Is responsible transferring email between a client and a mail server. 
IMAP (Internet Message Access Protocol) - Is responsible transferring email between a client and a mail server. 

POP3

Emails are downloaded and stored on a single device.
Sent messages are stored on the single device from which the email was sent.
Emails can only be accessed from the single device the emails were downloaded to.
If you want to keep messages on the server, make sure the setting "Keep email on server" is enabled, or all messages are deleted from the server once downloaded to the single device's app or software.
IMAP

Emails are stored on the server and can be downloaded to multiple devices.
Sent messages are stored on the server.
Messages can be synced and accessed across multiple devices.

![email-network-flow-4](https://github.com/user-attachments/assets/177c20a1-f299-4c9c-b4b4-b8145407448f)


What port is classified as Secure Transport for SMTP?
```
465
```
What port is classified as Secure Transport for IMAP?
```
993
```
What port is classified as Secure Transport for POP3?
```
995
```

Task 4
Email Headers

Before we begin, we need to understand that there are two parts to an email:

the email header (information about the email, such as the email servers that relayed the email)
the email body (text and/or HTML formatted text)
The syntax for email messages is known as the Internet Message Format (IMF).

Let's look at email headers first. 

What do you look for when analyzing a potentially malicious email?

Let's start with the following email header fields:

From - the sender's email address
Subject - the email's subject line
Date - the date when the email was sent
To - the recipient's email address


Warning: This is a snippet from an actual email. The email in the below image is from a honeypot Yahoo email address. Don't engage/interact with the email addresses or IP addresses revealed in this room.

![email-headers-1b](https://github.com/user-attachments/assets/ccdc8d8c-6acc-4c1b-83c7-ffc36b557d56)

Another method to obtain the same email header information, and more, is by viewing the 'raw' email details.

![email-raw-headers-menu-2](https://github.com/user-attachments/assets/5c58896a-f752-41ab-b0c0-883027f841b9)


![email-raw-headers-2b](https://github.com/user-attachments/assets/4f05bc98-f380-410f-9d8d-3c6e47a0d312)

Below is an additional resource from Media Template on how to analyze email headers:

 https://web.archive.org/web/20221219232959/https://mediatemple.net/community/products/all/204643950/understanding-an-email-header


What email header is the same as "Reply-to"?
```
Return-Path
```
Once you find the email sender's IP address, where can you retrieve more information about the IP?
```
http://www.arin.net
```

Task 5
Email Body

The email body is the part of the email which contains the text (plain or HTML formatted) the sender wants you to view. 

![email-text-2](https://github.com/user-attachments/assets/67b28864-3abd-46b5-b998-6991cba75087)


HTML is what makes it possible to add these elements to an email.

To view an email's HTML code is the same approach shown below, but it may vary depending on the webmail client. 

![email-source-code-2](https://github.com/user-attachments/assets/911d6305-d657-4eb5-b19e-609c9fbd916d)

In this specific email web client, Protonmail, the option to switch back to HTML is called "View rendered HTML".


![email-render-html](https://github.com/user-attachments/assets/0e224066-302c-406c-96e6-ec333e9b2490)

Let's look at a few examples below.

The following example is an HTML formatted email from "Netflix" with an attachment. The web client is Yahoo!

![email-with-attachment](https://github.com/user-attachments/assets/137f1dd4-8ba9-471f-abb3-a0b50cd026ae)

The email body has an image.
The email attachment is a PDF document.
Now let's view this attachment within the source code.

![email-with-attachment-2](https://github.com/user-attachments/assets/5082df9d-478f-4cdd-ac06-000629230892)


Content-Type is application/pdf. 
Content-Disposition specifies it's an attachment. 
Content-Transfer-Encoding tells us it's base64 encoded. 

In the above screenshots, what is the URI of the blocked image?
```
https://i.imgur.com/LSWOtDI.png
```
In the above screenshots, what is the name of the PDF attachment?
```
Payment-updateid.pdf
```
In the attached virtual machine, view the information in email2.txt and reconstruct the PDF using the base64 data. What is the text within the PDF?
```
THM{BENIGN_PDF_ATTACHMENT}

```

Task 6
Types of Phishing

Different types of malicious emails can be classified as one of the following:

Spam - unsolicited junk emails sent out in bulk to a large number of recipients. The more malicious variant of Spam is known as MalSpam.
Phishing -  emails sent to a target(s) purporting to be from a trusted entity to lure individuals into providing sensitive information. 
Spear phishing - takes phishing a step further by targeting a specific individual(s) or organization seeking sensitive information.  
Whaling - is similar to spear phishing, but it's targeted specifically to C-Level high-position individuals (CEO, CFO, etc.), and the objective is the same. 
Smishing - takes phishing to mobile devices by targeting mobile users with specially crafted text messages. 
Vishing - is similar to smishing, but instead of using text messages for the social engineering attack, the attacks are based on voice calls. 

What trusted entity is this email masquerading as?
```
Home Depot
```
What is the sender's email?
```
support@teckbe.com
```
What is the subject line? 
```
Order Placed : Your Order ID OD2321657089291 Placed Successfully
```
What is the URL link for - CLICK HERE? (Enter the defanged URL)
```
hxxp[://]t[.]teckbe[.]com/p/?j3=EOowFcEwFHl6EOAyFcoUFV=TVEchwFHlUFOo6lVTTDcATE7oUE7AUET==
```

Task 7 
Conclusion 

A BEC is when an adversary gains control of an internal employee's account and then uses the compromised email account to convince other internal employees to perform unauthorized or fraudulent actions. 

What is BEC?
```
Business Email Compromise
```
