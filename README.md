# no-public-amazon-S3
Built a lightweight security check that prevents teams from accidentally creating public AWS S3 buckets, a common and dangerous cloud misconfiguration. Doing so this using policy as code with Rego, Conftest, and GitHub Codespaces. In doing so (1) Wrote a security policy in code; (2) Evaluated real IaC (Terraform) against it; and (3) Got a policy-as-code enforcement result

# Why I Did This
Public S3 buckets can leak sensitive data to the entire internet with a single misconfiguration, this functions as a lightweight, automated safeguard that catches this risk before it reaches production.

# What I Learned

1. How Policy-as-Code works in practice.
2. How to write a Rego policy to block risky configurations.
3. How to test infrastructure code quickly using Conftest in Codespaces.
4. How to map a technical policy directly to compliance controls like NIST AC-6(10) and SC-12.

# How I Did It
1. Created a GitHub repo and added three files:
2. input.json – sample S3 config with "acl": "public-read".
3. policy/input.rego – policy that denies public-read buckets.
4. conftest.toml – test configuration.
5. Opened the repo in GitHub Codespaces for a no-setup environment.
6. Tested the policy with conftest test input.json --all-namespaces and saw the violation flagged.
7. Fixed the misconfiguration by changing "acl": "private" and re-tested to confirm the policy passed.

# The Outcome
I now have:
1. An automated guardrail preventing public S3 buckets.
2. A quick feedback loop for developers.
3. A clear compliance mapping to:
    AC-6(10) – Automated enforcement of least privilege.
    SC-12 – Prevention of unauthorized public access.
