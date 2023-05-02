#  **JS Regex-Ion**

## **Summary**

This is a brief tutorial explaining regular expression (regex), its main components, and what it does. 

As an example, we will take a look at the regex for the email address and do a breakdown of its components to better understand what each component represents. 

Regex “Matching an email address”: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## **Table of Contents**

- [Anchors](#anchors)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Quantifiers](#quantifiers)
- [The OR Operator](#the-or-operator)

## **What is Regex?**

Before we will dive deeper into our example, we need to define regex and its functionality. 

Regex stands for **reg**ular **ex**pression, and can be described as a series of special characters that are used to define a search pattern. When writing code, this search pattern can be used for basic validation purposes (e.g. validation criteria for creating passwords, verifying that user's email address matches the email address format, etc.). Regex are universal and can be used in any programming language. 

## **Regex Components**

Since regex is considered to be a literal, it must be wrapped in the **"/"** characters. 

In our example, we can see that the regex begins and ends with the **"/"** characters: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

In addition, regex can contain the following components: anchors, groups, bracket expressions, quantifiers, character classes, OR operators, flags, and character escapes. 

As we go through the "matching an email address" regex example, we can see different components at work. 

### **Anchors**

Each regex usually contains anchor components such as **"^"** and **"$"** characters:
- The **"^"** character signifies the beginning of the line (if searched in text) or string (if use in code) followed by a range of the characters. 
- The **"$"** character signifies the end of the line (if searched in text) or string (if use in code) preceded by a range of the characters. 

In our example, the regex has to starts at the beginning of the string (must start with 1 or more characters) `/**^**([a-z0-9_\.-]+)...`, and must end at the end of the string `...([a-z\.]{2,6})**$**/`. 

Now that we know that the regex is a considered to be a literal and has anchors (which start and end the string), let’s look further into the pattern `([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})` to see what each set of characters means.

### **Grouping Constructs**

Depending on the complexity of the regex, multiple parts of the string may need to be verified to ensure that different sections fulfill different requirements. These sections are called Groups and are defined using round parentheses **"()"**. 

In our example, we can see that the regex has 4 groups:
- **Group 0**: 
    - The whole regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` is considered to be a group of its own.
- **Group 1**: `([a-z0-9_\.-]+)`
    - This means that the first group of the string is looking for an exact match `[a-z0-9_\.-]`  followed by the quantifier character "+" within the string. 
- **Group 2**: `([\da-z\.-]+)`
    - This means that the second group of the string is looking for an exact match `[\da-z\.-]` followed by the quantifier character "+" within the string.
- **Group 3**: `([a-z\.]{2,6})`
    - This means that third group of the string is looking for an exact match `[a-z\.]` followed by a quantifier {2,6} within the string.

The groups 1 and 2 are joined by the **"@"** character, and then joined with the group 3 by the **"`\.`**, which represents literal dot(.) in this expression. 

### **Bracket Expressions**

The Bracket Expressions can be defined as any range of characters inside the square brackets **"[]"** that we want to match. In other words, we want to ensure that the range of the characters that is inside of the **[]** brackets is included in our match criteria regardless of the string’s length. 

The following match criteria can be listed within the Bracket Expressions:
- `[a-z]`: the string can contain any lower case letters between **a** and **z**. 
- `[A-Z]`: the string can contain any capital case letters between **A** and **Z**. 
- `[0-9]`: the string can contain any numbers between **0** and **9**. 
- `[_\.-]`: the string can contain **underscore**, **dot**, or **hyphen**.  

In the regex example, we can see several instances where the Bracket Expressions are used:
- In Group 1, the following match criteria defined for the string: **`[a-z0-9_\.-]`**. 
    - In this instance, the characters in the Group 1 will match any string that includes the combination of the lowercase letters between "a" and "z", any numbers between "0" and "9", and have special characters of underscore, dot or a hyphen. 
- In addition to matching the character criteria in Group 1 before the "@" character, the string must also match the character criteria in Group 2: **`[\da-z\.-]`**
    - The string must contain a combination of a digit character (represented by the character class **\d**, which is equivalent to [0-9]), any lowercase letters between "a" and "z", and a special character of hyphen or a dot. 
- Additionally, the regex also contains the character criteria for Group 3: **`[a-z\.]`**
    - The string must contain the combination of the lowercase letters between "a" and "z" and a special character of dot. 

### **Quantifiers**

As previously mentioned above, in addition to the bracket expressions, regex also has Quantifiers. 
Quantifiers can be defined as string's set limits that must be matched, and usually, include minimum and maximum number of characters that the regex is looking for. 

In the "match email address" regex, we can see the following examples of Quantifiers:

- **"+"**: implies that that the instance of the character can be matched one or more times
    - This type of quantifier can be seen in Group 1, following the Bracket Expression: `([a-z0-9_\.-]+)`
    - It can also be seen in the Group 2, also following the Bracket Expression: `([\da-z\.-]+)`

- **"{}"**: curly brackets can be used to set different types of limits that need to be matched:
    -  {n}: implies that the character pattern must be matched the n number of times
    -  {n, }: implies that the character pattern must be matched at least n number of times
    -  {n, x}: implies that the character patter must be matched between “n” (minimum) and “x”(maximum) times. 
        -    This type of quantifier can be seen in Group 3, where we are specifying that the combination of characters must be between 2 and 6 : `([a-z\.]{2,6})`

### **OR Operators**

The "OR Operator" is expressed as **"|"** and can be defined as an expression that could be written as (x|y) instead of [xy]. 
The "matching email address" regex does not contain any OR Operators; however, the character requirements for the Group 3 could be written slightly different such as (com|net|org|edu). The modified expression would not be as all-inclusive as the one we defined, because we are excluding any other combination of characters that could follow after the "." character in the email address. 

## **Conclusion**

After reviewing different regex components, the regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`  can be summarized as following:
- The email address must:
    - Start with any combination of lower-case letters, digits and special character such as underscore, hyphen or dot that matches the pattern at least one or more times,
    - Followed by the "@" character,
    - Followed by any combination of digits, lower-case letters and special character such as dot or hyphen that matches the pattern at least one or more times,
    - Followed by a dot,
    - followed by any combination of lowercase letters and a dot with a limit between 2 and 6 characters long. 

## **Author**
My name is Anastasiya, and I am currently enrolled in the Full Stack Application Development bootcamp at the University of Washington in partnership with edX. I enjoy learning new concepts and finding a way to implement them in real-life scenarios. 
To get in touch with me, you can visit my GitHub profile: https://github.com/anryl050

## **Resources**
The following resources were used to create this gist:
- https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial
- https://www.youtube.com/watch?v=7DG3kCDx53c
