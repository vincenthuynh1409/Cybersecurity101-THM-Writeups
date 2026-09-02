## Shodan

**Shodan** is basically a search engine for the Internet of Things (IoT). 
- Shodan continuously scans the internet, searching for networking equipment, industrial control systems, traffic cameras, and virtually anything else with a public network connection to see what's running and where!

For example, searching `apache 2.4.1` will return a list of servers advertising that version in their HTTP headers, broken down by country, organization, and port. 
- During a penetration test or vulnerability assessment, that kind of visibility is extremely useful, particularly when paired with a known CVE affecting that version.

<img width="661" height="300" alt="Screenshot 2026-09-01 213414" src="https://github.com/user-attachments/assets/601dc6b2-444e-4c38-8218-2ba1d240cf6b" />


Shodan also supports its own query filters, which let you narrow results significantly:

| **Filter** | **Description**                                                                             | **Example**                         |
| ---------- | ------------------------------------------------------------------------------------------- | ----------------------------------- |
| `country`  | Restrict results to a specific country code.                                                | `country:IE`                        |
| `port`     | Filter by a specific port number or a range.                                                | `port:22`                           |
| `org`      | Scope results in a named organisation or ASN Identifier (Who owns a range of IP addresses). | `AS7224`  <br>(Amazon Web Services) |
| `hostname` | Match against a specific hostname or domain.                                                | `hostname:fakebank.thm`             |

---
Task 2:

*"What domain is associated with the IP address `185.243.115.47`?"*

1. Click the `view site` button below to start the Shodan simulation
2. Type `apache` into the search bar
3. Find `185.243.115.47` IP entry

<img width="484" height="441" alt="image" src="https://github.com/user-attachments/assets/5836feea-1997-4c69-9342-10fab45cfbd4" />


**ANSWER**: `tryhackme.thm`

## VirusTotal

**VirusTotal** collates results from over 70 antivirus engines and website scanners into a single interface. 
- Submit a file, a URL, a domain, or a file hash. 
- **VirusTotal** will tell you whether any of those engines have flagged it as malicious or not.

> Whilst not foolproof, **VirusTotal** is a popular resource in the blue teaming community for obtaining a general consensus on suspicious files and links, as well as for gathering intelligence on new threats on the move.

---
Task 3:

*"How many security vendors have identified the file as dangerous?"*

1. Click the `view site` button
2. Search for the file `invoice_payment.exe` on the search bar

<img width="485" height="462" alt="image" src="https://github.com/user-attachments/assets/b27f8fb0-f6fc-4e36-8146-6f885ad37f8c" />


**ANSWER:** 52

## Vulnerability Databases (CVE)

The **Common Vulnerabilities and Exposures (CVE)** program is the closest thing the industry has to a universal dictionary of known vulnerabilities.

Each confirmed vulnerability is assigned a unique identifier in the format `CVE-YEAR-NUMBER`, such as `CVE-2025-55182`. 

If the vulnerability is impactful enough, it may even get a moniker (nickname).
- You may have heard of vulnerabilities such as *Heartbleed, React2Shell, and Log4Shell.* 

These vulnerabilities are given a score **(CVSS)** based on a variety of factors, such as:
- **Impact -** What damage can this vulnerability lead to?
- **Complexity** - Is the vulnerability easy to exploit or not? 
- **Availability** - How likely is it that someone can exploit this?

Organizations use scoring like this to prioritize their level of risk (Addressing the highest scoring first).

These identifiers function as a reference point among vendors, researchers, security tools, and documentation, ensuring that everyone discussing a vulnerability refers to the same issue. 
- Websites like ExploitDB compile this information alongside **"Proof of Concepts" (PoCs)**, which are scripts capable of demonstrating the vulnerability.

---
 Task 4:

*"What **CVSS** (Common Vulnerability Scoring System) classification did the vulnerability get?"*

1. Click the `view site` button
2. Search the Vulnerability Database for **`CVE-2026-1337`** in search bar

<img width="473" height="455" alt="image" src="https://github.com/user-attachments/assets/17edfcf5-c3fc-41fe-b65c-53963a78f913" />

**ANSWER:** 10

## Technical Documentation (MAN)

### Product and Tool Documentation

Each major security tool or platform provides its own documentation, which is the most reliable and up-to-date than any third-party tutorials.

When you're troubleshooting unexpected behavior or trying to understand how to use a tool in a certain way, the official documentation should always be your first stop - not your last.

### Linux "Man" Pages

Have you ever come across a command-line tool or command that you're not familiar with? 

Linux **MAN**ual pages have got your back. 

These pages serve as documentation that you can read within your terminal about any command on Linux, and a majority of cybersecurity tooling.

To view the manual page, run `man <command>`. For example:

A Snippet of the MAN page of "nc":

```shell
user@thm$ man nc
NC
                                                                                  
NAME
       nc — arbitrary TCP and UDP connections and listens

SYNOPSIS
       nc  [-46bCDdFhklNnrStUuvZz]  [-I  length]  [-i  interval]  [-M  ttl] [-m minttl] [-O length] [-P proxy_username] [-p source_port] [-q seconds] [-s sourceaddr] [-T keyword] [-V rtable] [-W recvlimit] [-w timeout]
          [-X proxy_protocol] [-x proxy_address[:port]] [destination] [port]
```
---
Task 5:

*"What is the example command?"*

1. Click the `view site` button to open terminal
2. (`man` is already typed for you) type in `nc` after the `man`
3. Scroll to the bottom of the terminal to find the example command

<img width="471" height="451" alt="Screenshot 2026-09-01 220353" src="https://github.com/user-attachments/assets/1b97adf8-2ed1-46ad-a07c-73b0258ad6d8" />



<img width="566" height="250" alt="Screenshot 2026-09-01 220406" src="https://github.com/user-attachments/assets/45c32048-50ef-40c0-b228-cd2b01c3ac7a" />


**ANSWER:** `nc host.example.com 42`

## GitHub

**GitHub** can be a great resource for staying updated on the latest threats and vulnerabilities. - Researchers often publish **proof-of-concept (PoC)** code, exploitation tools, and detailed technical reports there, which are usually faster than official channels. 

Searching for a CVE identifier (e.g., `CVE-2026-1337`) directly on GitHub often reveals repositories containing PoC code, scanner scripts, or detailed analyses of the vulnerability.

That said, not all PoCs are equally reliable. Some are incomplete, some are intentionally flawed, and occasionally a "PoC" repository is malicious itself. Always verify what you're about to execute.

---
Task 6:

*"What is the name of the script in the repository that will demonstrate the vulnerability?"*

1. Click the `view site` button to open terminal
2. Search up `CVE-2026-1337` on the search bar 
3. Find the script that demonstrates the vulnerability

<img width="466" height="461" alt="image" src="https://github.com/user-attachments/assets/7b0dfc49-9d07-46c7-acd1-09dcc30f8134" />


**ANSWER:** `exploit.py`




