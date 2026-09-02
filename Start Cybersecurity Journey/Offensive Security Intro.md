# Offensive Security Intro

**Offensive Security** is about thinking like an attacker to find weaknesses before real hackers do.
- basically simulating a hacker's actions to find weaknesses!

## Practical Lab:

Task 2:

<img width="513" height="412" alt="image" src="https://github.com/user-attachments/assets/5943cbe2-5ac2-4630-a819-810c03c45bf6" />

*What is the bank account number in the FakeBank application?*

**ANSWER:** 8881

---
Task 3:

Find a weakness in the FakeBank application. 
One common mistake is leaving hidden pages accessible.

You will be using this to run your first hacking tool, `dirbuster`. 

To find hidden pages using `dirbuster`, we will use the `dirb` command and the URL that we wish to search:
```bash
$ dirb http://fakebank.thm
```
Any lines from the output that start with `+` are pages that have been found. 
Dirb will find two URLs:

<img width="467" height="354" alt="image" src="https://github.com/user-attachments/assets/f26bdffa-4751-4019-a504-afcf73d239ce" />


*Dirb found one URL, `http://fakebank.thm/images`.*  
*What is the other hidden URL?*

**ANSWER:** `http://fakebank.thm/bank-tranfer`

---
Task 4:

You should now have found a hidden admin panel that lets you add money to your account (which was `http://fakebank.thm/bank-tranfer`)

"Use your account number 8881 and deposit $2000 (or more). After depositing, return to your account page and confirm the balance is now positive."

1. Add `/bank-tranfer` to `http://fakebank.thm` to access the admin portal page:

<img width="515" height="412" alt="image" src="https://github.com/user-attachments/assets/76ebfbca-3906-463e-b34b-bc5d1dfe14bd" />


2. Add bank account # 8881 in the dropdown menu

3. Type in 2000 (or more) into "Amount to deposit in USD" box

4. Click "Deposit Money" :D

<img width="512" height="409" alt="image" src="https://github.com/user-attachments/assets/5255cd3e-691d-4b64-a840-2a3008b94adb" />

**ANSWER:** BANK-HACKED

