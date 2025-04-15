# Password Spray Attempt (No Compromise)  
**Date Investigated:** March 30, 2025  
**Environment:** LOG(N) Pacific | Cyber Range
---

<p>
  Real-world threat activity investigated through hands-on detection and response inside a student cyber range environment.
</p>

-----
<h2>Incident Summary</h2>

A high-severity alert flagged suspicious logon activity targeting an internet-facing lab VM. Investigation confirmed a password spray attempt from external IPs, focused on the built-in `guest` account. No successful authentication or system compromise occurred. The device was not enrolled in endpoint protection and was publicly exposed at the time of the attack.

---

<img src="https://img.shields.io/badge/-WHO-000000?style=for-the-badge&logo=github&logoColor=white" />

- Targeted device: `finallabscott`  
- Attacker IPs from: China, Russia, and global scanning infrastructure  
- Account targeted: `guest` (built-in, enabled)

---

<img src="https://img.shields.io/badge/-WHAT-000000?style=for-the-badge&logo=github&logoColor=white" />

- Password spray attack (1,000+ failed attempts)  
- Attempted remote login via "Network Logon"  
- No successful authentication or shell activity observed

---

<img src="https://img.shields.io/badge/-WHEN-000000?style=for-the-badge&logo=github&logoColor=white" />

- Alert triggered: Mar 29, 2025  
- Logs reviewed: Mar 23–30, 2025

---

<img src="https://img.shields.io/badge/-WHERE-000000?style=for-the-badge&logo=github&logoColor=white" />

- Device: `finallabscott`  
- Exposure: Internet-facing with no Defender for Endpoint  
- Remote IPs: `218.92.0.186`, `5.178.87.180` (VT: known scanners)

---

<img src="https://img.shields.io/badge/-WHY-000000?style=for-the-badge&logo=github&logoColor=white" />

- External actors targeting public systems with weak/default credentials  
- Guest account was accessible and lacked protections  
- Likely part of a mass credential stuffing campaign

---

<img src="https://img.shields.io/badge/-HOW-000000?style=for-the-badge&logo=github&logoColor=white" />

- Automated spray tools attempted login to `guest` account  
- No lateral movement, persistence, or malware seen  
- Failed authentication logs confirmed across multiple time windows

---

<img src="https://img.shields.io/badge/-RECOMMENDATIONS-228B22?style=for-the-badge&logo=vercel&logoColor=white" />

1. **Disable Unused Accounts**  
   Remove or disable default/guest accounts across all VMs.

2. **Limit Exposure**  
   Avoid exposing unmanaged devices directly to the internet.

3. **Enable Endpoint Protection**  
   Enroll all devices in Defender for Endpoint or equivalent tools.

4. **Geo-Block Suspicious IPs**  
   Block known malicious ranges from untrusted regions where possible.

5. **Enforce Lockout Policies**  
   Implement lockout after failed login attempts to prevent enumeration.

---

<img src="https://img.shields.io/badge/-TIMELINE-4169E1?style=for-the-badge&logo=clockify&logoColor=white" />

| Date       | Event                                        |
|------------|----------------------------------------------|
| Mar 23–29  | Multiple failed logons targeting `guest`     |
| Mar 29     | Alert triggered by Sentinel (Password Spray) |
| Mar 30     | Incident triaged, no compromise confirmed    |
