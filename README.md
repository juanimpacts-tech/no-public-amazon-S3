# no-public-amazon-S3

**Purpose**
I built this project to prevent the accidental creation of **public AWS S3 buckets**, one of the most common and dangerous cloud misconfigurations. Using **Policy-as-Code** with **Rego**, **Conftest**, and **GitHub Codespaces**, I wrote and tested a simple policy that blocks any S3 bucket configured with public read access.

**Why I Did This**
Public S3 buckets can leak sensitive data to the entire internet with a single misconfiguration. I wanted a lightweight, automated safeguard that catches this risk **before it reaches production**.
My goal was to give developers fast feedback, reduce human error, and provide compliance teams with assurance that data storage remains private by default.

**What I Learned**

* How Policy-as-Code works in practice
* How to write a **Rego** policy to block risky configurations
* How to test infrastructure code quickly using **Conftest** in Codespaces
* How to map a technical policy directly to compliance controls like **NIST AC-6(10)** and **SC-12**

**How I Did It**

1. **Created a GitHub repo** and added three files:

   * `input.json` – sample S3 config with `"acl": "public-read"`
   * `policy/input.rego` – policy that denies public-read buckets
   * `conftest.toml` – test configuration
2. **Opened the repo in GitHub Codespaces** for a no-setup environment
3. **Tested the policy** with:

   ```bash
   conftest test input.json --all-namespaces
   ```

   ✅ Saw the violation flagged
4. **Fixed the misconfiguration** by changing `"acl": "private"`
5. **Re-tested** to confirm the policy passed

**The Outcome**

* An **automated guardrail** preventing public S3 buckets
* A **quick feedback loop** for developers
* A clear compliance mapping to:

  * **AC-6(10)** – Automated enforcement of least privilege
  * **SC-12** – Prevention of unauthorized public access
    i. AC-6(10) – Automated enforcement of least privilege.
    ii. SC-12 – Prevention of unauthorized public access.
