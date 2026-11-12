# Home Cybersecurity Lab

An academic penetration-testing case study covering vulnerability assessment, endpoint compromise, credential exposure, and access to sensitive data across a virtual lab.

This repository presents a public summary of the **ET0741 Network Hacking Mini Project** group report dated **2 February 2026**. Neo June Wai is a credited group member. The source does not separate individual contributions, so the results below are attributed to the group.

## Project outcome

The report records administrative access to a Windows XP Pro SP2 workstation, recovery of local account credentials, access to internal servers, and retrieval of a simulated bank code. It rates the overall lab risk as **High**.

The Windows XP OpenVAS scan reported **15 filtered findings: 3 high, 9 medium, and 3 low**. Scanner results and demonstrated compromise are documented separately.

## Scope and environment

The exercise used academic virtual machines in a NAT / Vnet6 environment. "Unique.com" is the scenario organization name, not an external testing target. Testing was limited to the supplied lab; denial-of-service and external or production systems were excluded.

| System | Role |
| --- | --- |
| Kali Linux | Assessment workstation |
| Windows XP Pro SP2 | Initial victim workstation |
| Linux end-user system | Additional in-scope endpoint |
| Service1 | Application server |
| Service2 | FTP server |

The source describes a shared internal subnet. It does not establish routed pivoting or an independently tested perimeter boundary. The hypervisor is not confirmed in the report.

## Assessment workflow

1. Discover hosts and enumerate exposed services.
2. Review OpenVAS findings on the Windows XP workstation.
3. Validate remote compromise using Metasploit.
4. Examine local credential exposure and password recovery.
5. Discover and access internal services.
6. Combine information from Service1 and Service2 to retrieve the lab's protected data.
7. Assess impact and propose remediation.

See the [case study](docs/case-study.md) for the attack narrative and its limitations.

## Findings at a glance

| Finding | Evidence status | Defensive priority |
| --- | --- | --- |
| Unsupported Windows XP endpoint and administrative compromise | Reported scan and successful session | Replace or isolate the legacy endpoint |
| Recoverable local credentials | Reported hash extraction and password recovery | Rotate credentials and reduce privileged access |
| Insecure server access on TCP 1524 and Telnet | Reported server access | Remove unauthorized listeners and restrict management access |
| Plaintext credentials and exposed key material | Reported file discovery | Remove secrets from files and restrict access |
| Legacy TLS and vulnerable ManageEngine service on TCP 6767 | Scanner-reported; individual exploitation not established | Verify findings, retire or patch service, harden TLS |
| Broad access between lab systems | Reported shared-subnet reachability | Introduce and test service-specific segmentation |

The [findings and remediation register](docs/findings-and-remediation.md) explains evidence, impact, and proposed validation. Remediation has **not** been demonstrated or retested in this repository.

## Tools documented in the report

- Kali Linux
- OpenVAS
- Nmap / Zenmap
- Metasploit Framework
- Netcat
- CrackStation

The original tool table also names Rainbowcat, but does not explain its use. Wireshark, packet analysis, and VirtualBox appeared in the earlier repository description; this report does not substantiate those activities or that hypervisor.

## Documentation

- [Case study and environment](docs/case-study.md)
- [Findings and remediation](docs/findings-and-remediation.md)
- [Evidence index and source limitations](docs/evidence-and-limitations.md)

## Learning outcomes

The exercise illustrates how a vulnerable endpoint, exposed credentials, and weak internal service controls can combine into a wider compromise. It also highlights the need to distinguish tool output from verified exploitation and to retain evidence that supports each claim.

For defensive engineering, the priorities are asset lifecycle management, restricted administrative access, secret handling, network segmentation, and remediation verification.

## Publication and attribution

Source: *ET0741 Penetration Testing Report, Group 3*, dated 2 February 2026, supplied for this portfolio summary.

This repository is a sanitized derivative of a group academic report. It does not claim a professional client engagement, sole authorship, or new testing. Student identifiers, other students' personal details, credential values, hashes, keys, and the simulated bank code are omitted. The original report and screenshots are not published here because they contain material requiring redaction.

Use the documentation only for authorized learning and defensive assessment.
