

### CWE-624 - Executable Regular Expression Error:

Regular expressions will be used many times for the input validations. But when it comes to performance analysis these types of the input validations against the regular expressions are very costly. Especially in the systems like Magento if the time for performing a task is high then it can easily result in the Denial of service. Because  with the increase in size of the input string, the comparison time also increases with the regular expression. Attackers can easily exploit this in the e-commerce systems as there will be lot of scope for the inputs. That is the reason we have selected this CWE for manual code review, we have given different attacks for denial of services in our misuse and assurance cases. 


### CWE-95 - Improper Neutralization of Directives in Dynamically Evaluated Code ('Eval Injection’):


Input validation is very vital in the e-commerce systems like Magento, there will be case where these input strings will be taken to execute the code in the background of the system. If the input string is not validated properly then there is a chance for the attackers to run that code and perform operation that are prohibited. In these consequences application security will be seriously impacted. We have mentioned different types of the injection attacks in our misuse and assurance cases that is the reason we have selected this specific CWE for the manual code review. The related attack patters are CAPEC-35 : Leverage Executable Code in Non-Executable Files.

## Manual Code Review:

During our Manual code review, we have gone through the Magento modules that will take the input parameters from the users like the credit card details during the payment phase or other other user details. Mainly the payment details validation blocks are present in java script modules which will validate the given card details for expiry etc. The developers are using regular expressions for validation, but the main thing is that they have kept a limit for the input strings that can be entered. In our opinion this can avert the attacks like the Denial of service as the limit of the characters strictly check the input string before comparing it with the regular expression. Even we have not found any traces for the issues like the code injection in these modules for the input validators.

 