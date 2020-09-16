# Project Proposal
## Team Members:

- Shashank Tankasala
- Lucas Asato
- Bhavana Gopisetty
- Reshma Babu Chethan
- Sai Pradeep Koneti

**Name of the Software:** We have selected [Magento](https://github.com/magento/magento2) as our open-source software.

**Hypothetical operational environment:** The environment that we are considering to analyze the threats is Home,  but it can also be used in enterprise and office environment. 

## System Engineering View:

![System Engineering View](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Attachments/System%20Engineering%20View.jpeg)

## Threats in the operational environment

1. Personal Information Hijack
2. Payments issues
3. Phishing emails
4. Hacked Redirect
5. Encryption of Secret data
6. Proper authorization and validation to access data
7. Secure Data Maintenance

## List of security features in the software

### Magento has below built-in Security Measures

1. **Enhanced password management:**
Currently, Magento has its strategy for password hashing. It supports multiple algorithms like MD5, SHA256, or Argon 2ID13. Magento supports strong hashing algorithms like MD5 and SHA-256 in password management. Now it also supports Argon2ID13 through the PHP sodium extension (requires libsodium library version 1.0.13/higher).
2. **XSS prevention strategies**
Has improved the prevention of cross-site scripting (XSS) attacks by making escaped data the default. Vulnerabilities can be prevented from XSS by authenticating and cleansing user input as well as sanitizing dynamic values when rendering the HTML view.
Magento's framework has adopted conventions that regulate the escaping of data in output. These include the ability to escape output for HTML pages such as HTML, JSON, Javascript, and via email.
3. **More flexible file system ownership and permission**
It has revised some file permission from the 2.0.6 version onwards. It no longer explicitly sets file system permission. Flexibility to restrict further permissions is provided through the use of umask.
4. **Improved prevention of clickjacking exploits**
Using an X-Frame-Options HTTP request header, Magento safeguards its merchant's store from clickjacking attacks.
5. **Use of non-default Magento Admin URL**
Uses random Admin URI along with installation, to avoid attacks on simple Admin URL as it’s easy for automated password guessing
6. **Secure cron to prevent malicious attacks**
HTTP basic authentication and encrypted password file for nginx, to provide authentication.
7. **Google reCaptcha**
The use of Google reCaptcha provides a greater level OS security for both at storefront and Admin UI. Thereby enhancing the Admin users login security, verification of customers new accounts, and password retrievals.
8. **Prevent cache poisoning:**
With the Enable_IIS_rewrites settings, Magento provides the option to remove preceding header values on the respective server, by this means avoids HTTP 404 error page injection and denial-of-service(DoS) through the IIS server.
9. **Two-Factor Authentication**
Magento provides 2FA to improve security by enabling 2-step authentication to access Admin UI from on all types of devices. This extension supports multiple authenticators like Google Authenticator, Authy, Duo, and U2F keys, to name a few.
10. **Magento provides a best practice guidelines**
To make its customers cautious about possible vulnerabilities such as Site defacing, Botnets, Direct server attacks, and Silent card capture, Magento has few [best practice guidelines](https://www.adobe.com/trust/security.html).  



## Project motivation

The software magento2 is used for creation of ecommerce website which gives the marketers control over their content and layout without having to involve front-end developers. However, at the same time, having the security provided by the software, which enables small business to create their own page and grow. The software features are in high need due to the high global ecommerce growth. Indeed, the ([estimated growth](https://www.oberlo.com/statistics/global-ecommerce-sales-growth))  between 2017 to 2023 is of 175% and currently has an estimated market size of $4.1 trillion (emarket).

However, ecommerce has multiple threats, such as credit card fraud, personal information leakage, phishing attacks, distributed denial of service attacks and others which can damage the seller&#39;s reputation. Mostly of these threats can be managed by security coding and by conducting software assurance analysis. Magento2 has an active community with clear documentation, explicit coding guidelines and with a history of multiple reported errors, which some of them could create the previous commented threats, but with fast response. The group personal motivation is to possibly be able to impact a big community, with more than 100,000 merchants worldwide, and the community by improving the software and its security.

![Project Motivation](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Attachments/Motivation.png)

## Open Source Software description

Magento is a leading platform for open e-commerce innovation.More than a 1,000 Magento stores come online every day,these merchants depend heavily on the ecosystem of third-party developers, to build Magento implementations, customizations, and extensions.It is a part of Adobe Experience cloud, which brings together all the marketing technology to a single place.Thus providing a seamless experience by integrating digital and physical shopping experiences.

It has upto 100000+ merchants worldwide. It is ideal for fast growing small business as it is customizable and agile.With affordable Cloud hosting reducing the cost of total ownership by eliminating the maintenance and monitoring costs.Magento accepts contributions in the form of new features, changes to the existing features, tests, documentation,bug fixes or optimizations.Magento values the contributions of the security research community,they strongly encourage developers to report all security issues privately via their bug bounty program to minimize risk to Magento merchants.

It has close to 1400 contributors. Nearly 7500 customers have migrated to Magento from Open Cart and Virtuemart last year. Its top users include Liverpool FC ,Pepe jeans, Land Rover, Harvey Nichols,Ford, Bulgari and many others.

The major languages used in Magento include PHP(82 %), HTML(9%) and Javascript (5.6%).

Magento maintains a clear documentation providing a developer every detail that he needs to build and manage a customized Magento store.

The documentation for Magento can be found [here](https://devdocs.magento.com/),it includes documents related to setup,backend development,frontend development, Magento API and its community.

### Activity in Magento

![Magento Activity](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Attachments/Activity.png)

### License Summary and Contributor Agreement

Magento is an open source eCommerce project facilitating the improvement of Magento Core products. They encourage developers to add more functionality to merchants giving them a seamless experience which can help them to grow as platform. The motivation for any developer to contribute to Magento is to boost their skills in the most widely used e commerce platform, and to share and gain knowledge from their experiences.

Magento accepts contributions in the form of new features, changes to the existing features, tests, documentation, bug fixes or optimizations. They have a contribution guide which clearly gives the instructions when a developer wants to contribute, the templates to be followed, the code quality to be maintained , and commit requirements. The clear documentation on all these activities helps Magento maintain uniformity. They use the fork and pull model to contribute to the Magento code base. This helps the contributors to have their own copy of the original code which can be later synced with the master copy. The forked repo can be later used to submit a pull request to the base repo to merge a set of changes from the fork into the main repository. They have a Community Engineering Team that reviews all issues and submissions by the developers and clarify from them if they have any issue regarding the contribution. The developer is given 14 days to respond to give the clarification else they close the issue. The team will add a label to an issue while working on it to indicate some information about the issue like the status and who is working on it and so on.

The Magento team has a few requirements that a developer has to adhere to while contributing. A few include:

- The contributors must adhere to the coding standards
- The commits must be accompanied by meaningful commit messages
- To report a bug they must open an issue and follow the reporting guidelines
- They must verify that all the automated tests run properly on their pull requests.

They have a contribution agreement that every contributor has to go through and sign. Here is a summary of their contribution agreement summary taken from Github

&quot;_By making a contribution, you agree to the terms of the Magento Contributor License Agreement, which includes your grant to Magento of a royalty-free, perpetual and irrevocable license to use and relicense your contribution, and any copyrights and patent rights in your contribution You may only contribute software and materials originally created by you or your company and you must have the right to make the contribute on behalf of yourself and/or your company_.&quot;

License Agreement: The Magento team has an Open Software License (&quot;OSL&quot;) v. 3.0, the complete license information can be found [here](https://github.com/magento/magento2/blob/2.4-develop/LICENSE.txt) 

All code committed to Magento repositories will be licensed under the OSL 3.0 or the Magento Enterprise Edition (MEE) license.

## Software Security History

The software project uses cvedetils to report security isssues. As of today, there are 84 security reports that have been posted and out of which 73 are [resolved](https://www.cvedetails.com/vendor/15393/Magento.html) .

In the earlier versions of Magento commercial and Enterprise applications, there was a bug identified by the team which is Authentication Bypass vulnerability which is due to improper authentication of incoming request handling where Remote attackers can gain control of the [system](https://www.cvedetails.com/vulnerability-list/vendor_id-15393/year-2019/opginf-1/Magento.html). The above bug has taken resolved after five months with a new patch where the Authentication Bypass is handled. Crading attack is one of the major issue in the recent times which means thousands of credit card which are stolen is tested during the [payment](https://github.com/magento/magento2/issues/28614).

The vulnerabilities like Insufficient server-side validation of user input, security bypass by authenticated user, A cross-site scripting mitigation bypass, and An access control bypass vulnerability are raised in the release versions of 2.1,2.2 and 2.3 and those are resolved in the hotfixes later which exposed the data of the authenticated users. The current issues are order details are captured in the payment gateway, but it is not saved in the database when the table which stores the information exceeds 2GB of memory. few third-party payment integrations created security issues while the payment is processing as the third-party payments are not secured properly. The developers have identified the issues with such third-party payment integration payments, and they have removed such third-party payments in the latest releases. Coming to the security issues like SQL Injections, this is a common vulnerability from the previous versions to the latest versions which are disclosing the sensitive information to the attacker and Modification of some system files or information is possible but the attacker does not know what files he is [modifying it](https://www.cvedetails.com/vulnerability-list/vendor\_id-15393/opsqli-1/Magento.html). When it is fixed in previous releases then in the upcoming releases the same bug is found on different files in the code.

The other type of security threat is HTTP Response Header Injection which is used to perform other attacks such as user redirection to a [malicious website](https://www.cvedetails.com/vulnerability-list/year-2018/ophttprs-1/http-response-splitting.html). Local File Inclusion is another vulnerability that can result in Sensitive information disclosure and remote [code execution](https://www.cvedetails.com/vulnerability-list/year-2018/ophttprs-1/http-response-splitting.html). The above are major security issues found in the earlier versions and latest versions out of which few issues are fixed, and few issues are yet to fix. PHP Object Injection and Stored cross-site scripting are major issues with high priority have been resolved in the latest versions.

Default configuration of the software might create security weaknesses under certain threat environments if it is left without changing. The security practices can be found [here](https://amasty.com/blog/magento-2-security-features-101/).

## Reflection

[Project Dashboard Link](https://github.com/pradeepkoneti/Softwareassurance/projects/1)

As everyone in the team is new to the open-source Projects, initially, we thought of learning about open source projects and how different IT industries will use them. But guest lecture from Dr. Germonprez helped us a lot to form that idea about the open-source projects and their management. Once everybody got an idea, we segregated the task and searched for an open-source project that would fit the criteria. In the consecutive meetings, everybody in the team presented their open source project, and then we took a confidence vote to select the project. Once the project is finalized, we have gone through the project documentation available in their GitHub and Wiki pages and segregated the tasks for the project proposal.

### Challenges Faced

As all the meetings are completely remote and everybody is doing a full course load. Initially, we found it hard to finalize a spot for team meetings and discussion sessions for project selection and proposal work. But we have streamlined it using the shared calendar and picked up perfect timings for the team meetings and discussion sessions. In the future, we will follow the same approach throughout the project for easy scheduling of the sessions.

The selection of the open-source project and defining the specific scope in that project for security engineering was challenging, as all of us are from different technical backgrounds. So rather than going for an open-source project in a specific language, we thought coming with unique software selection would be the right approach as it will give different perspectives. That assignment helped us to go through the open-source projects profoundly and choose the suitable one. After the team&#39;s presentation, we have voted for the one we like and finalized the project. This way, it gave us some exposure to the open-source projects; we will follow the same approach for all the tasks in the future.

Though all of us have some kind of work experience in the IT industry , none of us in our team had a good knowledge on the Systems Engineering view.
This was challenging as well as good learning experience for all of us. It was challenging for us to narrow down the scope of our project as Magento the project we chose was wide e-commerce platform
and narrowing the scope in the best interest of security bugs was tough. We all together spent time together to understand the Systems Engineering View and then came up with our diagram.
This was a good experience for us.