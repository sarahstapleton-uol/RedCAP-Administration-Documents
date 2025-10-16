REDCap: Architecture

Introduction to REDCap Architecture for Administrators
REDCap (Research Electronic Data Capture) software was developed by Vanderbilt University, USA, as a web application to enable researchers in healthcare (primarily) to store data securely, in abeyance of regulations. It is designed to manage the clinical research environment effectively (skip to section 5 for the ‘Administrator’s responsibilities’). It has multiple layers, definitions in the table below:

Layers with a Description
Client (Front-end):	Web browser interface (HTML, JavaScript, PHP) used by researchers, data entry personnel, and adminstrators
Application Server:	A PHP codebase (REDCap software). User authentication, form rendering, data entry logic and audit trails are managed at this point.
Database Server:';	MySQL or MariaDB store the metadata and research data.
File System / Storage:	A secure repository of all documentation uploaded, instances of data exports logs, activity logs and certain configuration files.
Web Server:	An example of this is Apache and it manages HTTPS requests (as implemented by API calls) and enforces data SSL/TLS encryption.

2. System Architecture and Data Flow
In a nutshell, the process is as follows:

-- A User connects via web-browser using the HTTPS 
-- The Web server sends the request to the REDCap PHP engine
-- REDCap’s Application logic enforces pre-determined user roles and permissions granted
-- The REDCap Database records, replies and updates data in a secure environment
-- Audit logs record every login attempt, data edits, and exports (exported using API calls)

2.1 Security Controls
This section records the security controls in effect on the REDCap database. The project administrator would not be expected to have detailed knowledge about the implementation of security on REDCap and it is included here as a reference guide. However, the main point is that a database has restricted access, which is enforced, managed and defended using the tools and techniques described below. (2.1.A - 2.1.B)

2.1.A. Network & Server Security

Various structural and technical configurations govern the 

-- TLS/SSL: In an HTTPS web Connection, all communication with the server is encrypted
-- The server is ‘Hardened’: Operating Software ((OS) repair bugs) patches, SSH access requirements and firewalls defences
-- Distinct sub-sections of project environments: Systems Administrators use the terms ‘Development’ (‘Dev’), ‘Test’ and ‘Production’ (‘Prod’) to talk about sub-sections 
-- Institutional authentication (SSO, Shibboleth, username/password combinations): privacy

2.1.B. Application-Level Security

Role-based permissions are granular and determined by the project administrator or other project personnel who hold significant responsibilities for the ethical considerations of information governance. The options available are;

-- Two-factor authentication (2FA) compatibility
-- Default logouts for idle sessions 
-- SQL Injection Attacks are notoriously harmful and could occur unless input is sanitized to prevent it; data is validated using internal logic rules to prevent this and other harmful cyber attacks
-- A core component of a PHP framework is CSRF and XSS protection

2.1.C. Data Security within the REDCap Environment

-- Protection of all data using institutional firewalls
-- A simple click of a mouse de-identifies or encodes data before it is exported 
-- Any files uploaded are transferred to a secure location beyond the reach of malicious hackers who access via the web’s root
-- All actions are recorded; this means that records created, edited, exported and stored are auditable; for example, all logins receive a timestamp when the user accesses the project's pages 
-- A full database backup (MySQL/Maria DB) can be enforced mandatorily by REDCap. This is achieved by creating 'mysqldump' or 'mariabackup' jobs using either an institution's internal backup systems or Cron jobs that will also automate them. This data can be stored in a secure, external archive, weekly/daily.

3. User Access Controls

Access Element	                : Description of Access Element Terms
User Rights: Each user has specific access rights at the             project level; data entry, design, export, reports, et cetera.
Roles and Role Templates:	    : Pre-defined permissions are set for consistency across users/projects.
User Access Dashboard	        : Administrators can monitor active users, last login, and privileges.
Record Locking / E-signatures:	Optional workflow control for data verification.
Data Access Groups (DAGs)	    : Isolate subsets of records to specific user groups (such as maintaining seperate sections for data if it is captured at multiple sites, including hospitals/community)
Project Ownership           	: PI or data steward responsible for user access and audit compliance
API Token Permissions       	: Per-user, per-project tokens; access is restricted to specific API endpoints and roles

4. Compliance and Governance

You will have heard about, and probably enforce, a number of data and information governance principles. Within the demands of our roles and responsibilities, sometimes matters are overlooked, or fail to receive prioritisation as a result of conflicts. To that end, a simple checklist could look like this:

-- HIPAA / GDPR alignment 
-- Logging and Auditing: export logs regularly for monitoring/compliance reporting
-- Design and implementat data retention policies: a patient’s consent, inheritable disease risks ... 
-- External modules compatibility with institutional guidelines and digital signatures can introduce conflicts and should be monitored when central operating policies alter to affect new business considerations

5. An Administrator’s Responsibilities

1. User provisioning and access controls (via LDAP, local, or SSO) to be managed
2. Audit logs and usage reports are regularly monitored 
3. Maintain REDCap and Operating Software Security updates 
4. (Typically) Enforce a ‘least amount of viable privileges’ approach that won’t restrict work 
5. Coordinate with the Database Administratot for assistance with secure backup procedures and testing that a restored database is performing correctly D
6. Prior to activating any additional, external modules or an API call, ensure to validate the data, backup and restoration. This step is a critical point in audit logs and should be retained. 

In effect, REDCap’s architecture separates application logic, data storage, and access control layers, providing multi-level security (network, system, application, user). Administrators govern access requirements via role-based controls, DAGs, audit logs, and institutional authentication, ensuring data integrity and regulatory compliance.





