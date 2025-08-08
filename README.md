# no-public-amazon-S3
Built a lightweight security check that prevents teams from accidentally creating public AWS S3 buckets, a common and dangerous cloud misconfiguration. Doing so this using policy as code with Rego, Conftest, and GitHub Codespaces. In doing so (1) Wrote a security policy in code; (2) Evaluated real IaC (Terraform) against it; and (3) Got a policy-as-code enforcement result

**Compliance Mapping**
This policy directly addresses critical security and compliance objectives by satisfying the following NIST SP 800-53 controls:

AC-6(10) – Automated enforcement of least privilege: This policy ensures that permissions for data storage are automatically restricted to the absolute minimum necessary. By preventing public access to storage buckets, it directly enforces the principle of least privilege, reducing the attack surface and mitigating risks associated with over-privileged access. This automated enforcement minimizes the potential for human error in configuring access controls.

SC-12 – Preventing unauthorized public access: The core of this policy is to eliminate the possibility of data being unintentionally exposed to the public internet. By strictly prohibiting public buckets, it acts as a preventative measure against unauthorized disclosure of sensitive information. This control is vital for maintaining data confidentiality and integrity, protecting against data breaches, and ensuring compliance with privacy regulations.
