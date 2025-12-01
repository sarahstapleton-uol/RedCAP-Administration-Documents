#### Checklist

1. Before you create the project

 Clarify the study purpose (audit, survey, RCT, registry, etc.).

 Decide if the project is Classic or Longitudinal (events, arms, repeated visits?).

 Decide if you will use surveys, forms (data entry), or both.

 Agree the core variables: IDs, outcomes, key exposures, dates, consent fields.

 Check local governance / approvals (ethics, DPO, data custody, retention).

 Decide the record ID structure (auto-number or meaningful IDs).

 Identify who needs access (PI, data entry, statistician, external collaborators).

2. Create the REDCap project

 Create a new project (use a template if your institution has one).

 Set project type: Classic vs Longitudinal; enable Arms/Events if needed.

 Give the project a clear title, purpose, and PI details.

 Leave the project in Development mode (do not move to Production yet).

3. Building instruments – Option A: Online Designer (no data dictionary)

 Open Online Designer.

 Create instruments (forms/surveys) with clear names (“Baseline Form”, “4M Follow-up”).

 For each field:

 Choose a variable name (short, meaningful, no spaces).

 Write a clear field label (what the user sees).

 Select appropriate field type (text, radio, dropdown, checkbox, calc, file upload).

 Add validation where needed (date, integer, email, number).

 Add field notes for instructions (units, format, etc.).

 Add branching logic if the field should appear conditionally.

 Mark any instruments that should be surveys and configure basic survey settings (title, instructions, thank-you text).

4. Building instruments – Option B: Using a Data Dictionary (CSV)

 Download the Data Dictionary (empty or template) from the project.

 Edit the CSV in Excel or similar (one row per field):

 Define variable_name, form_name, field_type, field_label.

 Add choices, calculations, OR slider labels for categorical and calc fields.

 Add branching_logic as REDCap logic (e.g. [age] >= 18).

 Specify text_validation_type_or_show_slider_number where needed.

 Check for typos in variable names and duplicate names.

 Save as plain CSV (not xlsx).

 Upload the data dictionary back into REDCap and fix any reported errors.

5. Hybrid approach – supplementing / customising an existing dictionary

 Import the base data dictionary provided by your institution or collaborator.

 Download the current dictionary again before editing (to avoid overwriting changes).

 Add new rows for custom fields/instruments at the bottom or grouped by instrument.

 Clearly distinguish local-only items (site_specific_…).

 Re-upload and check for errors/logic conflicts.

 Avoid major structural changes (removing key variables) once data collection has started.

6. Project configuration & governance

 In Project Setup, configure:

 User Rights and assign roles (PI, data entry, statistician).

 Data Access Groups (DAGs) if multi-site.

 Randomization Module if applicable.

 Logging (ensure it is enabled, it usually is by default).

 Configure Surveys:

 Enable Public Survey if needed.

 Set up Survey Queue and/or Auto-Survey Invitations (timed or logic-based).

 Set RECORD ID field and auto-numbering options.

 Check data export rights for each role (full, de-identified, none).

7. Testing the project (before going live)

 Create several test records (include edge cases: very old/young ages, extreme values).

 Test branching logic:

 Confirm fields appear/disappear under the right conditions.

 Test calculated fields and date differences:

 Verify results manually for a few examples.

 Test surveys from a participant’s perspective:

 Use survey links (public and/or invitations).

 Check wording, layout, required fields, progress indicators.

 Test survey flow:

 Survey Queue order.

 Auto-Survey Invitations (trigger conditions & timing).

 If longitudinal:

 Confirm instruments are assigned to the correct events/arms.

 Enter test data across multiple time points.

 Run Data Quality Rules on test data to see if any rules need tweaking.

 Test exports (CSV, R, etc.) to ensure variables and labels look correct.

 Document any design decisions / quirks in a project README or “Notes” instrument.

8. Moving to Production

 Remove test records (or mark/lock them and exclude them from analysis).

 Confirm all stakeholders (PI, data manager, statistician) sign off the design.

 In Project Setup, request move from Development to Production.

 Read the warning about structural changes in Production; accept if ready.

9. During data collection – maintenance

 Monitor Logging periodically for unexpected activity (bulk edits, deletions, exports).

 Review Data Quality Rules regularly and correct errors/missingness.

 Maintain User Rights – add/remove users as staff join/leave.

 If Production changes are needed:

 Make edits in Draft Mode.

 Test on a few records (or a sandbox project) before applying to live data.

 Back up key exports periodically (secure storage, respecting governance).

 Use Form Status and reports to monitor completeness.

10. Exporting data to Excel

 Open Data Exports, Reports, and Stats.

 Create a Report (select instruments, fields, filters).

 Choose Export Data → CSV (Excel compatible).

 Decide on de-identification options (remove IDs, dates, free-text if needed).

 Export and open in Excel; check:

 Column names (variable names) and labels.

 Coding of categorical fields (e.g. 1, 2, 3 vs labels).

 Date formats (may need conversion in Excel).

11. Exporting data to R

 From the same Export page, select R (statistical software) export.

 Download:

 The CSV data file.

 The R script (.R) that maps labels and types.

 In R:
 
 source("your_redcap_export_script.R")   # loads data and applies labels

 Check that:

 Factor levels correspond to the codebook (dropdown/checkbox options).

 Dates imported as Date (or convert with as.Date).

 Missing values (NA) correctly represented.

 Optionally build a codebook in R from the Data Dictionary for reference.

12. Project closure / archiving

 Confirm all planned data collection is complete.

 Run final Data Quality checks and resolve outstanding issues.

 Export final datasets (R + CSV) and store in approved secure location.

 Export or save the Data Dictionary and any project documentation.

 Lock or archive the project according to local policy (don’t delete unless instructed by governance).

