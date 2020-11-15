## Top-Claim 2: Magento minimizes data hijacking

The data that is being managed in the eCommerce websites is very crucial and critical. Because a loss of that data can result in serious ill fame to the entire organization, many hackers will be trying to get that data because it involves mostly personal details or financial information. In this assurance claim, we are trying to present the assurance strategies of the Magento to reduce the risk of the data hijacking from the websites that are using the open-source software. One a whole, we can say that data that is being managed on the websites will be encrypted or appropriately secured.  

### Evidence E2.1:

The top Claim C2 leads to a rebuttal R 2.1 that what if the Magento is transferring the data in plain text format. We address this issue with sub claim 2.1, stating that Magento provides an option to encrypt the data transfer between the system and the users with the [SSL certificates' help](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#fastly-tls). Then another rebuttal R2.2 arises that what if there is a scenario that SSL certificate used was expired. Then we can address this issue with the claim that there will be validation regarding the certificates and the remainders, which can be seen in the Magento Documentation. This brings us to the Evidence 2.1. Magento [provides notifications](https://www.magecloud.net/marketplace/extension/ssl-certificate-reminder-and-validator/) on the SSL certificates with extensions' help; it can even validate the certificate. 

### Evidence E2.2:

In the previous sub claim, it is already mentioned that Magento provides an option to encrypt the transferred data with the help of an SSL certificate. It raises another rebuttal 2.3 that what if the certificate that is being used is compromised. To address this, Magento provides an option to use the [custom certificates](https://www.mageplaza.com/kb/how-to-enable-ssl-in-magento-2.html). There is also an option to validate the certificate used with the help of the extensions. But here, another rebuttal R2.4 exists what if there is an SSL stripping attack on the websites. To prevent this, Magento has provided an option to enable the [HTTP Strict Transport Security](https://www.aspirationhosting.com/how-to-confgure-magento-part-3/). The same thing has been provided as evidence in the E2.2. 

### Evidence E2.3:

There is another rebuttal for the sub claim C2.1, that what if there is any man in the middle attack. To address this, Magento provides options to secure all of its [webpages](https://www.mageplaza.com/kb/how-to-enable-ssl-in-magento-2.html) like login, and administration URL's with the help of the SSL certificate, which is clearly stated in the Magento documentation, i.e., the evidence E.2.3 

### Evidence E2.4:

There is a chance for undermining case UM1 for the evidence E2.3. That what if the secure URLs that are not available to the users to access, to address that Magento effectively communicates with the search engine with the help of the [Search engine robots](https://docs.magento.com/user-guide/marketing/search-engine-robots.html), which is presented in the evidence E2.4. But there is another rebuttal case for the sub claim 2.1 that what if the developer's code consists of any insecure content like image or document URLs that are not secured under https. In this case, Padlock present to ensure the security of the users regarding the website will be disabled.  There is no proper mechanism in the Magento side to address this issue, but there is a chance to scan this issue in the third party sites like [whynopadlock](https://www.whynopadlock.com/)   

