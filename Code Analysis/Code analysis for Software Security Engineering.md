# Code Review

## Code Review Strategy

The Magento code is mostly written in PHP. There are many components in the systems like the payments, UI and the integration modules, etc. As this open-source software is available for a long time, many third party plugins can be installed and integrated with the software. The plugins typically use the API calls but are not included in the source code. There is a clear developer guide that will give instruction to all the contributors.

As the project codebase is huge, full manual review is not a feasible solution to completely review it. To complete the code review, we have decided to incorporate both the code review approaches, automated and manual, to perform the analysis. To execute both the approaches in parallel, some of the team members who got familiar with the automated code analysis tools will go ahead with the Magento code's installation and analysis with the automated code review tools. The rest of the team will go through the Magento issues and select a list of the CWE relevant to the existing cases. For selecting the CWE’s, we have even gone through a Scenario-based strategy that analyzes our previous Misuse and Assurance cases to match the possible attacks that can happen in the Magento system. By the end of the analysis of the issues, misuse cases, we ended up selecting 11 CWE that will be analyzed in the Magento code.

While coming to the automated code review, we researched the automated code review tools that will be the best fit for the Magento system as most of it is written in the Php. Most of the automated code analysis tools are only having commercial packages, which makes them out of our reach. But the automated code analysis tool that looked a perfect fit for our analysis was SonarQube. A community edition can be installed in our local machines and provides different features like issue review, security hotspots, etc. We haven’t solely relied on the SonarQube, we even tried to run the analysis on the SonarCloud, which is an online version of the SonarQube. Still, unfortunately, due to the Magento code's size, it is not possible to run the analysis in the SonarCloud. Then we explored other tools that are good at analyzing the Php code and ended up with the Codacy. The Codacy is a publicly available, online tool which can be used for static code analysis. So, both SonarQube and Codacy are mainly used to identify potential security concerns in the existing Magento codebase. On the whole, we have used both the automated and manual code review process to find the potential security issues based on the attacks that we have outlined in our misuse cases, assurance cases, and threat models.

### Challenges

- Expertise in PHP Language:

Magento code is mostly developed using PHP language, but unfortunately, no one in our team got any experience with the PHP language. This is a major challenge in the manual code review because we need to go through the code and find out any present issues. To overcome those, we have gone through online blogs and tutorials to find out the security issues related to the codes developed in PHP and mostly relied on the Magento open-source software's ongoing issues. 

- Huge Code base: 

As e-commerce, Magento already got a considerable code base, and it is not possible to scan the complete code in some of the automated code analysis tools. To overcome this, we have only concentrated on the misuse and assurance cases that we have generated previously and analyzed the code related to those modules.   

## Findings from manual code review

We have analyzed our misuse and assurance cases, and since Magento is an e-commerce platform. We tried to identify the most vulnerable scenarios and linked the related CWE's to them. Below are the categories for the vulnerabilities.

#### Login Authentication

We selected some of the majors CWE’s related to the login authentication, for manual code review using previous misuse cases done earlier on the semester. In this analysis we will be focusing on finding code faults related with credential appropriation using brute force attacks, dictionary attacks or by insufficiently protected credentials.

As par of this, we selected a few login authentication related CWE’s, CWE-798, CWE-307 and CWE-259. We analyzed mostly of the user and a few admin login related codes for the previous mentioned login attacks. We started by checking the weakness mentioned in CWE-798 and CWE-259 at the same time, since CWE-259 is a child of CWE-798. From this two CWE’s we understand that the threats have two main variation, inbound and outbound, but due to time constrains and the group language ineptitude we were only able to check for the first variation, leaving this analysis incomplete. Latter on, the team checked weakness mention in CWE-307, by checking if the system restricts the number of authentication attempts.

During our manual code analysis on login authentication, we did not notice any hard-code credentials, on the inbound variation, nor we founded errors	 with the restrictions of excessive authentication attempts. The analysis was based on the weak code suggested from the corresponding CWE.

