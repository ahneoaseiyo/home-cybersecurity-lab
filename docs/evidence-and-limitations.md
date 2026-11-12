# Evidence index and limitations

## Source and attribution

This summary is based on the supplied *ET0741 Penetration Testing Report, Group 3*, dated 2 February 2026. Neo June Wai appears among the five credited students. The document does not assign individual tasks, so the repository attributes assessment outcomes to the group.

The original DOCX is retained outside this repository. It includes student identifiers and screenshots associated with passwords, hashes, keys, and the simulated bank code. No raw report or screenshot has been published as part of this update.

## Source evidence index

These are references to figures in the source report, not downloadable evidence in this repository. Figure labels and captions are reproduced as an index; the underlying screenshots have not been independently validated here.

| Source reference | What the report associates with it | Relevant finding |
| --- | --- | --- |
| Figures 1.1-1.3 | Host discovery and operating-system identification | LAB-001, LAB-006 |
| Figure 1.4 | Network topology | LAB-006 |
| Figure 2 | Windows XP OpenVAS scan summary | LAB-001, LAB-005 |
| Figure 3 | Successful Metasploit access | LAB-001 |
| Figures 4-5 | Password hashes and recovered passwords | LAB-002 |
| Figure 6.1 | Internal host discovery with Zenmap | LAB-006 |
| Figures 6.2-6.3 | Server port verification | LAB-003 |
| Figure 7 | Service1 file, first key, and stored credentials | LAB-003, LAB-004 |
| Figure 8 | Service2 file and second key | LAB-004 |
| Figures 9-11 | Combined keys and access to protected lab data | LAB-004 |

## Corrections and unresolved details

- **Attacker position:** The executive summary describes Internet-user access; the detailed scope places Kali on the internal network. This repository uses the internal-lab account and makes no claim of external exposure.
- **Severity counts:** The summary uses broad high/critical language, but section 4.2 specifies 3 high, 9 medium, and 3 low findings after filtering. The explicit counts are retained; no critical count is invented.
- **Initial exploit:** Neither a Metasploit module nor a CVE is identified in the narrative. ManageEngine scanner findings are not assumed to be the cause of the successful session.
- **Privilege escalation:** Administrative access is reported, but a separate escalation step and exact security principal are not established by the text.
- **Pivoting:** Same-subnet server access is described. A route, tunnel, or enforced boundary crossing is not established.
- **Netcat terminology:** Netcat is a tool. TCP 1524 and an Ingreslock label do not, by themselves, identify a verified application or protocol.
- **Filenames:** The narrative names TopSecretFile.txt; a caption names TopSecretCode.txt. The role of SecretCode.txt versus the protected bank-code file is also unclear.
- **Credentials:** Password recovery is reported, but the hashing algorithm, recovery duration, and exact password-policy weaknesses are unspecified.
- **Tool usage:** Rainbowcat is listed without a described procedure. Wireshark use, packet analysis, and VirtualBox are not supported by this report.
- **Isolation:** NAT / Vnet6 is the reported configuration. No independent check of Internet isolation or a complete interface and routing inventory is supplied.
- **Remediation:** Recommendations are present; implementation and retest results are absent.
- **Methodology:** The report states alignment with NIST SP 800-115. This repository does not claim that compliance or full methodological coverage was independently audited.

## Publishing additional evidence

Before publishing source excerpts or screenshots:

1. Confirm permission to share group work and any course-provided material.
2. Remove student IDs and unnecessary personal information.
3. Redact plaintext passwords, hashes, key values, tokens, and protected data.
4. Apply permanent redaction to image pixels and inspect the exported result.
5. Keep enough context to identify the tool, target role, and relevant result.
6. Add a caption distinguishing scanner output from a validated outcome.

A redacted evidence set would strengthen this portfolio. Its absence is disclosed here rather than replaced with fabricated screenshots or reconstructed scan output.
