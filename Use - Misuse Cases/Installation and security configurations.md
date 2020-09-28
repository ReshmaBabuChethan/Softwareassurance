**Installation and security related configuration in Magento**

All e-commerce sites are the main targets of the hackers as they are involved in the payment system to complete the order. They have provided the clear documentation part of installation, such as: operating systems supported by Magento, the system requirements needed, what version of the system supports Magento and others [1]. Magento provides clear instructions on installation using the compressed files, composer and through the code[2], however the installation of Magento can have a few problems. For intance, while using composer or using command line instructions problems can be encounterd with the PHP-extensions,as we can see in xdebug [3], where the problems with PHP dependencies installation cause common errors during the installation of Magento, since different Magento versions requires specific PHP dependencies. Other problems that can occur are related with different versions of PHP, as all versions of PHP are not supported for Magento installation. Magento documentation acknowledge the supports of the PHP versions 7.0 and above excluding the 7.2 version, as it has problems with browser cookies and message rendering in the application.Before Magento 2.4.0 merchants need to install and configure the official Braintree payment integration extension from the Magento Marketplace from Magento 2.4.0, the extension is included in the Magento release.

Coming to the security, the major security issues of the Magento are cross-site scripting attacks, remote code execution attacks, and recent attacks like the Magecart attack, where Magento killer has occurred in recent years which is considered Majento major security breaches till date [4]. Coming to the security,  The security-related practices documentation is provided for the Magento project is very good which covers all parts of the application security [5] like configuring, and installing the SSL certificate can be easily done and renewed which adds security to all the store admins, admins, and users of Magento [6]. 

- SSL/TLS settings are configured to include supported protocols, controlling the server&#39;s behavior with respect to requesting a certificate from client connections. Also, the verification that the certificates have been signed by a trusted authority. Configurations can be made inside the Magento system to contain the private key and certificates to be trusted.
- Magento uses an encryption key to protect passwords and other sensitive data.AES-256 algorithm is used to encrypt all data that requires decryption. Besides, a strong Secure Hash Algorithm (SHA-256) is used to hash all data that does not require decryption.
- Admin login activities in Magento are secured by the making admins creating strong passwords, two-factor authentications with one-time passcode and another feature CAPTCHA can also be configured.
- Magento system can validate the session variables as a protective measure against possible session fixation attacks or hijack user sessions.
- Magento requires that the visitor&#39;s browser allow both cookies and JavaScript for full operations. To do that the user&#39;s browser is set to the highest privacy setting that prevents both cookies and JavaScript. Magento systems can be configured to test the capabilities of each visitor&#39;s browser and display a notice to the user of Magento if the settings need to be changed.
- All types of users in the Magento system are assigned roles to limit the access of the user to specific things.
- The easy way to protect the environment is to keep all software on the server up to date and apply security patches as recommended by Magento and Magento uses only secure communications protocol (SSH/SFTP/HTTPS) to manage files inside the system.


[1] [https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements-tech.html](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements-tech.html)

[2] https://devdocs.magento.com/guides/v2.4/install-gde

[3] [https://support.magento.com/hc/en-us/articles/360034242212](https://support.magento.com/hc/en-us/articles/360034242212)

[4] [https://en.wikipedia.org/wiki/Magento#Security\_concerns](https://en.wikipedia.org/wiki/Magento#Security_concerns)

[5] [https://docs.magento.com/user-guide/magento/magento-security-best-practices.html](https://docs.magento.com/user-guide/magento/magento-security-best-practices.html)

[6] [https://magenticians.com/how-to-install-enable-magento-ssl/](https://magenticians.com/how-to-install-enable-magento-ssl/)