#### Activity Log

We selected some of the major CWE’s related to logs, for manual code review from earlier misuse and assurance cases we understood that the Magento has a log capturing mechanism. Magento admin monitors and validates the logs for any unusual activities. So, we wanted to check for any weakness in the logs related source code. Configuring loggers is security-sensitive, logs are useful to track after any security incident. Capturing, maintaining proper logs is essential and it should have enough information to lead on the root cause of the damage. Codes related to logs capturing can also become targets for attackers as these may contain sensitive information. Hence configuration of what type of information and how they are logged becomes crucial. 

As part of this, we shortlisted some of the logs related to CWE’s. We analyzed a few of the logs related codes to validate for any log injection attacks. We understood from the CWE- 532 that the log capturing can also become a weak point if sensitive information is exposed to the attacker.  We also checked for any weaknesses mentioned in CWE-117 and CWE-778, checked for related weaknesses in some of the logs related source code such as ConsoleLogger.php, SampleDataDeployCommand.php, Mysql.php, and LoggerProxy.php.

![Manual](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture13.png)

![Manual](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture14.png)

We tried to check for any hard-coded values and how logs/errors are getting reported. Magento uses Psr\Log\LoggerInterface to capture and write logs. We didn’t observe any full path, data type conversion, or any username passwords, location information in easily decodable format in the source codes. We tried to look for those weak code suggestions from CWE and traversed the codebase; could not find any. As mentioned, since the Magento codebase is huge and our team has no hands-on experience on PHP, we were able to do only limited surf for manual code analysis.


#### Weak Encryption

