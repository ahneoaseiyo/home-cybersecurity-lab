# Academic penetration testing case study

## Context

The ET0741 group exercise assessed a deliberately vulnerable virtual environment for the scenario organization Unique.com. The source report is dated 2 February 2026. It describes authorized academic testing of supplied virtual machines and excludes denial-of-service attacks and out-of-scope systems.

This is a retrospective summary of that report. No new scans, exploitation, or remediation were performed while preparing this repository.

## Environment

Kali Linux and the target systems were described as sharing a NAT / Vnet6 internal network. The Windows XP workstation was the initial target; Service1 and Service2 held information used to reach the exercise objective. A Linux end-user system was also in scope.

The report gives the Windows XP scan target as `192.168.119.128`, a private lab address. It does not provide a complete, unambiguous textual inventory of all addresses, interfaces, routes, and access controls. Consequently, this summary does not reconstruct an exact network diagram.

The report's executive summary refers to Internet-user access, while its engagement overview and topology describe an internal attacker on the same network. The internal-lab description is used here; external exploitability was not established.

## Recorded assessment sequence

### Discovery and enumeration

Nmap / Zenmap identified live hosts and open services. The report references operating-system discovery and a topology figure. Reachability inside the shared lab network was established, but the text does not prove traffic crossed an enforced security boundary.

### Vulnerability assessment

OpenVAS assessed the Windows XP workstation. The report records 15 findings after filtering: 3 high, 9 medium, and 3 low.

Reported issues included an unsupported operating system, ManageEngine Security Manager Plus weaknesses on TCP 6767, and legacy SSL/TLS configurations. The report names directory traversal and SQL injection as scanner findings. It does not establish that either was the initial access mechanism.

### Initial access

The report records a successful Metasploit remote session on Windows XP and administrative-level access. The exploit module, CVE, payload, and exact privilege context are not identified in the narrative.

Administrative access is therefore reported as a demonstrated outcome in the source. A particular vulnerability-to-exploit mapping, or a separate privilege-escalation step, cannot be inferred from the text alone.

### Credential exposure

Local account password hashes were extracted, and the report records successful password recovery for two accounts using CrackStation. This supports a credential-exposure finding.

The text does not provide the hash algorithm, cracking duration, or password-policy evidence. It therefore cannot establish the precise cause or strength of every account password. Recovered values and hashes are omitted from this repository.

### Internal server access

The group used further discovery to identify internal services. The report describes Netcat access to a listener associated with TCP 1524 and also mentions Telnet access to Service1.

Netcat is a networking utility, not a protocol. A port's service label alone does not establish the identity of the application behind it. The report supports insecure service access, but lacks sufficient detail to characterize the exact listener or a routed pivot technique.

### Protected data retrieval

The report describes finding a file on Service1 containing key material and Linux account credentials, then obtaining additional key material from Service2. Combining the information reportedly enabled access to the simulated bank code.

The narrative and captions disagree on some filenames and are unclear about which file was password-protected. This summary preserves the reported outcome without inventing encryption details, file formats, or access steps.

## Impact

The recorded chain demonstrates administrative endpoint compromise, disclosure of local and plaintext credentials, access to internal servers, and disclosure of the exercise's protected data.

In a comparable real environment, those conditions could expose confidential data and enable further unauthorized access. Actual financial loss, production impact, persistence, availability disruption, and organization-wide compromise were not measured in this lab.

## Defensive lessons

An exposed legacy endpoint can create opportunities beyond that single host. Removing unsupported systems addresses one entry point; restricting internal services and protecting credentials addresses subsequent access.

Splitting sensitive information across multiple hosts does not itself provide adequate protection when an attacker can access each host. Effective controls must restrict who can access both the data and the means to unlock it.

The next meaningful validation would be to apply the proposed controls and repeat the relevant access checks in an authorized lab. The source report does not document that work.
