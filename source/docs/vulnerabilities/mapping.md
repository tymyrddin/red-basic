# Mapping vulnerabilities to exploits

## Attack tree

```text
1 List exploitable vulnerabilities by CVSS score
    1.1 Calculate Exploitability
    1.2 Calculate Impact
    1.3 f(Impact)
    1.4 BaseScore
2 Prioritisation possibilities
    2.1 Severity level
    2.2 Vulnerability exposure
    2.3 Criticality
```

## Notes

### Nessus

In Nessus, the Vulnerability Information includes whether known exploits are available for a vulnerability. 
The section labeled “Exploitable With” even shows what tools can be used to exploit the vulnerability.

### Common Vulnerability Scoring System

The Common Vulnerability Scoring System (CVSS) is a standard vulnerability scoring
system used by vulnerability scanners to identify the severity of the vulnerability.
A CVSS base score can be a number from 0 to 10, with 0 being the least severe, and
10 being the most severe.
            
The format of the base score for CVSS2:

```text
CVSS2#AV:N/AC:L/Au:N/C:C/I:C/A:C
```

### Exploitability

Three metrics are used to calculate the exploitability of a vulnerability: 

* The access vector (AV), used to measure how the hacker executes the exploit. Does she have to have physical access 
to the system, be in an adjacent network and use pivoting, or is the vulnerability exploitable from a remote network?
* The attack complexity (AC), to describe how easy or difficult it is to exploit the vulnerability.
* Authentication (Au), used to specify how many times she would need to authenticate to exploit the vulnerability.

```text
Exploitability = 20 * AV * AC * Au
```

### Impact metrics

Impact metrics are used to identify what the impact of the exploit is on the confidentiality (C), integrity (I), and 
availability (A) of systems and their data. The values can be None (N), Partial (P) or Complete (C)

```text
Impact = 10.41 * (1-(1-C)*(1-I)*(1-A))
f(Impact) = 0 if Impact = 0, 1.176 otherwise.
```
### End score

```text
BaseScore = roundToOneDecimal(( (0.6*Impact) + (0.4*Exploitability)-1.5) * f(Impact))
```

## Resources

* [NVD CVSS v2 Calculator](https://nvd.nist.gov/vuln-metrics/cvss/v2-calculator)
* [NVD CVSS v3 Calculator](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator) 
