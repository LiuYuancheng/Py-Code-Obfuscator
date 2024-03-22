# Python Program Obfuscator

![](C:/Works/NCL/Project/Malware_Repo/src/pyObfuscator/doc/img/logo_normal.png)

**Program design Purpose** : We want to create a python program obfuscation tool which can easily obfuscate encode the source code to be a bytes type executable python section for people who want to protect their intellectual property rights, or are running Python services with sensitive source code. It will also provide the decoder to convert the obfuscated bytes data back to the source code. The program contents 3 Part: 

- **Obfuscation Encoder** :  obfuscate the python source code (whole file or section of the code) to unreadable byte data and added the execution header to create the executable but unreadable python program 
- **Obfuscate Decoder** : reverse the encode process to convert the obfuscated bytes data back to python code. 
- **Web Interface** : Provide the web UI for the user to easily encode and decode the python program. 

The usage example is shown below :

![](C:/Works/NCL/Project/Malware_Repo/src/pyObfuscator/doc/img/usageExample.png)

```
# Created:     2024/03/21
# Copyright:   Copyright (c) 2024 LiuYuancheng
# License:     MIT License
```

**Table of Contents**

[TOC]

------

### Introduction 

The program obfuscation is a common method to secure and protect Python, it will use the method such as renaming identifiers, code encryption,  code packing and dead code insertion to make it difficult for hackers to understand the execution/control flow or gain access to your sensitive source code. There are several different kinds of obfuscation lib or tools such as [pyarm](https://pyarmor.readthedocs.io/en/latest/) or [offree online tool's obfusaction tool](https://freecodingtools.org/py-obfuscator) , but most of then didn't provide the decode algo, or can't not adjust the obfuscation code side or can only obfuscate file. 

We want to follow the idea of  [offree online tool's obfusaction tool](https://freecodingtools.org/py-obfuscator) to build a web based python program obfuscation program with below feature: 

- Provide multi-layer python code obfuscation with the customizable size of the encoded obfuscated code. 
- Provide the both encoder and decoder function for maintaining and debugging the obfuscated code.
- Provide the whole python program and part of the source code so the result can be a mixed type program. 
- Provide flexible code random contents insertion so every time the generated obfuscated codes are different even use the same source code. 
- Provide a standard API for user to plug in their project and Web-UI to make the encode and decode usage convenience. 

The system work flow is shown below:

![](C:/Works/NCL/Project/Malware_Repo/src/pyObfuscator/doc/img/sysWorkflow.png)

`version v0.1.2`

**Obfuscate Encoder Web Page**

The Obfuscate Encoder page is shown below, to obfuscate a python function or program, copy the python source code in the source code text field, select the random contents append paymaster `randomLen` (0 ~ 100), each line of code will be append 16Bytes random sting * `randomLen` before do the Obfuscation encode. Press the "Run Obfuscation Encode" , the obfuscated code will show on the right result text field.

![](C:/Works/NCL/Project/Malware_Repo/src/pyObfuscator/doc/img/encoderPage.png)

>  Remark: Every time use press the run button, it will generate the different obfuscated code result.



**Obfuscate Decoder Web Page**

Same as the encoder page, the decoder page is shown below. The user need to copy the  obfuscated code's bytes data (in the `exec()` function) in the left text field, then press the run decoder button to convert the obfuscated code back to source code. 

![](C:/Works/NCL/Project/Malware_Repo/src/pyObfuscator/doc/img/decoderPage.png)

> Remark: If the user only want to source code, check the `remote the comments` check box. 



------

### Background Knowledge

**What is Program obfuscation ?** 

Program obfuscation is a technique used in software development to deliberately make the source code of a program more difficult to understand or reverse-engineer, while preserving its functionality. It is commonly employed in scenarios where the developer wants to protect their intellectual property, prevent unauthorized access, or hinder attempts to tamper with the software.

Here are some common techniques used in program obfuscation:

1. **Renaming identifiers**: This involves renaming variables, functions, classes, and other identifiers in the code to non-descriptive or cryptic names. For example, variables like `userInput` might be renamed to `a` or `b`, making it harder to understand their purpose.
2. **Control flow obfuscation**: This technique involves altering the flow of control in the program, making it harder to follow the logical structure. This can be achieved through techniques such as adding redundant code, using conditional statements in unusual ways, or restructuring loops.
3. **Data obfuscation**: Data obfuscation involves disguising data within the program, making it harder to understand or extract sensitive information. This can include encrypting strings or splitting them into smaller parts that are concatenated at runtime.
4. **Code encryption**: This involves encrypting some or all of the code in the program and decrypting it at runtime. This makes it difficult for attackers to analyze the code without knowing the decryption key.
5. **Dead code insertion**: Inserting dead code (code that is never executed) into the program can confuse reverse engineers and make it harder to understand the true functionality of the program.
6. **Code packing**: This involves compressing or packing the executable file, making it harder to analyze using standard tools. The packed code is typically decompressed and executed at runtime.
7. **Anti-debugging techniques**: These are methods used to detect and prevent the program from being debugged, which can make it harder for attackers to analyze the code.

It's important to note that while obfuscation can make reverse engineering more difficult, it's not a foolproof method for protecting software. Skilled attackers may still be able to reverse engineer obfuscated code given enough time and resources. Therefore, obfuscation is often used in conjunction with other security measures such as encryption, access control, and code signing. Additionally, obfuscated code can be harder to maintain and debug, so developers should weigh the benefits against the potential drawbacks before applying obfuscation techniques.