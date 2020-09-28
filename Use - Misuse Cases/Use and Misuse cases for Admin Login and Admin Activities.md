 1. #### Admin Login and access prevention
One of the most resourceful areas in Magento is the Admin Panel, as it has high privileged access to the site. Magento super admin will have full administrator privileges to manage all the functionalities, which includes having full permissions, access to all features and options. Admin uses the UI panel to modify/configure the Magento system and storefront parameters.  
 - A Trespasser wants to access the Magento Admin panel to defame it. He has no permission, so he will try to guess the System Admin’s password using Brute force attack. Authorized login and 2-factor authentication at site prevents this attack. As a safety net and extra precaution, there could be a minimum time set for, recovery link expiration; time between each password reset requests and for Admin session lifetime. Additionally, enabling the Account Lockout time feature enables us to lock out the admin account after the maximum number of attempts is met, and also we can set the maximum number of times a user can try to login before the account gets locked, which further mitigates such attacks. To prevent password guessing, Magento Admin uses whitelisting of IP addresses and enabling non-default admin URL (through command line and env.php files) techniques. This avoids password capturing.
 
	 A Trespasser wants to access some restricted resources on the site. Any unauthorized access to restricted resources can also be avoided by setting proper user roles and specific resource access.
	 
 - Trespassing also involves destroying the file system. File system security is complex and extremely important. Trespasser wants to sneak into the Magento file system to access and destroy the files. However, System Admin prevents this action by setting proper ownership and access permission on every file, based on usage. To facilitate this, Magento uses umask (file system creation mask) to further restrict the access, this provides special security on a shared hosting production system. 


 1. #### Admin Activities
Magento Admin’s activities involve handling orders, preparing catalog, arrangement of shipments, CMS, design of storefront, organizing customer information, and managing configurations. It is not handled by a single person but consists of a set of admin groups with Super Admin and Division Admin privileges for separate divisions. Customer maintenance, Catalog/Inventory management, and Magento Order Management (MOM) also known as Order Management System (OMS) are all controlled by respective admins from individual departments.

- A Gangster wants to ruin the Magento site by inserting a virus which includes content spoofing or to insert malicious content through email or infected software. Admin can keep the Magento storefront site clean from known security risks by conducting frequent security scans on a daily/weekly or on-demand basis. This includes patch updates, security notifications, and virus protection updates. Magento also provides security reviews to check for signs of an attack and the latest potential vulnerabilities. They also ensure best practices through the security registry alert and security center. Magento malware and vulnerability monitor inspects for any security issues with files, databases, and admin accounts. With all these in place, Magento Admin’s can avoid Gangsters inserting malicious viruses or content into their sites.

- A Gangster wants to delete store data entirely/partially.  Whereas Magento Admin holds a backup of their complete repository taken regularly and with proper Disaster Recovery along with a well-versed Business Continuity Plan in place, Magento can continue with an uninterrupted business performance. In an E-commerce website even if something goes wrong businesses should continue to serve their customers otherwise it creates reputation problems and unexpected losses. To handle this, proper data backup is mandatory. Any data loss caused by unexpected parties can be reversed to its original state.

- A Gangster wants to send some hijacking content to the store site. To do so he keeps checking to identify any possible loopholes. Magento Admin configuration enables Admin’s to capture any action from a user at their site in Action Logs. All these Trespasser’s activities will get captured in the Action Log. Admin can validate any suspicious activity by inspecting the activity logs and protect storefront sites from any interference. Also, the firewall and Session validation feature at the system admin configuration protects against any session fixation attacks or attempts to poison or hijacking site sessions. Validating and sanitizing user inputs/dynamic values can help prevent XSS vulnerabilities. Additionally, it has XSS prevention at site which involves Content Security Policies that help to mitigate against Cross-Site Scripting attacks, card skimmers, session hijacking, clickjacking, etc. 
	
	Action log records every change that was made to the store. This log feature captures Name, object ID, action-outcome, date, and IP address. Admin’s can use these captured logs for further evaluation.


#### Alignment of Security requirements with advertised features:

##### Admin login and access prevention
- Magento Admin platform has the proper authentication functionality to login and maintain the application. It uses encrypted password and 2-factor authentication techniques while login. Super admin can have the complete access and set roles to different users. Magento admin uses umask file permission to restrict file access. This way of restricting access will give enhanced security to resources.
[Admin Login](https://docs.magento.com/user-guide/stores/security-admin.html)
[Access Permission](https://docs.magento.com/user-guide/system/permissions.html)
[File Permission](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html#restrict)
[User Roles](https://docs.magento.com/user-guide/system/permissions-user-roles.html)

##### Admin Activities
-   Magento Admin activities involves securing and managing the site data. XSS prevention and CSP enables cross-site scripting attacks. Regular patch updates, monitoring the scanning tools help to keep the site safe. Admin can also conduct regular security scans to keep the storefront site free from known risks. A proper data backup and business continuity plan can avoid any data loss. Also, it helps to continue the business without any disruptions.

	[CSP](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/security/content-security-policies.html)
[Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html)
[XSS Prevention](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/xss-protection.html)