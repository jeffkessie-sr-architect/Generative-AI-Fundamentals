# Defense in Depth for Production AI Agents on Databricks


# 1. The Challenge

A production AI agent needs multiple layers of protection to ensure it is secure, safe, and properly monitored.

A single security feature is not enough. Different layers must address different risks, including:

**Unauthorized access to data and resources.**
**Harmful or inappropriate AI-generated content.**
**Exposure of sensitive information (PII).**
**Lack of visibility into AI activity.**
**Missing security policies and risk controls.**

# 2. The Four Security Layers

## A. Unity Catalog – Access Control and Lineage

Unity Catalog manages access to data and other governed resources.

It helps organizations:

**Control who can access data.**
**Apply permissions and security policies.**
**Track data lineage.**
**Understand where data comes from and how it is used.**

Purpose: Protect data and control access.

## B. Unity Gateway Guardrails – Runtime Safety

Unity Gateway guardrails help protect AI applications while they are running.

They provide safeguards such as:

**Filtering harmful content.**
**Detecting personally identifiable information (PII).**
**Applying runtime safety checks.**

Purpose: Prevent unsafe content and protect sensitive information.

## C. Inference Tables – Auditing and Monitoring

Inference tables capture information about model requests and responses.

They help teams:

**Record model inputs and outputs.**
**Review AI interactions.**
**Investigate unexpected behavior.**
**Monitor production activity.**
**Support auditing and troubleshooting.**

Purpose: Maintain visibility into AI activity.

## D. Databricks AI Security Framework (DASF) – Risk Management

DASF provides a structured framework for identifying and managing AI security risks.

It helps organizations:

**Identify potential AI security threats.**
**Understand vulnerabilities.**
**Map risks to appropriate controls.**
**Establish security practices across the AI lifecycle.**

Purpose: Organize and manage AI security risks and controls.

# 3. How the Four Layers Work Together

Each layer addresses a different security responsibility.

        +----------------------------------+
        |       PRODUCTION AI AGENT        |
        +----------------+-----------------+
                         |
                         v
        +----------------------------------+
        |         UNITY CATALOG            |
        |                                  |
        |  Access Control & Data Lineage   |
        +----------------+-----------------+
                         |
                         v
        +----------------------------------+
        |        UNITY GATEWAY             |
        |                                  |
        |  Runtime Guardrails              |
        |  Harmful Content Filtering       |
        |  PII Detection                   |
        +----------------+-----------------+
                         |
                         v
        +----------------------------------+
        |        INFERENCE TABLES          |
        |                                  |
        |  Record Inputs and Outputs       |
        |  Audit and Monitor Activity      |
        +----------------+-----------------+
                         |
                         v
        +----------------------------------+
        |   DATABRICKS AI SECURITY          |
        |       FRAMEWORK (DASF)           |
        |                                  |
        |  Risk Identification             |
        |  Security Controls               |
        +----------------------------------+


**Note: This is a conceptual view of the security layers, not a required execution sequence. DASF provides guidance across the entire AI lifecycle.**

## Official Databricks AI Security Framework

- [Databricks Agentic AI Security](https://www.databricks.com/sites/default/files/2026-03/databricks-security-framework_0.pdf)

- [Databricks AI Security Framework](https://www.databricks.com/sites/default/files/2025-02/databricks-ebook-dasf-2.pdf)


# 4. Why Defense in Depth Matters

Using multiple security layers helps prevent one security weakness from compromising the entire application.

For example:

Unity Catalog restricts unauthorized data access.
Unity Gateway guardrails help prevent harmful outputs and sensitive information exposure.
Inference tables provide records for investigation and auditing.
DASF helps teams identify risks and select appropriate security controls.

Together, these capabilities provide broader protection throughout the AI application lifecycle.

# 5. Conclusion

Remember the four responsibilities:

Unity Catalog = Access and lineage
Unity Gateway = Runtime safety and PII detection
Inference Tables = Audit and monitoring
DASF = Risk catalog and security controls
