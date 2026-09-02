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
