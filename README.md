1. Client Summary: Artemis Financial

Client: Artemis Financial, a financial services company specializing in investment and wealth management solutions.

Software Requirements: Artemis Financial needed to modernize their web application to ensure secure data transmission and protect sensitive customer financial information. The specific issues they wanted addressed included:
- Implementing secure communication channels (HTTPS instead of HTTP)
- Adding data integrity verification through cryptographic hashing
- Identifying and mitigating known software vulnerabilities
- Ensuring compliance with financial industry security standards (GDPR, FTC Safeguards Rule)

2. What I Did Well & Importance of Secure Coding

What I did well: When identifying software security vulnerabilities, I effectively used the OWASP dependency-check tool to scan for known vulnerabilities in third-party libraries. I also successfully identified that the application was using HTTP instead of HTTPS, which exposed sensitive data to potential interception.

Why secure coding is important: Secure coding prevents data breaches, protects customer privacy, maintains regulatory compliance, and safeguards company reputation. A single vulnerability can lead to millions in losses, legal liability, and irreversible damage to customer trust.

Value to company's well-being: Software security directly protects:
- Customer financial data (PII, account numbers, transaction history)
- Regulatory compliance (avoiding fines and legal action)
- Business continuity (preventing downtime from attacks)
- Brand reputation (maintaining customer confidence)

3. Challenging and Helpful Parts of the Vulnerability Assessment

Challenging: The most challenging part was understanding how to properly generate and configure a self-signed certificate for HTTPS, including setting up the correct keystore format (PKCS12) and configuring Spring Boot's application.properties file with the right parameters.

Helpful: The vulnerability assessment process flow diagram was extremely helpful for visualizing the security layers and understanding how each component (cipher selection, certificate generation, dependency checking) fits together in a complete security solution.

4. Increasing Layers of Security & Future Mitigation Techniques

How I increased security layers:
- Layer 1 - Secure Communication: Converted HTTP to HTTPS using TLS/SSL with a self-signed certificate
- Layer 2 - Data Integrity: Implemented SHA-256 cryptographic hashing for checksum verification
- Layer 3 - Static Analysis: Integrated OWASP dependency-check Maven plugin
- Layer 4 - Secure Configuration: Enforced HTTPS redirection and proper keystore settings

Future vulnerability assessment tools:
- SAST Tools: SonarQube, Checkmarx for static code analysis
- DAST Tools: OWASP ZAP for dynamic testing
- SCA Tools: Snyk, Dependency-Track for ongoing dependency monitoring
- Mitigation decision criteria: CVSS scores, exploitability, business impact, and regulatory requirements

5. Ensuring Functionality and Security

Verification process:
- Functional testing: Ran the Spring Boot application and manually tested the `/hash` endpoint to verify SHA-256 checksum generation
- Security testing: Used browser developer tools to confirm HTTPS was active (padlock icon) and HTTP requests were properly redirected
- Vulnerability re-scanning: Ran `mvn dependency-check:check` after refactoring to ensure no new vulnerabilities were introduced

Key verification steps:
```bash
# Run dependency check
mvn clean dependency-check:check

# Run application
mvn spring-boot:run

# Test HTTPS endpoint
curl -k https://localhost:8443/hash
```

6. Resources, Tools, and Coding Practices

Tools used:
- Spring Boot 2.2.4 - Web application framework
- OWASP dependency-check-maven (5.3.0) - Vulnerability scanning
- Java Keytool - Certificate generation
- Maven - Build automation

Coding practices:
- Defense in depth (multiple security layers)
- Secure defaults (HTTPS enforced by default)
- Minimal information disclosure (generic error messages)

Future helpful resources:
- NIST National Vulnerability Database (NVD)
- OWASP Cheat Sheets
- Spring Security documentation

7. What to Show Future Employers

From this assignment, I would showcase:

1. Practices for Secure Software Report - Demonstrates my ability to document security implementations professionally

2. Code Implementation - The SHA-256 hashing endpoint showing cryptographic implementation in Java:
```java
MessageDigest md = MessageDigest.getInstance("SHA-256");
byte[] hashBytes = md.digest(input.getBytes(StandardCharsets.UTF_8));
```

3. Security Configuration - The HTTPS/SSL setup in `application.properties` demonstrating knowledge of TLS configuration

4. Vulnerability Assessment Process - Evidence of using OWASP dependency-check and interpreting results

These artifacts demonstrate my ability to:
- Implement cryptographic solutions
- Configure secure communications
- Perform vulnerability assessments
- Document security practices professionally
- Apply industry-standard best practices (least privilege, defense in depth, secure defaults)

---

 Portfolio Artifact Submitted

☑ Practices for Secure Software Report (Project Two) - Included in repository
