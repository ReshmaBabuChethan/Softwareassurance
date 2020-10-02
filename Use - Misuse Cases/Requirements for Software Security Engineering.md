# Requirements for Software Security Engineering

## Introduction

The open-source system we have selected is Magento, which is an eCommerce platform that can help store owners to have a flexible shopping cart and all the functionalities of the online store. As we know, the eCommerce system will have different integrations and interactions; hackers will take leverage on those and try to launch various attacks on the system in a real-time environment. We have identified below five interactions of the Magento open-source software. 

- [Login System](#login-system)
- [Admin Login and access prevention](#admin-login-and-access-prevention)
- [Admin Activities](#admin-activities)
- [Order Management System](#order-management-system)
- [SSL Upgrade for the Website](#ssl-upgrade-for-the-website)

## Login System

![Login System Misues Case](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Use%20-%20Misuse%20Cases/Misuse%20case%20for%20Login%20system.jpeg)

### Use case:
The website client wants to make a purchase on the website. For that the client can create an account or if already had one login to it. The account can store different personal information, such as name, last name, address, phone number, credit card number and others.

### MisUse Case:
A hacker with the intention of stealing the user information, or even use the online shop for them, can use different attacks to achieve its purpose, such as: 
- Dictionary attacks: that takes advantage of the fact that people tend to use common words and short passwords;
- Brute force attacks: that normally use a program to generate likely passwords or random character sets;
- Keylogging: that records the keys struck on a keyboard;

### Security Requirement:
Since dictionary attacks and brute force attacks are similar, these attacks can be prevented with similar actions that includes that the user is required to use strong passwords (at least 8 characters, mixture of both uppercase and lowercase letters, a mixture of letters and numbers, inclusion of at least one special character), the website to limit the max number of logging attempts, use of captcha and enable the use of two steps verifications.
For the keylogging, the system can enable the use of two steps verifications and prompt the software owner to update the software regularly.

### Relevant Advertised Security Features of Magento:
Magento provides multiple tools to enhance the security of the website, such tools can cover the treats of the login MisUse case. This is described in the magento [user guide](https://docs.magento.com/user-guide/stores/security.html) in the Security section. A few of the tools offered are:
- Magento Security Scan: which allows the user to monitor Magento sites for known security risks, and to receive patch updates and security notifications;
- CAPTCHA: which allows the site owner to enable captcha;
- Two-Factor Authentication: which allows the use of two-factor authentication;
- Set Password Protection: which allows the recovery of the password just from the owner email; account sharing that disallow logging from same account on different devices; and limit the lifetime of password.
- Account Security: that allows the user to configure their admin panel to limit the number of passwords reset requests per hour and the maximum login failures to lockout account 

 ## Admin Login and access prevention:
One of the most resourceful areas in Magento is the Admin Panel, as it has high privileged access to the site. Magento super admin will have full administrator privileges to manage all the functionalities, which includes having full permissions, access to all features and options. Admin uses the UI panel to modify/configure the Magento system and storefront parameters.  
 - A Trespasser wants to access the Magento Admin panel to defame it. He has no permission, so he will try to guess the System Admin’s password using Brute force attack. Authorized login and 2-factor authentication at site prevents this attack. As a safety net and extra precaution, there could be a minimum time set for, recovery link expiration; time between each password reset requests and for Admin session lifetime. Additionally, enabling the Account Lockout time feature enables us to lock out the admin account after the maximum number of attempts is met, and also we can set the maximum number of times a user can try to login before the account gets locked, which further mitigates such attacks. To prevent password guessing, Magento Admin uses whitelisting of IP addresses and enabling non-default admin URL (through command line and env.php files) techniques. This avoids password capturing.
 
	 A Trespasser wants to access some restricted resources on the site. Any unauthorized access to restricted resources can also be avoided by setting proper user roles and specific resource access.
	 
 - Trespassing also involves destroying the file system. File system security is complex and extremely important. Trespasser wants to sneak into the Magento file system to access and destroy the files. However, System Admin prevents this action by setting proper ownership and access permission on every file, based on usage. To facilitate this, Magento uses umask (file system creation mask) to further restrict the access, this provides special security on a shared hosting production system. 
 
 	![Admin Login - Use/ Misuse case diagram](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Use%20-%20Misuse%20Cases/AdminLogin-%20use_misuse_cases.jpeg)

 ## Admin Activities:
Magento Admin’s activities involve handling orders, preparing catalog, arrangement of shipments, CMS, design of storefront, organizing customer information, and managing configurations. It is not handled by a single person but consists of a set of admin groups with Super Admin and Division Admin privileges for separate divisions. Customer maintenance, Catalog/Inventory management, and Magento Order Management (MOM) also known as Order Management System (OMS) are all controlled by respective admins from individual departments.

- A Gangster wants to ruin the Magento site by inserting a virus which includes content spoofing or to insert malicious content through email or infected software. Admin can keep the Magento storefront site clean from known security risks by conducting frequent security scans on a daily/weekly or on-demand basis. This includes patch updates, security notifications, and virus protection updates. Magento also provides security reviews to check for signs of an attack and the latest potential vulnerabilities. They also ensure best practices through the security registry alert and security center. Magento malware and vulnerability monitor inspects for any security issues with files, databases, and admin accounts. With all these in place, Magento Admin’s can avoid Gangsters inserting malicious viruses or content into their sites.

- A Gangster wants to delete store data entirely/partially.  Whereas Magento Admin holds a backup of their complete repository taken regularly and with proper Disaster Recovery along with a well-versed Business Continuity Plan in place, Magento can continue with an uninterrupted business performance. In an E-commerce website even if something goes wrong businesses should continue to serve their customers otherwise it creates reputation problems and unexpected losses. To handle this, proper data backup is mandatory. Any data loss caused by unexpected parties can be reversed to its original state.

- A Gangster wants to send some hijacking content to the store site. To do so he keeps checking to identify any possible loopholes. Magento Admin configuration enables Admin’s to capture any action from a user at their site in Action Logs. All these Trespasser’s activities will get captured in the Action Log. Admin can validate any suspicious activity by inspecting the activity logs and protect storefront sites from any interference. Also, the firewall and Session validation feature at the system admin configuration protects against any session fixation attacks or attempts to poison or hijacking site sessions. Validating and sanitizing user inputs/dynamic values can help prevent XSS vulnerabilities. Additionally, it has XSS prevention at site which involves Content Security Policies that help to mitigate against Cross-Site Scripting attacks, card skimmers, session hijacking, clickjacking, etc. 
	
	Action log records every change that was made to the store. This log feature captures Name, object ID, action-outcome, date, and IP address. Admin’s can use these captured logs for further evaluation.
	
	![Admin Activities - Use/ Misuse case diagram](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Use%20-%20Misuse%20Cases/AdminActivities-%20use_misuse_cases.jpeg)

### Alignment of Security requirements with advertised features:

#### Admin login and access prevention
- Magento Admin platform has the proper authentication functionality to login and maintain the application. It uses encrypted password and 2-factor authentication techniques while login. Super admin can have the complete access and set roles to different users. Magento admin uses umask file permission to restrict file access. This way of restricting access will give enhanced security to resources.
	- [Admin Login](https://docs.magento.com/user-guide/stores/security-admin.html)
	- [Access Permission](https://docs.magento.com/user-guide/system/permissions.html)
	- [File Permission](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html#restrict)
	- [User Roles](https://docs.magento.com/user-guide/system/permissions-user-roles.html)

#### Admin Activities
-   Magento Admin activities involves securing and managing the site data. XSS prevention and CSP enables cross-site scripting attacks. Regular patch updates, monitoring the scanning tools help to keep the site safe. Admin can also conduct regular security scans to keep the storefront site free from known risks. A proper data backup and business continuity plan can avoid any data loss. Also, it helps to continue the business without any disruptions.
	- [CSP](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/security/content-security-policies.html)
	- [Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html)
	- [XSS Prevention](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/xss-protection.html)



## Order Management System

![Order Management System Misuse Case](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Use%20-%20Misuse%20Cases/Mis-use%20Case%20Diagram%20Template%20(1).jpeg)

### Use case:
This usecase emphasizes on the scenario where a responsible OMS(Order Management System) admin tries to secure the customer details and their payment credentials by monitoring the network regularly, performing regular scans and vulnerability security assessments.The payment modules in this scenario includes the payment gateway through which the customers pay the bills either by using their credit card or through paypal.So it is the responsibility of the OMS admin to secure the personal details of the customers and their credit card credentials.

### MisUse Case:
Hustler in this scenario is a hacker who is interested in stealing the card details of the customers and stealing their money. He tries to attack the system in all possible ways to get access to that system by introducing malicous code and performing digital skimming which is one of the biggest threats to the e-commerce payment gateways. He utilizes Magecart,for his attack during which he modifies the mage.php code in Magento websites cart sections.This kind of cyber attack works for the hackers as it allows them to exploit the known software vulnerabilities to inject malicious JavaScript code into online checkout software systems. It has a relatively low barrier to entry, making credit card skimming a walk in the park. [Magento Killer](https://magenticians.com/magento-killer/) is the other attack methodology the hustler follows by modifying the core_config_data table which allows him to get the payment information from the compromised Magento store. 
 

### Security Requirement:

To mitigate these threats it is important to identify the vulnerabilities of the store. Magento provides a tool, Magento security scan tool that scans the stores and reports all potential vulnerabilities and any available patches that fix the issues.Magecart attackers are known for [card skimming](https://www.stratica.com.au/how-to-stop-digital-skimming-e-commerce-s-greatest-security-threat) or silent card capture,they exploit a vulnerability and tap the data coming through the shopping cart. One of the biggest dangers of this is that it can go undetected for a long period of time.Without security patches and regular scans and updates, there is high risk of data breach if new vulnerabilities are discovered.This can lead to compatibility issues with third-party integrations, leading to instability and inconsistent site performance. 


### Relevant Advertised Security Features of Magento:
Magento releases regular updates that provide bug fixes and performance improvements.Magento provides a tool, [Magento security scan tool](https://magento.com/blog/magento-news/introducing-new-magento-security-scan-tool) that scans the stores and reports all potential vulnerabilities and any available patches that fix the issues. Magento provides some security extensions to help reinforce the security of the website.These extensions offer features like the ability to block certain IP addresses,strengthen login security, protect against fraudulent orders and payments, and detect and remove malware.Magento’s Security Center offers a free scan can be used to monitor security risks, updating malware patches, and detecting any unauthorized access to the website.





## SSL Upgrade for the Website: 

![SSL certificates Use Case](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Use%20-%20Misuse%20Cases/Mis-use%20Case%20Diagram%20SSL.jpeg)


In this use case and misuse case diagram, we can look at the advantages of having the SSL certificates in the open-source software Magento.

### Use case:

In this use case, Joe the secure-minded user wants to access the eCommerce website that is being hosted using the Magento open-source software. Stuart the administrator who is also careful with the security of the data and transactions has included the SSL certificate for the website using the available options in the Magento open-source software.  

### MisUse Case:

Eric, the eavesdropping hacker, wants to get hold of the transaction or data to launch some phishing attacks as per the information collected. Initially, he will try to make the session hijack attacks by taking leverage on logging into the website. Still, knowing hackers like Eric will be commonly attacking the eCommerce websites, Stuart has added the SSL certificate to the website and even enabled the front end option, Admin URLs to use the certificate. This way, the login of all the users and admins will be secured and can prevent attacks like the Eric's session Hijack. As the Eric is aware that the administration is using the SSL certificate through the eCommerce website, he will try to launch attacks like Man in the middle and SSL Stripping. So, in attacks like SSL stripping Eric will take leverage on the certificate validity and expiration. Suppose the certificate is expired or not valid. In that case, hacker will try to attack the traffic that is happening between the users and the website, then attacks as the agent that receives information from the website and gives it to the user. As the hacker is doing the transaction, he can completely use that information and take advantage of that by doing phishing attacks or fraudulent transactions. This scenario will be a typical case with the Man in the middle attack to leverage the user information. To completely prevent that kind of scenario, our secure admin Stuart monitors the SSL certificates through the Magento features. As there is also an option for using the custom certificate instead of the one that is provided by Magento, Stuart can completely prevent the eavesdropping attacks by using certificates from trusted certificate authorities and robust hashing algorithms with the digital signature.   


### Security Requirement:

SSL certificate is mandatory for the ecommerce websites, because the transaction that will be happening through the website contains the financial information and credentials of the users. If the data is not encrypted then Hackers like Eric, can easily leverage on the data by doing some man in the middle attacks. 

### Relevant Advertised Security Features of Magento:

Magento has given the process for installing the [SSL certificates](https://www.cloudways.com/blog/install-ssl-magento/) for the websites that use this open-source software. They have clearly stated that using custom SSL certificates can prevent websites from different kinds of attacks, making the website more secure. Once the administrator installs the certificate, there is an option to add that certificate to different Urls like login, which will prevent the attacks like session Hijacking. 


## Installation and security related configuration in Magento

All e-commerce sites are the main targets of the hackers as they are involved in the payment system to complete the order. They have provided the clear documentation part of [installation](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements-tech.html), such as: operating systems supported by Magento, the system requirements needed, what version of the system supports Magento and others. Magento provides clear instructions on installation using the compressed files, [composer and through the code](https://devdocs.magento.com/guides/v2.4/install-gde), however the installation of Magento can have a few problems. For an instance, while using composer or using command line instructions problems can be encountered with the PHP-extensions,as we can see in [xdebug]((https://support.magento.com/hc/en-us/articles/360034242212)), where the problems with PHP dependencies installation cause common errors during the installation of Magento, since different Magento versions requires specific PHP dependencies. Other problems that can occur are related with different versions of PHP, as all versions of PHP are not supported for Magento installation. Magento documentation acknowledge the supports of the PHP versions 7.0 and above excluding the 7.2 version, as it has problems with browser cookies and message rendering in the application.Before Magento 2.4.0 merchants need to install and configure the official Braintree payment integration extension from the Magento Marketplace from Magento 2.4.0, the extension are included in the Magento release.

Coming to the security, the major security issues of the Magento are cross-site scripting attacks, remote code execution attacks, and recent attacks like the Magecart attack, where Magento killer has occurred in recent years which is considered Majento major [security breaches](https://en.wikipedia.org/wiki/Magento#Security_concerns) till date. Coming to the security,  The security-related practices documentation is provided for the Magento project is very good which covers all parts of the [application security](https://docs.magento.com/user-guide/magento/magento-security-best-practices.html) like configuring, and installing the [SSL certificate](https://magenticians.com/how-to-install-enable-magento-ssl/) can be easily done and renewed which adds security to all the store admins, admins, and users of Magento. 

- SSL/TLS settings are configured to include supported protocols, controlling the server&#39;s behavior with respect to requesting a certificate from client connections. Also, the verification that the certificates have been signed by a trusted authority. Configurations can be made inside the Magento system to contain the private key and certificates to be trusted.
- Magento uses an encryption key to protect passwords and other sensitive data.AES-256 algorithm is used to encrypt all data that requires decryption. Besides, a strong Secure Hash Algorithm (SHA-256) is used to hash all data that does not require decryption
- Admin login activities in Magento are secured by the making admins creating strong passwords, two-factor authentications with one-time passcode and another feature CAPTCHA can also be configured.
- Magento system can validate the session variables as a protective measure against possible session fixation attacks or hijack user sessions.
- Magento requires that the visitor&#39;s browser allow both cookies and JavaScript for full operations. To do that the user&#39;s browser is set to the highest privacy setting that prevents both cookies and JavaScript. Magento systems can be configured to test the capabilities of each visitor&#39;s browser and display a notice to the user of Magento if the settings need to be changed.
- All types of users in the Magento system are assigned roles to limit the access of the user to specific things.
- The easy way to protect the environment is to keep all software on the server up to date and apply security patches as recommended by Magento and Magento uses only secure communication protocol (SSH/SFTP/HTTPS) to manage files inside the system.

## Reflection

Initially, we had a brainstorming session to identify the scenarios that fall under our system of interest. All of us came up with different scenarios, and after discussing each scenario's scope, we narrowed them down to 5 significant cases. We proactively chose one scenario each and decided to draw the use case diagram with its misuse case scenario in it. After having our weekly meeting, we showcased the diagrams and after review every team member suggested some changes in our diagrams. Later after receiving some review comments after we met with our professor, we understood that we should not have repetitive scenarios in diagrams. The diagrams should also be speaking the intention of the actors. This was a little challenging for us to differentiate the scope of each scenario. So, we have divided the scenarios and started working on different break out sessions for scenarios that have colliding use cases. This approach helped us track down the overlap easily and to make the neccessary modifications. 

As discussed above, it was challenging for our entire team to differentiate the scope of colliding scenarios and confine them under the scope of Magento handling those scenarios. But the break out sessions helped us to solve that issue. Going forward, we came up with an approach that in case of any problem or blocks on the tasks that they got assigned, every team member will create an issue with the tag "help wanted" and explain their blocks, so other team members can help them to overcome those blocks. 

On the whole, this assignment helped us a lot to know more about the use cases and the features that each system must possess to overcome the threats in the real-time environment.  
                                                                                                                                                                                                                                                                                                       
[Weekly Meetings - MOM](https://drive.google.com/file/d/1HtXY2KkCGCrKeiqnB67zMyCiiH6OsySF/view?usp=sharing)
 
