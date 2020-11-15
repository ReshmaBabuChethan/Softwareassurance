# Designing for Software Security Engineering

## Team Members:

- Shashank Tankasala
- Lucas Asato
- Bhavana Gopisetty
- Reshma Babu Chethan
- Sai Pradeep Koneti

## Introduction:

In this project, we are working on Magento, an open-source eCommerce platform that can help the users and store owners have a seamless online shopping experience. We know that it is impossible to build perfect software that is not prone to any threats, but we can always secure the software by minimizing the threats. We worked on the most threat prone scenarios and learned how Magento could reduce the risk from that particular threats by identifying the claims and evidence to support them. The top four scenarios include: 


- [DFD for login System](#dfd-for-login-system)
- [DFD for Payment System](#dfd-for-payment-system)
- [DFD for SSL Certificate System](#dfd-for-ssl-certificate-system)
- [DFD for the Catalog Management](#dfd-for-the-catalog-management)

## DFD for login System:

![DFD for login System](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/DFD%20login.PNG)

[Threat Modeling Report for Login System](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/Threat%20Modeling%20Report%20Login.pdf)

## DFD for Payment System:

![DFD for Payment System](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/Payment_Processing.PNG)

[Threat Modeling Report for SSL Payment System](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/Payment_module.pdf)

## DFD for SSL Certificate System:

![DFD for SSL Certificate System](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/SSL_Certificate_DFD.JPG)

[Threat Modeling Report for SSL Certificate System](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/SSL%20Certifcate%20process%20report%20(1).pdf)


## DFD for the Catalog Management:

![DFD for the Catalog Management](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/Admin-Catalog_DFD.JPG)

[Threat Modeling Report for Catalog Management](https://github.com/pradeepkoneti/Softwareassurance/blob/master/DFD/Admin_Catalog-Threat%20Modeling%20Report.pdf)


## Observations:

### Spoofing:

- Spoofing mitigations involve strong authentication mechanisms, including complex password requirements, two-factor authentication, requiring HTTPS, and slow password hashes. A secure implementation of an ecommerce applications would enforce strong password complexity requirements by avoiding the commonly used passwords and requiring long and [alphanumeric passwords](https://docs.magento.com/user-guide/customers/password-options.html). Requiring a secure web transfer protocol like HTTPS should be a minimum as well. For added security, requiring two-factor authentication when performing susceptible activities such as password changes and any modifications are helpful.
- Magento allows different configurations for password requirements, leaving the specific parameters open to the administrators to add. It uses the email template to change the password and recovery link can be set by admin. Magento does support use of third-party authentication mechanisms, which is the only way to implement a two-factor authentication approach. Magento require two [factor-authentication](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication.html) for all sensitive administrator level changes.
- [Session tokens](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html) will be given to every user session which will even improve the authentication and validation mechanism. 
- While coming to the spoofing of the SSL certificate which will fall under the threats like SSL stripping or tampering the mitigations are most related to the SSL certificate. Magento provides an option to configure the custom certificates which consists of robust [CA authority certificates](https://www.mageplaza.com/kb/how-to-enable-ssl-in-magento-2.html). 
- One of the most vital areas in Magento is the Admin Panel, as it has high privileged access to the site. Magento super admin will have full administrator privileges to manage all the functionalities, which includes having full permissions, access to all features and options. Magento Admin’s activities involve handling orders, preparing catalog, arrangement of shipments, CMS, design of storefront, organizing customer information, and managing configurations. Using standard authentication protocols will mitigate spoofing attacks. Magento uses a strong authentication mechanism with two-factor authentication and once authenticated then only the admin can access the Magento catalog. Magento Admin platform has the proper authentication functionality to login and maintain the application. It uses encrypted password and two-factor authentication techniques to [validate the login](https://docs.magento.com/user-guide/stores/security-admin.html). 


### Tampering:

- Mitigations for tampering most commonly include the sanitization of input data and authorization mechanisms.
- A secure Magento program should have input validation involving data types, length, character types, and an approved list validation approach.
- Magento allows mechanism to validate session variables and does input sanitization as a protective measure against possible session fixation attacks. Admin must set these [validations](https://docs.magento.com/user-guide/stores/security-session-validation.html) at configuration.
- Magento ensures that the data is not tampered during the request-response cycle between the processes and the interactors. It implements the [Response Validator](https://devdocs.magento.com/guides/v2.4/payments-integrations/payment-gateway/response-validator.html) component in the Payment modules to perform the gateway response verification. This includes low level data formatting, security verification, and execution of business logic that is required by the store configuration.

  
### Repudiation:

- Magento maintains a log record of all access, which can alert [certain threats](https://docs.magento.com/user-guide/system/action-log-report.html).
- Session tokens mechanism that is present in the magento will help for the effective management of the user records to monitor their activities. 
- Action Log feature in Magento captures every change made by an admin to the catalog. All activities will get captured in the Action Log. Admin can validate any suspicious activity by inspecting the activity logs and protect storefront sites from any interference. Any modification done to the catalog can be observed through these [logs](https://docs.magento.com/user-guide/system/action-log.html).
- Magento ensures non-repudiation with the help of the [response handler](https://devdocs.magento.com/guides/v2.4/payments-integrations/payment-gateway/response-handler.html), that processes the payment provider response, which handles the modification of order status, saving information in a transaction response. So the response handler modifies the order state only based on the payment gateway response, thus logging all the information reducing the scope for repudiation.
  
### Information disclosure:

- Magento uses Session tokens to authenticate the access and uses advanced encryption mechanism to [protect the information](https://docs.magento.com/user-guide/system/encryption-key.html#:~:text=Magento%20uses%20an%20encryption%20key%20to%20protect%20passwords%20and%20other%20sensitive%20data.&text=This%20includes%20credit%20card%20data,that%20does%20not%20require%20decryption).
- Magento provides an option to completely secure and encrypt the data that is present in the website with the help of the [SSL certificates](https://support.magento.com/hc/en-us/articles/115004685333-SSL-TLS-certificates-for-Magento-Commerce-Cloud-FAQ). 
- There is an option in the Magento to configure custom SSL certificates which has high encryption algorithms and standards.  
- Magento uses standard security certificates for encryption mechanisms such as SSL which securely validates and encrypts data that travels both ways between the browser (client) and server which prevents information disclosure when crossing trust boundaries.

### Denial of service:

- Magento implements reverse proxy to allow authorized access.
- Magento has strong access control mechanisms in order to prevent unnecessary data flow between the trust boundaries
- Magento maintains the sessions timeout which can be handled by admin.
- Magento has controllers and helpers (Fastly) inside the application which can provide services such as CDN, DDoS protection, web application firewall, SSL/TLS certificates, Origin cloaking, [image optimization](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html)
- Magento uses resources with greater availability, load balancers, and a timeout policy for every process to mitigate this threat. It uses Nginx which functions as a reverse proxy to [allow authorized access](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html?itm_source=devdocs&itm_medium=search_page&itm_campaign=federated_search&itm_term=nginx).


### Elevation of Privilege:

Standard mitigation strategies for Elevation of Privilege type threats typically include the following.
- Input validation
- Access control lists, Roles, and Groups
- Ensuring the least amount of access and information is available for given users or system  process actionsIn the context of Magento, there are two different type of privilege elevation, those done within the system and those within the machine the system is running on. For Magento, the application itself and associated processes do not need to be run with admin privileges so we do not concern ourselves with that aspect.
- Only authorized admins(Merchants) will have access to Magento Catalog/Inventory and they have strong privileges with a two-factor authentication mechanism to avoid any unwanted access. Magento avoids XSS vulnerabilities by validating and sanitizing the inputs. It also sanitizes dynamic values. This contains input and output processing to avoid [XSS attacks](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/xss-protection.html). Magento uses Content Security Policies (CSP)  to avoid [cross-site scripting attacks](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/security/content-security-policies.html?itm_source=devdocs&itm_medium=search_page&itm_campaign=federated_search&itm_term=csp).


## Reflection:

We have started this assignment by assigning each team member to create a level 0, level 1 DFD from the use case and misuse case scenario developed as part of milestone 2 previously. After finishing the DFD draft, we together discussed the created DFD diagrams and provided feedback for all the DFD diagrams. While doing that, the team discovered a few questions about how to construct the DFDs and that some diagrams had the same structure, since we were not sure what to do, we waited to have the meeting with the professor to continue the project. After the meeting with the professor, we have clarified our doubts and received some positive feedback and improvement suggestions. Once we were done with the professor meeting, we had another meeting to merge-common DFDs and combine them. Having regular meetings on time for a longer duration helped us to complete the assignment on time. Since we merged some DFDs we decided to create groups to treat their threats and create a summary draft. We suffered some problems with the threat’s generation for two DFDs, where two members were not able to generate the threats on their machines. The problem was solved by creating the same DFDs on a different member machine. In the end, we got together to check the threat’s justifications and combine our findings to create the summary. In this assignment, the team organization improved compared to the previous ones, and we could see that by how the meetings were organized and the time needed for them. The only problem encountered was the threat generation problem in some DFDs, however, this was countered by working together as a team. Overall this project helped us to learn about trust boundaries and their importance, how they can be helpful to the analysts to identify the major areas of focus. We understood the level of abstractions of the system while drawing the level 0 and level 1 diagrams.

[Project Dashboard](https://github.com/pradeepkoneti/Softwareassurance/projects/5)
[Team Meetings - MOM](https://github.com/pradeepkoneti/Softwareassurance/blob/master/MOM.md)