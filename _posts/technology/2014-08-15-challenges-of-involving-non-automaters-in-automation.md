---
title: "Test Automation: The challenge of involving Non-Automators"
tags:
- quality assurance
- test automation
---
Today, very few companies (if at all) rely on pure manual testing for regression.  
Most of the organizations try to figure out their own architecture of the test automation frameworks. And with a little expertise, it is just a matter of days to churn out a fully working test automation framework.

But, the biggest challenge of any automation framework is to excite non-automators for its use. Since manual testers are usually the end-users of an automation suite, their involvement with automation cannot be compromised.

##Challenges & Mitigation
There can be a variety of reasons for manual testers to hate test automation. Some of them are related to skillset and others are related to the thought process of testers. Let's talk a little bit about the reasons from a tester's point of view.

<!--more-->
###Thought Process
In my personal experience, following thoughts usually cross the minds of some manual testers when talking about test automation.

- **Automation will eat my job**  
    One word, Misconception. The only thing that can be done here is to educate the users that the purpose of test automation is to *compliment* manual testing, and not to *replace* testers.
- **Regression seldom finds bugs**  
    This is true in case of stable products, however regression still cannot be ignored. Manual testing cannot cover 100% of the functionality in every build/release, and machines never get bored of running same tests again.
- **It is too much effort**  
    Manual testers are sometimes sceptical about spending effort in automating tests, mainly because they think that their time can be better utilized in finding bugs manually. This issue can be resolved by showing some use-cases where automation has considerably reduced recurring effort. The underlying point is that there is definitely a one time effort in writing a framework or scripts, but usually the ROI is quite high in most of the cases.

###Skill-set
Sometimes manual testers are not programmers, and this can hinder the adoption of an automation framework by a team. These issues can mitigated by designing/choosing a framework according to the targeted set of users. Lets see some scenarios:

- **Testers don't know coding at all**  
    In some organizations, manual testers are not required to learn coding. This scenario is more common in black-box testing environments. In  such environment, if a pure scripting oriented framework is chosen it may take extra effort for the team to learn coding. In such cases it is better to go for different approaches such as keyword-based automation, as they don't required much coding skills and are easier to understand.
- **Unfamiliar with a particular programming language**  
    This scenario further breaks into two cases.
    1. Everyone know a common language  
        The solution is simple. Choose a framework/tool which utilizes that particular language.
    2. Everybody has a different skillset  
        This scenario can be a little tricky. The team can surely go for the non-scripting frameworks but those tests are usually slightly less flexible than scripted tests. The other way is to design a framework which provides the ability to write scripts in any language (like [STAF][]). The flip side of this approach is that maintainability can become an issue if users are free to choose the language they code in.

##Conclusion
Admittedly it is a little difficult to pump up manual testers about test automation. However, by educating the users and making proper choices regarding the design and architecture of the framework, the resistance towards automation can be reduced a great deal.

[STAF]: http://staf.sourceforge.net/