For evaluating the risk to sensitive information through using insufficiently random values we have chosen the CWE 330. Magneto being an ecommerce platform includes a lot of sensitive information during transactions. This is possible when the code generates random values  and improper cryptography methods are used the hacker can easily identify the patterns and hijack that session of the user to gain access to sensitive information. Thus we started exploring the session id generation part of the code. After analysing the code, we have analyzed that Magento adheres to the standards and does not use any random generator that is vulnerable to attacks, rather it uses good encryption standards to ensure that the hacker cannot easily identify patterns and hijack any session, and also since the data is encrypted it is [more secure](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Session/SessionManager.php#L423) 

![Manual](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture12.png)

#### Denial of Service

During our Manual code review, we have gone through the Magento modules that will take the input parameters from the users like the credit card details during the payment phase or other user details which is the case in the CWE 624, 95 . Mainly the payment details validation blocks are present in java script modules which will validate the given card details for expiry etc. The developers are using regular expressions for validation, but the main thing is that they have kept a limit for the input strings that can be entered. In our opinion this can avert the attacks like the Denial of service as the limit of the characters strictly check the input string before comparing it with the regular expression. Even we have not found any traces for the issues like the code injection in these modules for the input validators.

![Manual](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture15.png)

#### Cross Site Scripting

We have found that cross-site scripting is one of the major attacks to the magneto system from the previous assignment use case and misuse cases. In most of the use case and misuse case scenarios for the Magento system, cross-site scripting is a major thing that attackers prone to attack the Magento system. We found that the CWE are related to this attack and we got to know the CWE-79 and CWE-1004 that are related to this attack. When I try to search for the code related to these CWE in the code. As the code base is too large we found that there are few files related to this common weakness enumeration.

```javascript
public function setCookieSecure($cookieSecure)
{
$this>setOption('session.cookie_secure',(bool)$cookieSecure);
return $this;
}
```

## Findings from automated code scanning

#### SonarQube
Using SonarQube we started Magento code analysis at first. The tool uses a sonar scanner to scan for code issues. The tool was able to find 4.5K bugs and 933 security issues. 
![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture1.png)

![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture2.png)

It has notified along with the severity of issues such as blocker, critical and major issues. The breakdown of security hotspot issues includes the following:
##### High:
-	 Authentication = 50
-	 Command Injection = 1
-	 Cross-Site Scripting (XSS) = 1043

##### Medium:
-	Denial of Service (DoS) = 525
-	Code Injection = 31
-	Weak Cryptography = 234

##### Low:

-	Insecure Configuration = 28
-	Log Injection = 6

![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture3.png)

We first began to analyze these security hotspot issues and documented based on category.

#### Issue Analysis:

##### Authentication:
Multiple issues were reported for password authentication, most of the issues look similar, for example, variable name used for password with which it’s easy to identify which is related to password. Tool suggests that credentials should not be hard-coded because it’s easily accessible from application source code or binary. We can find similar suggestions as weaknesses in CWE-798 Use of Hard-coded Credentials and CWE-259 Use of Hard-coded Password. We can find related attack patterns in CAPEC-191 and CAPEC-70.
This type of issues has caused the following vulnerabilities:
•	   CVE-2019-13466
•	   CVE-2018-15389

Tool suggests storing the credentials outside of the code in a configuration file, database, or secret management service.

![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture4.png)
![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture5.png)


Tool also suggests for sensitive code examples:

```javascript
$password = "65DBGgwe4uazdWQA"; // Sensitive
$httpUrl = "https://example.domain?user=user&password=65DBGgwe4uazdWQA" // Sensitive
$sshUrl = "ssh://user:65DBGgwe4uazdWQA@example.domain" // Sensitive

```

We can also check for suggestions from the tool on how to remediate this type of sensitive code.

```javascript

$user = getUser();
$password = getPassword(); // Compliant

$httpUrl = "https://example.domain?user=$user&password=$password" // Compliant
$sshUrl = "ssh://$user:$password@example.domain" // Compliant
```

##### Command Injection :
Tool reported some of the issues that could lead to Command Injection as noted below. The suggestions were similar to the Authentication issue. Here also we could see the variable name used for password with which it’s easy to identify that it’s related to password. Tool suggests that credentials should not be hard-coded because it’s easily accessible from application source code or binary. We can find similar suggestions as weaknesses in CWE-798 Use of Hard-coded Credentials and CWE-259 Use of Hard-coded Password.

![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture6.png)

##### Denial of service :
Tool suggests that using regular expressions is security-sensitive. Evaluating regular expressions against input strings is potentially an extremely CPU-intensive task. Specially crafted regular expressions such as (a+)+s will take several seconds to evaluate the input string aaaaaaaaaabs. The problem is that with every additional character added to the input, the time required to evaluate the regex doubles. Evaluating such regular expressions opens the door to Regular expression Denial of Service (ReDoS) attacks. In the context of a web application, attackers can force the webserver to spend all of its resources evaluating regular expressions thereby making the service inaccessible to genuine users. We can find this type of weakness reported in CWE-624 - Executable Regular Expression Error. However, the equivalent regular expression, a+s (without grouping) is efficiently evaluated in milliseconds and scales linearly with the input size. 
This type of issues has caused the following vulnerabilities:
•	CVE-2017-16021
•	CVE-2018-13863

![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture7.png)

![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture8.png)

##### Weak Cryptography :
The tool suggests that an attacker may be able to hijack another user's session If a session ID can be guessed (not generated with a secure pseudo-random generator, or with insufficient length). If a session id is not unique, set from a user-controlled input, or length is too short then there is a risk and can yield to weakness CWE-330 - Use of Insufficiently Random Values.

![SonarQube](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture9.png)

We could see some of the vulnerabilities reported [here](https://www.cvedetails.com/vendor/15393/Magento.html)

#### Codacy: 

In order to find the bugs and issues of the magento software we have tried another tool named codacy which is a standard tool to analyze the static code and which is also one of the available too for PHP language. When we run our code analysis with Codacy initially we got few errors in analyzing the code then we came to know whenever a repository is added to this tool it takes time to register the code repository and it took around 3 hours of time to scan such as a huge code base. We found that there are total of 36459 open issues we found when we scan the tool. Out of which the security issues related are 2952. 

![Codacy](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture10.png)


![Codacy](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture11.png)


The tool found many issues related to security that are maily related to the usage of deprecated functions from the lower versions of php. The next issues were all related to the improper handling of the improper usage of include file operation which is a major security threat as the complete directory of the sensitive information can be exposed to the attacker. The remaining issues are usage of superglobal variables in the code, improper usage of validated Sanitized Input. The above mentioned isues are related to the following CWE’S.

##### Discouraged-Function-issues: 

![Codacy](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture16.png) 

##### Include file Issues:

![Codacy](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture17.png) 

#### Super Global Variables Issues:

![Codacy](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture18.png)
 
#### Validated Sanitized input issues:

![Codacy](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Pictures/Picture19.png)

The tool has shown the issues related to usage of discouraged functions which is related to the security as shown above. Multiple issues have been reported related to the discouraged functions, file include functions, Super Global variables, validation of sanitized input.  Then based on the issues when I gone through the CWE documentation related to PHP issues I found that the similar weakness exist in  CWE-98 is the one which is related to the improper control of the include functions. And also weakness related to the super global issues are related to the CWE-1024 which is the exposure of the Global variables. The Codacy tool provide the relation like how to avoid the weakness in the code by highlighting the line of the code and by giving the brief about how to avoid the weakness in the code which is easily understand by the programmers.

The CWE’S related to the above issues are :

CWE-98: Improper Control of Filename for Include/Require Statement in PHP Program ('PHP Remote File Inclusion')
CWE-1024: Comparison of Incompatible Types.


## Summary of key findings

#### [CWE-798](http://cwe.mitre.org/data/definitions/798) - Use of Hard-coded Credentials

(Parent of [CWE-259](http://cwe.mitre.org/data/definitions/259) - Use of Hard-coded Password (specific for Password))

Hard-coded credential can be a valuable resource for an attacker that allows it to bypass the authentication that was configured. This creates a security hole which might be difficult for the system to detect, and even if detected might be difficult to fix. There exist to main variation, inbound (software contains an authentication mechanism that checks the input credential against a hard-coded set of credentials) and outbound (software connects to another system, and this system contains hard-coded credential for connecting components). This type of weakness is related to CWE-344 Use of invariant value in Dynamically Changing Context, CWE-671 Lack of administrator control over Security and CWE-287 Improper Authentication. Related attach patterns CAPEC-70 Try common or Default Usernames and Passwords.

#### [CWE-307](https://cwe.mitre.org/data/definitions/307.html) - Improper Restriction of Excessive Authentication Attempts
Improper restriction of excessive authentication attempts can lead to brute force and dictionary attacks since it does not prevent multiple failed authentication attempts. This type of weakness is related to CWE-799 Improper Control of Interaction Frequency and CWE-287 Improper Authentication. We can see related vulnerabilities in CVE-1999-1152. Related attack patterns can be seen in CAPEC-16 Dictionary-based Password Attack and CAPEC-49 Password Brute Forcing.


#### [CWE-532](https://cwe.mitre.org/data/definitions/532.html) - Insertion of Sensitive Information into Log File

Information in the log file can give valuable guidance to an attacker. Different log files can be used for different stages and can unconsciously report sensitive data. For example, server logs can give information on the full path, names, and system information, and sometimes usernames and passwords. This type of weakness is like CWE-538 Insertion of sensitive information into an externally accessible file or directory. CVE-2017-9615 and CVE-2018-19999036 are the related vulnerabilities resulting from this weakness. CAPEC-215 holds more information on attack patterns.

#### [CWE-117](https://cwe.mitre.org/data/definitions/117.html) - Improper output neutralization for Logs

This can allow an attacker to forge log entries or inject malicious content into logs. This happens when data enters an application from an untrusted source or when data is written to an application or system log file. This type of weakness is related to CWE-116(Improper Encoding or Escaping of Output) and can lead to CWE-93(Improper Neutralization of CRLF sequences-CRLF Injection). We can see these related vulnerabilities in CVE-2006-4624. Related attack patterns show CAPEC-268(audit log manipulation) CAPEC-81(weblogs tampering) and CAPEC-93(Log Injection-Tampering-Forging).

#### [CWE-778](https://cwe.mitre.org/data/definitions/778.html) - Insufficient Logging

 This type of issue occurs when software either does not record the event or omits important details about the event when logging it. If security-critical events such as failed login attempts are not logged properly, this can make malicious behavior more difficult to detect and can hinder analysis. This weakness is related to CWE-223 omission of security-relevant Information. This type of weakness can lead to CVE_2008-4315, CVE-2008-1203 vulnerabilities.

#### [CWE 330](https://cwe.mitre.org/data/definitions/330.html) - Use of Insufficiently Random Values


In scenarios where the software generates  random values in a context, there is a high scope that the attacker can guess the next value that would be generated and he can gain access to sensitive information or impersonate as another user. For example when the software generates a random identifier for a user’s session with help of user id, then the session id will always be the same, and thus the attacker could easily predict the session and he can attack the session. To prevent this attack using a 256- bit seed is good enough to create a good random number. Also using good encryption strategies can help.This can also lead to other cryptographic and authentication errors. Related attack patterns include CAPEC-112, CAPEC-485, CAPEC-59.

#### [CWE 315](https://cwe.mitre.org/data/definitions/315.html) - Cleartext Storage of Sensitive Information in a Cookie

In some cases the application can store sensitive information in cleartext in a cookie and the attackers can take advantage of it with the help of some tools and read the sensitive information. Some scenarios include admin password stored in a cookie, authentication information stored in a cookie and so on. Good encryption techniques can help in securing the data and reduces the risk of sensitive data being captured by the attacker. The other related attack patterns include CAPEC-31, CAPEC-37, CAPEC-39and CAPEC-74.

#### [CWE-624](https://cwe.mitre.org/data/definitions/624.html) - Executable Regular Expression Error:

Regular expressions will be used many times for the input validations. But when it comes to performance analysis these types of the input validations against the regular expressions are very costly. Especially in the systems like Magento if the time for performing a task is high then it can easily result in the Denial of service. Because  with the increase in size of the input string, the comparison time also increases with the regular expression. Attackers can easily exploit this in the e-commerce systems as there will be lot of scope for the inputs. That is the reason we have selected this CWE for manual code review, we have given different attacks for denial of services in our misuse and assurance cases. 


#### [CWE-95](https://cwe.mitre.org/data/definitions/95.html) - Improper Neutralization of Directives in Dynamically Evaluated Code ('Eval Injection’):


Input validation is very vital in the e-commerce systems like Magento, there will be case where these input strings will be taken to execute the code in the background of the system. If the input string is not validated properly then there is a chance for the attackers to run that code and perform operation that are prohibited. In these consequences application security will be seriously impacted. We have mentioned different types of the injection attacks in our misuse and assurance cases that is the reason we have selected this specific CWE for the manual code review. The related attack patters are CAPEC-35 : Leverage Executable Code in Non-Executable Files.

#### [CWE-79](https://cwe.mitre.org/data/definitions/79.html) - Improper Neutralization of Input During Web Page Generation

The CWE-79 is related to the inject the malicious code into the user session cookies and gain control over the username and password of the users of the Magento and with the help of username and password the attackers try to run the commands which make changes in the Magento system. This type of attack also has an impact on the Availability Access control mechanism. The SSL certificate will avoid all such kinds of attacks related to Magento. Magento documentation provides the instructions to setup SSL for Magento systems.

#### [CWE-1004](https://cwe.mitre.org/data/definitions/104.html) - Sensitive Cookie Without 'HttpOnly' Flag.

The CWE-1004 is related to the that whenever we include the ‘HttpOnly’ flag value in the session cookie which avoids all the attacks of CSS. But in our code, there is no flag value is used as magneto proposes the solution to set the flag value with environment variables or with the help of GUI from admin console can be used to make changes by the super admin.


## Contributions

The team realized that we could do some contribution on the installations documentation since we had some problem while following it.
To contribute to the project, we need to be complaint with Magento's contribution guidelines as it’s a big open-source project for eCommerce platform and contribution has to be genuine. Since we intend to contribute with the documentation, we will need to create a topic on the [Magento 2](https://community.magento.com/t5/Magento-2-x-Feature-Requests-and/idb-p/feature-requests?_ga=2.240654403.1910862862.1607290268-1686783359.1599864396) Feature Requests and Improvements forum. In this new topic we intend to suggest new content on the documentation in areas that we had doubts during installation and where we had to follow third parties’ instructions such as forums and blogs. The main topics that the team will introduce are:
-	Clarification on the PHP-extensions and their dependencies.
-	Clarification on the supported PHP versions.

These topics are better explained on Installation and security related configuration in [Magento](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Use%20-%20Misuse%20Cases/Requirements%20for%20Software%20Security%20Engineering.md).
From our analysis the team does not intend to do a code contribution. This decision was made based on two points. Firstly, the group could not find any code problems during the manual code analysis, due to the project size and PHP being a new language to the group. Secondly, the insecurity about the results of our automated code analysis, due to possible cases of false positives and the inexperience with such tools.


## Reflection

We had faced multiple issues at the beginning of code analysis; the project was big, the PHP language was new, and as well the code analysis. Based on the tools suggested by the professor, the task became easy and we also had to rely on a few online links for installation and setup purposes. 

Initially, we were in a dilemma on how to approach code analysis as PHP is a new language for all the team members. Having said that we started to go through those tools which the professor has listed as part of the lecture and identified the tool which best suits for our PHP project. We found SonarQube supports PHP and started to dig into it, which almost took two hours for the setup and 9 hours to complete execution. Parallelly few of the team members were doing manual code reviews using issues reported in the actual Magento GitHub website based on our earlier understanding from misuse case and assurance case assignments. Since we were using SonarQube for the first time we had faced multiple issues while executing. We referred to their website and few YouTube links for installation, setup, and any language-specific rules. The first time when we executed it, even though the code analysis execution was successful in the backend, the frontend dashboard was throwing some errors and not reflecting the analysis report. Hence, we had to do a fresh setup once again from the beginning and run the execution again. Finally, we were able to see the issues on the dashboard this time. Since we used the community edition, we weren’t allowed to download the analysis report as it was supported only for the enterprise edition, and hence had to come up with a way to share the analysis report with team members. Tool analysis reflected around 4.5K issues, so we first analyzed major issues reported for security and explored more using CWE and CVE.

For manual analysis, as mentioned earlier since everyone is new to PHP and because the codebase was huge, we had to struggle a bit to analyze the code flow and the strategy was a bit vague. We later set up a proper code review strategy of going through issues reported on GitHub, identified related CWE’s, and CVE to explore more from the codebase, after the team’s check-in with Professor. 

Additionally, we also explored a few more automated tools available online; Codacy and Sonar Cloud, to validate whether all tools were reporting similar issues. Codacy free version was not so good and the whole team had to rely on SonarQube analysis which wasn’t easy to share as mentioned earlier.

We learned multiple things from this project, as to what is code analysis and its significance; the varieties of automated code analysis tools and how to use those; and why manual code review is important. Professor’s instructions on manual and automated code analysis helped us to move forward with our assignment. Also, we understood together as a team, we can make uneasy tasks easy and we enjoyed working together. Our regular team meetings, planning and peer review on segregated tasks helped us to meet this milestone on the given timeline.



[Project Dashboard](https://github.com/pradeepkoneti/Softwareassurance/projects/6)

[Team Meetings - MOM](https://github.com/pradeepkoneti/Softwareassurance/blob/master/MOM.md)