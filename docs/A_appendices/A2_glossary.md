ALERTS & NOTIFICATIONS

A REDCap module that sends automated emails/app messages according to certain specified conditions; including abnormal lab results, upcoming visit dates, missing data. Logic is usually based on field values, events, or dates.

API

The REDCap Application Programming Interface. External scripts or systems (R, Python, SAS) can programmatically read from, and write to, a REDCap project using HTTPS requests.

API TOKEN

A project-specific, user-specific secret key that authenticates a REDCap API. The token only grants the associated user’s level of access for that specific project. Secure storage of the API Key is imperative.

ARM

In a longitudinal REDCap project, an ARM is a group of events that represent a distinct pathway or cohort. Typically, they would be be called 'Control Arm', or Intervention Arm' and similar, so that different ARMS hold unique sets of events and schedules.

AUTO-NUMBERING

A project option: REDCap automatically assigns sequential numeric RECORD IDs, which can be used as a Primary Key. It is recommended so that the project does not contain duplicate entries.

AUTO-SURVEY INVITATIONS

Automatically send survey invitations according to pre-defined, project logic and time-codes, such as a second survey at a new time point. 

BRANCHING LOGIC

Conditional logic controls whether a field or survey question is shown to a participant according to answers already received; an example is not to request information about the menopause from a man, i.e. SEX = female.

CALCULATED FIELD

A field with automatic calculations; for example, BMI, age in years. This facility uses REDCap’s functions like if(), datediff(), and arithmetic expressions.

CHECKBOX FIELD

A field type that allows multiple selections from a list of options. In the data dictionary and exports, each option is stored as a separate 0/1 variable.

CLASSIC PROJECT

A project type where all data collection occurs in a single 'wave' with no longitudinal structure. This project does not have arms or events, since they are unecessary, and correspond only to a single event.

DATA ACCESS GROUP (DAG)

A mechanism to restrict which records users can access, implemented when all records are assigned to a DAG and a DAG is created for a user group; for example, Ward Nurse, Consultant.

DATA COLLECTION INSTRUMENT

A structured form or survey that holds questions known as fields. Instruments could be case report forms or participant-facing surveys.

DATA DICTIONARY

A CSV file that defines all fields in a REDCap project: variable names, labels, field types, choices, branching logic, calculations, and validations. It is an editable and downloadable document.

DATA EXPORT TOOL

The internal, platform module that is responsible for the download of project data in multiple formats including CSV, SPSS, Stata, and R. There are de-identification options as well as defined user permissions and DAG restrictions.

DATA IMPORT TOOL

Larger batch uploads are permissible using the DATA IMPORT TOOL as well as updates to existing REDCap data via CSV. The file must use correct variable names and record IDs; REDCap validates and reports errors or mismatches.

DATA QUALITY RULES

Configurable checks that scan project data for potential problems and which outline the importance of clearly defined structure to a project that recognises field entries that out of scope/range, illogical entries and inconsistencies, in additio to missing required fields. Review and repair by the user are peritted.

DOUBLE DATA ENTRY

A project is configured from two independent users who enter identical data that requires discrepancies to be compared and resolved at a later stage; useful for data accuracy.

E-CONSENT

REDCap instruments/surveys include the option to obtain electronic informed consent, which could also include PDF creation, signatures, and regulatory or internal compliance workflows.

EVENT

A time point or milestone in a longitudinal project. Instruments are assigned to events to define which forms are considered complete.

EXTERNAL MODULE

An extendable, plug-in component that adds new functionality to REDCap. They are able to offer integration with other systems, and custom dashboards. They must be managed by administrators and enabled per project.

FIELD

The basic data element in REDCap (equivalent to a variable or question). Each field has a name, label, type, and optional logic/validation.

FIELD LABEL

The human-readable text shown to users or participants for a field. It is distinct from the underlying variable name and exports of raw data will not include these labels.

FIELD NOTE

Helper text displayed under a field to provide additional instructions or clarifications (DD/MM/YYYY format).

FIELD VALIDATION

To verify that type/format of data is entered as specified into a field.

FORM STATUS

An indicator to make plain the completion status of an instrument with names such as Unchecked, Incomplete, or Complete. They are useful for tracking progress and that the record is completed in-full.

INSTRUMENT

A REDCap data collection form or survey. Instruments are built in the Online Designer or data dictionary and can be used as internal forms or participant surveys.

LONGITUDINAL PROJECT

A project with data collected at multiple time points (events), possibly organized into arms, useful for schedules, repeated measurements, and complex designs.

LOCKING

A feature that prevents further editing of records or forms used predominantly in clinical trials. Useful combination with electronic signatures.

MOBILE APP

The REDCap mobile application that allows offline data collection on tablets/phones and later synchronization to a central REDCap server. Useful for fieldwork or low-connectivity settings.

ONLINE DESIGNER

The web-based interface for creating and editing instruments, fields, and branching logic directly, without editing the CSV data dictionary.

PARTICIPANT IDENTIFIER

A field used to store a subject’s or participant’s ID. It can be very useful for de-identification and privacy policies.

PIPING

Insertions of prior data field values into question text, survey headers, or personalization of messages.

PROJECT

A self-contained REDCap database with its own instruments, users, records, and settings. Each study, registry, or survey implementation is typically one project.

PROJECT ID

The numeric identifier assigned by REDCap to each project (“Project 123”). Used internally and in URLs and APIs to reference a specific project.

PROJECT SETUP

The configuration area where project settings are defined: type (classic/longitudinal), arms/events, randomization, surveys, user rights, and general options.

RANDOMIZATION MODULE

The random allocation of records to groups (treatment vs control) is automayed according to a predefined randomization scheme, often stratified or blocked.

RECORD

A unit of observation in a REDCap project, usually representing a participant, subject, or case. In longitudinal projects, one record spans multiple events.

RECORD ID

The unique primary key for each record (1001, PT-047). This is the first field in the project and is required; all databases require a primary key unique identifier for a record. It links all instruments and events for a given subject.

REPEATING EVENT

A longitudinal event configured to repeat multiple times for a single record, such as routine dialysis or insulin dosage reviews. 

REPEATING INSTRUMENT

Multiple use instruments within single events: adverse effects each require a distinct index. 

ROLE

A reusable set of user-rights settings that can be assigned to multiple users. Simplifies management of permissions consistently.

SCHEDULING MODULE

A tool for generating and managing visit schedules for participants in longitudinal projects, based on events and optional offset/visit windows.

SERVER

The physical or virtual machine where REDCap is installed and hosted. Managed by local IT; responsible for security, backups, storage.

SURVEY

A participant-facing version of an instrument, accessed via public or private links. Surveys can be anonymous and can be used for data collection without user login.

SURVEY INVITATION LOG

A log showing all scheduled, sent, and completed survey invitations, including timestamps, recipients, and status.

SURVEY LOGIN

An optional mechanism requiring participants to authenticate their identity before accessing a survey, used for non-anonymous or secure workflows.

SURVEY QUEUE

A feature that displays multiple surveys in sequence to a participant, based on logic and completion status.

TOKEN

In REDCap context, the token usually refers to the API token or survey access token: a unique code used to securely access a survey or the API.

USER RIGHTS

The module where administrators define which projects users can access and what they can do; view, edit, export, design, randomise, admin rights and others.

VARIABLE NAME

The unique, machine-readable name (bp_sys, bi_cons1) given to a field and visible in data exports and the data dictionary. 

VARIABLE TYPE

The classification according to a REDCap field type (text, dropdown, radio, checkbox, calculated, file upload) and/or validation (date, integer, email).