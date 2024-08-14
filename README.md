<h1 align="center">Summary Diagram</h1>


<p align="center">
<br/>
<img width="950" alt="Portfolio" src="https://i.imgur.com/2l36XB7.png">
<br />
</p>


<br />
<br />

<h1 align="center">Project walk-through</h1>

<br />
<br />

---
<a name="toc"></a>
**Table of Contents:**

- [Setting Up the Environment](#setting-up-the-environment)
- [User Input and Data Preparation](#user-input-and-data-preparation)
- [Obtaining a Password List](#obtaining-a-password-list)
- [Implementing the Password Cracking Logic](#implementing-the-password-cracking-logic)
- [Comparing Hashes and Finalizing the Program](#comparing-hashes-and-finalizing-the-program)
- [Testing the Program](#testing-the-program)




---

<h4>Tip: Any configuration options not mentioned in the walkthrough can be left at their default settings</h4>

---

[back to top](#toc)
## Setting Up the Environment

<br />
<br />



 - We'll be using Visual Studio Code for this project. Start by creating a new folder named [SHA1-PASSWORD-CRACKER] and within it, create a file called [main.py].
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/XDhOPxM.png">
<br />
<br />
<br />
<br />


 - In main.py, we'll begin with the standard Python idiom to check if the script is being run as the main program:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/r3NWO9o.png">
<br />
<br />
<br />
<br />



---

[back to top](#toc)
## User Input and Data Preparation

<br />
<br />

 - The first step is to prompt the user for the SHA1 hash they want to crack:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/Akx1yEh.png">
<br />
<br />
<br />
<br />


 - To ensure consistency, we'll clean up the user input by removing any leading or trailing spaces and converting it to lowercase:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/QnopHhE.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Obtaining a Password List

<br />
<br />

 - For our dictionary attack, we need a list of common passwords. These lists are often used in ethical hacking and can be found online.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/PKNvEHO.png">
<br />
<br />
<br />
<br />

 - Search for "password list file" in your preferred search engine.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/YY8XZJH.png">
<br />
<br />
<br />
<br />

 - Once you find a suitable list, copy the URL of the file.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/Eyeq2Kp.png">
<br />
<br />
<br />
<br />

 - Use the cURL command in the VS Code terminal to download the file. We'll rename it to [passwords.txt] for simplicity:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/gU2vIjK.png">
<br />
<br />
<br />
<br />

 - You should now see passwords.txt in your project folder.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/eWh93TK.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Implementing the Password Cracking Logic


 - Now, let's implement the core logic. We'll read the password file, iterate through each line, and compare it to the user's input:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/DFT6jeC.png">
<br />
<br />
<br />
<br />

 - To compare the passwords, we need to convert each password to its SHA1 hash. We'll create a function for this:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/hRDqGcw.png">
<br />
<br />
<br />
<br />


 - Let's define the `convert_text_to_sha1()` function. First, we need to import the necessary module.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/XnX4w8s.png">
<br />
<br />
<br />
<br />


 - The `hashlib` module provides various hashing algorithms, including SHA1.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/rQ2SWqV.png">
<br />
<br />
<br />
<br />


 - Here's our function to convert text to SHA1:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/XEoYhjN.png">
<br />
<br />
<br />
<br />

 - We use the `encode()` method to convert the string to bytes, specifying 'utf-8' encoding for clarity.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/Xx3urYk.png">
<br />
<br />
<br />
<br />



 - The `hexdigest()` method returns the hash as a string of hexadecimal digits, which is what we want for comparison.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/lnMtot0.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Comparing Hashes and Finalizing the Program

<br />
<br />


 - Back in our main logic, we now have the SHA1 hash of each password from the file.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/0IZqFnL.png">
<br />
<br />
<br />
<br />

 - We can compare this hash with the user's input:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/ktC7lip.png">
<br />
<br />
<br />
<br />

 - If we find a match, we'll print the cracked password and exit the loop:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/cL7OVSb.png">
<br />
<br />
<br />
<br />

 - If we've gone through the entire file without finding a match, we'll inform the user:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/GGAPM57.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Testing the Program

<br />
<br />

 - Our SHA1 password cracker is now complete. Let's test it with two scenarios.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/dI9ablL.png">
<br />
<br />
<br />
<br />


 - First, we'll test with a hash that exists in our password list:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/wv6lHpR.png">
<br />
<br />
<br />
<br />



 - Choose a random string from passwords.txt and use an online SHA1 generator to get its hash.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/xjoTV37.png">
<br />
<br />
<br />
<br />



 - Run the program and enter this SHA1 value.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/QnwvW9c.png">
<br />
<br />
<br />
<br />



 - The program should successfully find and display the password.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/zdiFTFO.png">
<br />
<br />
<br />
<br />


 - Next, let's test with a hash that doesn't exist in our list:
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/GCvPe0l.png">
<br />
<br />
<br />
<br />


 - Enter a random SHA1 hash not in the file. The program should respond with "Password not found".
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/UhlpIoS.png">
<br />
<br />
<br />
<br />







\<end\>

[back to top](#toc)

<br />
<br />
<br />

