# Assurance Cases for Software Security Engineering


## Introduction:

In this project, we are working on Magento, an open-source eCommerce platform that can help the users and store owners have a seamless online shopping experience. We know that it is impossible to build perfect software that is not prone to any threats, but we can always secure the software by minimizing the threats. We worked on the most threat prone scenarios and learned how Magento could reduce the risk from that particular threats by identifying the claims and evidence to support them. The top five scenarios include: 


- [Magento minimizes SQL injections](#assurance-claim-1-magento-minimizes-sql-injections)
- [Magento minimizes data hijacking](#assurance-claim-2-magento-minimizes-data-hijacking)
- [Magento minimizes malicious code](#assurance-claim-3-magento-minimizes-malicious-code)
- [Magento minimizes leakage of sensitive data](#assurance-claim-4-magento-minimizes-leakage-of-sensitive-data)
- [Magento Software minimizes unauthorized login access](#assurance-claim-5-magento-software-minimizes-unauthorized-login-access)


## Assurance Claim 1: Magento minimizes SQL injections

![Assurance Case_ SQL injection](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Assurance%20Case/Assurance%20Case_%20SQL%20injection.jpeg)

### Evidences:

- E1.1 – Magento security center: Our sub-claim C1.1 assures that third parties extensions developers are provided with best practices documentations for developing their product. However, even with best practices documentation these extensions can still have SQL injection vulnerabilities. We address this problem with sub-claim C1. 5, where Magento provides a webpage called [Security Center](https://magento.com/security), which gather security information for Magento, which includes new patches releases, security updates, security alerts, best practices, and others. In this page, Magento also announces common third-party extensions known vulnerabilities, and advise it users to fix these problems as fast as possible to improve user’s security, consequently minimizing SQL injections on the system. 

- E1.2 – Magento security scanner: Our sub-claim C1.2 assures that even if the user does not follow Magento’s best practices it can still be protected by performing security checks. However, sometimes user does not have the time or does not remember to do them. We address this problem with sub-claim C1.6, where Magento provides a security Scan tool. [Magento security Scan](https://docs.magento.com/user-guide/magento/security-scan.html), is a tool that allows the user to monitor the sites for known security risks and enable the user to schedule security scan. The tool, in the end of the scan, provides reports with the results and the possible recommended corrective actions for solving.

- E1.3 – Magento Commerce Cloud: Our sub-claim C1.3 assures that even if the user does not follow Magento’s best practices it can still improve its protection by using a firewall. However, the user might not know which firewall to use. We address this problem with sub-claim C1.7, where Magento provides a web application firewall [WAF](https://devdocs.magento.com/cloud/cdn/fastly-waf-service.html) powered by Fastly, which detects, logs, and blocks malicious request traffic before it can damage the site or network. Magento WAF includes specific filters for SQL injection attacks and its [variant](https://support.magento.com/hc/en-us/articles/360016353452--Web-Application-Firewall-WAF-powered-by-Fastly-the-FAQ). Unfortunately, this service does not support protection against malware or bot mitigation, rate limiting and configuring a logging endpoint for customer.

- C1.8 and C1.9 – Our sub-claim C1.4 assures that that even if the user does not follow Magento’s best practices the user can still improve its protection by reviewing their code and repairing the possible threads. However, we cannot assume that the user knows how to do it or that they can do it effectively. We address this problem with sub-claim C1.8 and C1.9, where Magento could provide web vulnerability scanners and SQL injection attack tools to help the user to find the threads on their system and consequently fixing the possible threads for SQL injections on their system.

## Assurance Claim 2: Magento minimizes data hijacking

The data that is being managed in the eCommerce websites is very crucial and critical. Because a loss of that data can result in serious ill fame to the entire organization, many hackers will be trying to get that data because it involves mostly personal details or financial information. In this assurance claim, we are trying to present the assurance strategies of the Magento to reduce the risk of the data hijacking from the websites that are using the open-source software. One a whole, we can say that data that is being managed on the websites will be encrypted or appropriately secured. 

![Assurance Case SSL Certificate](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Assurance%20Case/Assurance%20Case%20SSL%20Certificate.jpeg) 

### Evidence E2.1:

The top Claim C2 leads to a rebuttal R 2.1 that what if the Magento is transferring the data in plain text format. We address this issue with sub claim 2.1, stating that Magento provides an option to encrypt the data transfer between the system and the users with the [SSL certificates' help](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#fastly-tls). Then another rebuttal R2.2 arises that what if there is a scenario that SSL certificate used was expired. Then we can address this issue with the claim that there will be validation regarding the certificates and the remainders, which can be seen in the Magento Documentation. This brings us to the Evidence 2.1. Magento [provides notifications](https://www.magecloud.net/marketplace/extension/ssl-certificate-reminder-and-validator/) on the SSL certificates with extensions' help; it can even validate the certificate. 

### Evidence E2.2:

In the previous sub claim, it is already mentioned that Magento provides an option to encrypt the transferred data with the help of an SSL certificate. It raises another rebuttal 2.3 that what if the certificate that is being used is compromised. To address this, Magento provides an option to use the [custom certificates](https://www.mageplaza.com/kb/how-to-enable-ssl-in-magento-2.html). There is also an option to validate the certificate used with the help of the extensions. But here, another rebuttal R2.4 exists what if there is an SSL stripping attack on the websites. To prevent this, Magento has provided an option to enable the [HTTP Strict Transport Security](https://www.aspirationhosting.com/how-to-confgure-magento-part-3/). The same thing has been provided as evidence in the E2.2. 

### Evidence E2.3:

There is another rebuttal for the sub claim C2.1, that what if there is any man in the middle attack. To address this, Magento provides options to secure all of its [webpages](https://www.mageplaza.com/kb/how-to-enable-ssl-in-magento-2.html) like login, and administration URL's with the help of the SSL certificate, which is clearly stated in the Magento documentation, i.e., the evidence E.2.3 

### Evidence E2.4:

There is a chance for undermining case UM1 for the evidence E2.3. That what if the secure URLs that are not available to the users to access, to address that Magento effectively communicates with the search engine with the help of the [Search engine robots](https://docs.magento.com/user-guide/marketing/search-engine-robots.html), which is presented in the evidence E2.4. But there is another rebuttal case for the sub claim 2.1 that what if the developer's code consists of any insecure content like image or document URLs that are not secured under https. In this case, Padlock present to ensure the security of the users regarding the website will be disabled.  There is no proper mechanism in the Magento side to address this issue, but there is a chance to scan this issue in the third party sites like [whynopadlock](https://www.whynopadlock.com/)   


## Assurance Claim 3: Magento minimizes malicious code

It would be a challenging task for Magento to completely avoid the injection of malicious code into the system. Magento tries its best to reduce the risk of malicious code being introduced into 
the code. By following few of the best practices it tries to be resilient to risks introduced by malicious code injection. In our claim we begin our discussion with a rebuttal R1 that unless
Magento is injected with malicious code, the software is secure. Our Sub Claim C3.1 assures that Magento follows all the security policies and guidelines, that reduces the risk of Magento 
being injected with malicious code.

![Assurance claim - malicious code](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Assurance%20Case/Assurance%20claim%20-%20malicious%20code.jpeg)

### Evidence E3.1
Our Sub Claim C3.1 leads to rebuttal R2, what if the software is not up to date. We address this question with Sub Claim C3.2 where Magento ensures to notify its users with updates
on the latest patches. The Evidence E3.1 for this claim is the Magento Security Center, where it gathers all the information about the latest patches, security updates, notifications and best
security practices to be followed. [Magento](https://magento.com/security) publishes all the hotfixes on the Magento Security Center that contain high-impact security or quality fixes that affect many Magento merchants. It has introduced a Security Alert Registry which is a mailing list that receives updates every time there is a potential security vulnerability or Magento patch. Thus, ensuring all 
its users are informed about the latest security patches. 
 
### Evidence E3.2

We also have our Sub Claim C3.3 which addresses rebuttal R2, which states that Magento provides a scanner for identifying missing or infected patches. Evidence E3.2 provides the evidence for this
subclaim through a mage report. Magneto provides an option to scan our site on magereport.com to identify any missing security patches and to determine if it has been infected with known [malware strains](https://magento.com/security/best-practices/remediating-your-site-after-malware-attack)



 
### Evidence E3.3
Our Sub Claim C3.1 also leads to rebuttal R3, which argues that what if unnoticed malicious code has been introduced into the software. Sub Claim C3.4 addresses this rebuttal by stating that Magento performs scanning to detect if some malicious code has been introduced. Evidence E3.3 shows the evidence for this subclaim, where Magento provides its users a Security scan tool
 that enables Magento merchants to regularly monitor their sites and receive updates regarding known security risks, malware, and unauthorized access. Security Scan is a free service of
 Magento and can be run on any version of Magento Commerce and [Magento Open Source](https://magento.com/blog/magento-news/introducing-new-magento-security-scan-tool) 
 
 It scans result reports that show which checks the site has passed and failed and whether further action is required, provides details on the schedules of specific scans, and suggests 
 remediation steps for each failed security test.
 
 
### Evidence E3.4

 
UM1 undermines our evidence E3.3 questioning the frequency of the scans performed by Magento and what would happen if the scans are not performed regularly. Our Sub Claim C3.5 answers this question, stating that Magento provides regular security checks and also notifies its users about the same. The evidence for this is provided in the [Magento security documentation](https://www.adobe.com/content/dam/acom/en/security/pdfs/Adobe-Magento-Commerce-BestPractices-Guide.pdf)


The documentation clearly states that the Magento security scan service, allows us to monitor our magneto sites for known security risks and security notifications.
It provides an option to schedule security scans to run weekly, daily or on demand. It also maintains a history of security reports in the individual accounts.

### Evidence E3.5
Our Sub Claim C3.1 also leads to rebuttal R4, which argues about the consequences of Magento being attacked by Cross Site Scripting (XSS) attack. But Sub Claim C3.6 assures that rebuttal by 
stating that Magento provides an option to configure CSP (Content Security Policies) headers. The CSP are a powerful tool to mitigate XSS attacks and the other related attacks like card skimming,
session hijacking, clickjacking, and other malware related attacks. Evidence E3.5 provides evidence for this claim through a CSP report where Magento reports the policy violations which 
is useful for [debugging](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/security/content-security-policies.html) 
CSP's built-in browser prevents loading malicious script from an attacker's website and also from sending the credit card info to the attacker's website.

### Evidence E3.6
UM2 undermines our evidence E3.5 questioning the possibility of users needing some assistance to fix the violation identified by the CSP report. Thus the Sub Claim C3.7 assures that Magento 
provides the restrict mode option where it can help the users to resolve the violation. The evidence for this subclaim is provided in E3.6 in respect to Magento's restrict mode. In this mode, Magento acts on any policy violations.
Policies can be configured for admin html and storefront areas separately to accommodate different use cases. Magento also permits [configuring unique CSPs](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/security/content-security-policies.html) for specific pages.

 
### Evidence E3.7
We also have our Sub Claim C3.8 which addresses rebuttal R4, which argues that Magento provides OWASP ruleset for filtering cross site injection attacks which can minimize the risk of XSS attack. Evidence E3.7 provides the evidence for that subclaim with help of [Magento WAF report](https://support.magento.com/hc/en-us/articles/360016353452--Web-Application-Firewall-WAF-powered-by-Fastly-the-FAQ). The OWASP ruleset protects against cross-site injection attacks. It leverages a mechanism for each request looking for cross-site injection and other threats to the origin and scores every request against the entire core ruleset and validates that the request score.


## Assurance Claim 4: Magento minimizes leakage of sensitive data

For any eCommerce platform, online transactions and personal information are key things to be protected. This yields to crucial issues and reputation damage if not handled properly. Here we are trying to assure how well Magento secures its sensitive data. Magento security and privacy policies meet legal requirements and industry compliance for online merchants. These are mandated by Payment Card Industry (PCI) and law.

![AssuranceClaim-4-Dripping of sensitive data](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Assurance%20Case/AssuranceClaim-4-Dripping%20of%20sensitive%20data.jpeg)

### Evidence E4.1:

- The business that accepts payment by credit card over the internet should follow a set of requirements established by the Payment Card Industry (PCI). As merchants handle customer credit card information they should maintain a secure server environment by adhering to these guidelines. Adhering to PCI guidelines, Magento protects payment data by providing extensive security to payment transactions thereby avoiding easy access to payment details or preventing skimming of payment data. This is evident from [Magento PCI compliance documentation](https://magento.com/pci-compliance?_ga=2.179952685.867899796.1601778413-1356859247.1599591671) which shows the steps Magento implements to be PCI compliant.

### Evidence E4.2:

- Merchants have to comply with having a strong customer authentication requirement set by the Payment Service Directive (PSD2). To authenticate the payment transactions, Magento facilitates strong customer authentication such as utilizing password/PIN, security token, biometric, etc. Magento uses a secure payment gateway which is complied with PSD2 to ensure payment security. Its online transactions are highly secured as it uses Braintree and Paypal payment modules. Hence Magento is trustworthy as almost all eCommerce websites use these payment modules for online transactions. [Magento payment services documentation](https://docs.magento.com/user-guide/stores/compliance-payment-services-directive.html) elaborates on payment module.

### Evidence E4.3:

- Magento follows California Consumer Privacy Act (CCPA) and General Data Protection Regulation (GDPA) guidelines to protect sensitive data. Exploiting user’s personal information as in name, phone number, address is against the law. If the software does not handle privacy policies properly then users lose trust in the system. [Magento privacy policy documentation](https://docs.magento.com/user-guide/stores/compliance-ccpa.html) talks more regarding CCPA and GDPA compliance.

### Evidence E4.4:

- Magento avoids unauthorized access and protects its site being error prone. It provides proper security with a strong login mechanism for Admin users to ensure all high level and storefront data are safe, as further explained in [Top-Claim C5](https://github.com/pradeepkoneti/Softwareassurance/issues/52).

Thus, with all the above-mentioned evidences Magento adheres to protect payment and sensitive data.



## Assurance Claim 5: Magento Software minimizes unauthorized login access

![login Assurance case](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Assurance%20Case/_login%20Assurance%20case.jpeg)

### Evidence E5.1
Our Top claim assures that Magento Software minimizes unauthorized login access that restricts the unauthorized access to the system but with a doubt of if the user password is weak, we address the same with the Sub Claim C5.1 that Magento forces users to set for Complex passwords which are provided by the Evidence E5.1 where the [requirements for password](https://docs.magento.com/user-guide/customers/password-options.html) includes the uppercase and lower case characters, numbers and special characters with minimum eight characters length.

### Evidence E5.2
For the Top claim, Magento Software minimizes unauthorized login access the doubt comes like what if the attacker performs a brute force attack then our Sub Claim C5.2 makes sure that all the activities are alerted to Magento admin. But still, if the admin credentials are compromised then the Sub Claim C5.5 assures that Magento facilitates a strong admin login mechanism which is explicitly provided in the Evidence E5.2 [Admin login](https://docs.magento.com/user-guide/stores/security-admin.html) features from Magento like accepting the login mechanism by specific IP Address and by specific email address etc.

### Evidence E5.3
Here we come with doubt like what if the username and password are phished based on our top claim Magento Software minimizes unauthorized login access but that can be supported by Sub Claim C5.3 which is Magento two way authentication but that raises for another doubt like what if one of the two-way authentications is compromised. For the doubt raised, Sub Claim C5.6 answers that Magento facilitates multiple 2-way authentication mechanisms which are provided in the Evidence E5.3 which provides [four ways](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) of 2-way authentication like Google, Duo Security, Auth, and U2F.

### Evidence E5.4
For the top claim, Magento Software minimizes unauthorized access here raises the doubt like what if the access from third-party applications are insecure to support that doubt the Sub Claim C5.4 states that Magento OAuth protocol allows a system to control which third-party applications have access to internal data without revealing or storing any user IDs or passwords. Here raises another doubt that what if Magento OAuth protocol is bypassed. To support that Sub Claim C5.7 states that OAuth uses a token mechanism which is provided by the Evidence E5.4 request token and access token [procedure](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-oauth.html) from Magento.

## Reflection: 


[Project Dashboard](https://github.com/pradeepkoneti/Softwareassurance/projects/4)

[Team Meetings - MOM](https://github.com/pradeepkoneti/Softwareassurance/blob/master/MOM.md)








