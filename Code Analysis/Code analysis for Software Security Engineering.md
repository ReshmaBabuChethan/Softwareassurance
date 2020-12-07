# Code Review

### Code Review Strategy

The Magento code is mostly written in PHP. There are many components in the systems like the payments, UI and the integration modules, etc. As this open-source software is available for a long time, many third party plugins can be installed and integrated with the software. The plugins typically use the API calls but are not included in the source code. There is a clear developer guide that will give instruction to all the contributors.

As the project codebase is huge, full manual review is not a feasible solution to completely review it. To complete the code review, we have decided to incorporate both the code review approaches, automated and manual, to perform the analysis. To execute both the approaches in parallel, some of the team members who got familiar with the automated code analysis tools will go ahead with the Magento code's installation and analysis with the automated code review tools. The rest of the team will go through the Magento issues and select a list of the CWE relevant to the existing cases. For selecting the CWE’s, we have even gone through a Scenario-based strategy that analyzes our previous Misuse and Assurance cases to match the possible attacks that can happen in the Magento system. By the end of the analysis of the issues, misuse cases, we ended up selecting 11 CWE that will be analyzed in the Magento code.

While coming to the automated code review, we researched the automated code review tools that will be the best fit for the Magento system as most of it is written in the Php. Most of the automated code analysis tools are only having commercial packages, which makes them out of our reach. But the automated code analysis tool that looked a perfect fit for our analysis was SonarQube. A community edition can be installed in our local machines and provides different features like issue review, security hotspots, etc. We haven’t solely relied on the SonarQube, we even tried to run the analysis on the SonarCloud, which is an online version of the SonarQube. Still, unfortunately, due to the Magento code's size, it is not possible to run the analysis in the SonarCloud. Then we explored other tools that are good at analyzing the Php code and ended up with the Codacy. The Codacy is a publicly available, online tool which can be used for static code analysis. So, both SonarQube and Codacy are mainly used to identify potential security concerns in the existing Magento codebase. On the whole, we have used both the automated and manual code review process to find the potential security issues based on the attacks that we have outlined in our misuse cases, assurance cases, and threat models.



### Findings and Summary from manual code review



### Findings and Summary from automated code scanning


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
$password = "65DBGgwe4uazdWQA"; // Sensitive
$httpUrl = "https://example.domain?user=user&password=65DBGgwe4uazdWQA" // Sensitive
$sshUrl = "ssh://user:65DBGgwe4uazdWQA@example.domain" // Sensitive



We can also check for suggestions from the tool on how to remediate this type of sensitive code.

$user = getUser();
$password = getPassword(); // Compliant

$httpUrl = "https://example.domain?user=$user&password=$password" // Compliant
$sshUrl = "ssh://$user:$password@example.domain" // Compliant

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
The CWE’S related to the above issues are :
CWE-98: Improper Control of Filename for Include/Require Statement in PHP Program ('PHP Remote File Inclusion')
CWE-1024: Comparison of Incompatible Types.




### Summary of key findings



### Contributions

The team realized that we could do some contribution on the installations documentation since we had some problem while following it.
To contribute to the project, we need to be complaint with Magento's contribution guidelines as it’s a big open-source project for eCommerce platform and contribution has to be genuine. Since we intend to contribute with the documentation, we will need to create a topic on the [Magento 2](https://community.magento.com/t5/Magento-2-x-Feature-Requests-and/idb-p/feature-requests?_ga=2.240654403.1910862862.1607290268-1686783359.1599864396) Feature Requests and Improvements forum. In this new topic we intend to suggest new content on the documentation in areas that we had doubts during installation and where we had to follow third parties’ instructions such as forums and blogs. The main topics that the team will introduce are:
-	Clarification on the PHP-extensions and their dependencies.
-	Clarification on the supported PHP versions.

These topics are better explained on Installation and security related configuration in [Magento](https://github.com/pradeepkoneti/Softwareassurance/blob/master/Use%20-%20Misuse%20Cases/Requirements%20for%20Software%20Security%20Engineering.md).
From our analysis the team does not intend to do a code contribution. This decision was made based on two points. Firstly, the group could not find any code problems during the manual code analysis, due to the project size and PHP being a new language to the group. Secondly, the insecurity about the results of our automated code analysis, due to possible cases of false positives and the inexperience with such tools.


### Reflection

We had faced multiple issues at the beginning of code analysis; the project was big, the PHP language was new, and as well the code analysis. Based on the tools suggested by the professor, the task became easy and we also had to rely on a few online links for installation and setup purposes. 

Initially, we were in a dilemma on how to approach code analysis as PHP is a new language for all the team members. Having said that we started to go through those tools which the professor has listed as part of the lecture and identified the tool which best suits for our PHP project. We found SonarQube supports PHP and started to dig into it, which almost took two hours for the setup and 9 hours to complete execution. Parallelly few of the team members were doing manual code reviews using issues reported in the actual Magento GitHub website based on our earlier understanding from misuse case and assurance case assignments. Since we were using SonarQube for the first time we had faced multiple issues while executing. We referred to their website and few YouTube links for installation, setup, and any language-specific rules. The first time when we executed it, even though the code analysis execution was successful in the backend, the frontend dashboard was throwing some errors and not reflecting the analysis report. Hence, we had to do a fresh setup once again from the beginning and run the execution again. Finally, we were able to see the issues on the dashboard this time. Since we used the community edition, we weren’t allowed to download the analysis report as it was supported only for the enterprise edition, and hence had to come up with a way to share the analysis report with team members. Tool analysis reflected around 4.5K issues, so we first analyzed major issues reported for security and explored more using CWE and CVE.

For manual analysis, as mentioned earlier since everyone is new to PHP and because the codebase was huge, we had to struggle a bit to analyze the code flow and the strategy was a bit vague. We later set up a proper code review strategy of going through issues reported on GitHub, identified related CWE’s, and CVE to explore more from the codebase, after the team’s check-in with Professor. 

Additionally, we also explored a few more automated tools available online; Codacy and Sonar Cloud, to validate whether all tools were reporting similar issues. Codacy free version was not so good and the whole team had to rely on SonarQube analysis which wasn’t easy to share as mentioned earlier.

We learned multiple things from this project, as to what is code analysis and its significance; the varieties of automated code analysis tools and how to use those; and why manual code review is important. Professor’s instructions on manual and automated code analysis helped us to move forward with our assignment. Also, we understood together as a team, we can make uneasy tasks easy and we enjoyed working together. Our regular team meetings, planning and peer review on segregated tasks helped us to meet this milestone on the given timeline.


