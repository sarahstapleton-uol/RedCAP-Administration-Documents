Data Analysis Beyond REDCap

1.0 The REDCap platform enables users to export data with a simple interface, but customised exports are also possible. This section will introduce each of them and provide a basic level example of how to export data.
There are two major approaches to data exports: 

	1.1 web interface (menu + click option)

	1.2 API (programmatic access for automation or scripts)

It should be noted at this point that the ability to export data is dependent on the user’s individual rights or permissions as per REDCap records in ‘ Users.’ These priveleges adhere to general software anonymisation standards, such that first and last names are removed, numeric identifiers (house number, Date of Birth, faetal heart rate), and other data. The aim is to deidentify every record, which may also be supplemental to ‘hidden’ fields, where a user has only limited rights. And this is especially true when exporting a full dataset, which requires the highest level of permissions. Verify that you have used an HTTPS request and observe DAG rules that govern the no. of exports.

1.1.1 There are various ways of approaching data export as a user intending to export data. Your requirements and intentions, as well as project governance, could restrict which data is exported on a user-to-user basis. Each administrator must evaluate their personnel and assume responsibility for operating under GDPR, which preferences access to data required only to fulfil a specific purpose and for within the allotted timeframe. 

The most common approaches to exporting data are as follows;
A complete, all fields/columns and all entries/rows, project dataset
Custom reports built by users from within the interface; for example, a dataset contains variables ‘species’, ‘breed’, ‘age’, ‘diagnosis’ from which the user only requires breed and diagnosis to answer the question raised by the Principal Investigator: ‘What are the most common reasons for admission to the surgery per breed?’

The metadata, referred to as a Data Dictionary in REDCap; some computer scientists describe this term as meaning, ‘data about data’, which can be surprisingly useful resource at times.

File attachments, such as those uploaded to REDCap as a storage space and later removed to a permanent archive. For example, a patient gives consent for their biological data to be transferred to a laboratory outside the UK for analysis with an electronic signature in a .pdf. This document must be preserved to attest to ethical, as well as respectful, recognition of the patient’s right to exercise ownership of their biological data, sometimes far in excess of the duration of the research project.  

1.1.2.1 Example: REDCap Web Interface 
The examples that follow use a single approach to the export of the data type mentioned. There are often multiple possibilities to perform a functionality within the environment.

1.1.2.2 The Dataset
Follow the main menu available from within the project. Go to 

(a) Project Home → From the Applications the Menu (Margin) → Data Exports, Reports, and Stats.
(b) Choose Export Data
(c) Select the required format from .csv, .r., .xml., .sas, .json

1.1.2.2 Example: Custom Reports
Follow the main menu available from within the project. Go to 

(a) Project Home → From the Applications the Menu (Margin) → Data Exports, Reports, and Stats.
(b) Select the custom report from the entry in the left-hand side margin
(c) Choose Export Data

OR at step (b)

(bi) Select Create New Report → Select Required Fields  → Filter (event, instrument, other) 
(bii) Select a custom arrangement for the data; choose a layout for variables, make a Group
(c) Choose Export Data (+1.1.2.2.c )

1.1.2.3 Example: The Metadata
Recall that this Area reports the ‘data about data’, which is a useful description that offers a guiding principle when thinking about this Resource. This export will produce the logic behind your dataset’s calculations across multiple fields, encode the type of option available to the patient through the survey, expose weaknesses in survey linkage and groupings, as well as state the equivalence between machine-readable variables and the corresponding human-readable text fields. There are many other uses and applications of this important fields and it is one which should be explored by administrators in conjunction with an individual with suitable expertise.

Change the content parameter in an API call to content=metadata, which is true for exporting a report by its ID (usually a name entered to a text fields) or user behaviours. The table below provides an example of how this might look in your script.

Data Fields	    Command
Metadata	-d "content=metadata"
Report	    -d "content=report" -d “report_id=xyz123"
File	    -d "content=file" -d "record=1" -d "field_name=upload_field"
Users	    -d "content=user"

1.1.2.4 Example: Application Programming Interface (API) 
An API represents the highest possible level of control over the data. Its programmatic strengths include the import and export of data that are particularly suitable for automation of analysis workflows. An administrator is solely responsible for API key authorisation. The access permitted is unrestricted, controlled by any individual with an API key. These unique alpha-numeric strings are constructed in chunks of 52 randonly generated Latin and Arabic characters with some common symbols (@, #, &). The user who has an API Key must have knowledge of how to store the key securely, and how to enable the script to read it; it should never be written into the code. 

The scripts are accepted in Python, R or Bash as follows:

1.1.2.4. A Simple API Command to Request Data is Exported using cURL
curl -X POST \
  -d "token=YOUR_API_TOKEN" \ # NB: Guidance Notes (1.1.2.4)
  -d "content=record" \
  -d "format=csv" \
  -d "type=flat" \
  -d "rawOrLabel=raw" \
  -d "exportCheckboxLabel=false" \
  -d "returnFormat=json" \
  https://YOUR_REDCAP_URL/api/



Parameter	        Description
token	            Requires a unique API token
content=record	    Exports record-level data (see also 1.1.2.3)
format=csv	        File format (csv, json, xml)
type=flat	        One row per record
rawOrLabel	        Use label for human-readable data
returnFormat	    Response format for errors (json, xml)

1.1.2.4.B Python code to Request Data using a URL

import requests
import pandas as pd

url = 'https://ENTER_PROJECT_URL_IN_REDCAP/api/'
data = {
    'token': 'UNIQUE_API_TOKEN',
    'content': 'record',
    'format': 'csv',
    'type': 'flat',
    'rawOrLabel': 'label',
    'returnFormat': 'json'
}

response = requests.post(url, data=data)
df = pd.read_csv(pd.compat.StringIO(response.text))
print(df.head())

1.1.2.4.c Additional Information

It is interesting to note that while customised reports are built and tested in the user’s interface, those report IDs can become references in an API ‘call’ for automated requests to the server

-d "content=report" \
-d “report_id=47" \
-d "format=json"

