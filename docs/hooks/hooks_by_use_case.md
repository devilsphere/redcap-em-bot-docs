# 🗂️ Choosing the Right REDCap Hook: Developer Use Case Guide

This guide organizes REDCap hooks into categories based on **common developer scenarios**.

---

## 📄 Survey Lifecycle Hooks
Use when **manipulating surveys** or **survey responses**:

| Hook | Purpose |
|:-----|:--------|
| [`redcap_survey_page`](redcap_survey_page.md) | Modify or inject content at the bottom of a survey page |
| [`redcap_survey_page_top`](redcap_survey_page_top.md) | Modify or inject content at the top of a survey page |
| [`redcap_survey_complete`](redcap_survey_complete.md) | Perform actions immediately after a survey is submitted (before redirect) |
| [`redcap_survey_acknowledgement_page`](redcap_survey_acknowledgement_page.md) | Modify the survey Thank You page (after survey completion) |

---

## 🛠️ Form & Record Management Hooks
Use when **working with data entry forms** or **saving records**:

| Hook | Purpose |
|:-----|:--------|
| [`redcap_add_edit_records_page`](redcap_add_edit_records_page.md) | Modify the Add/Edit Records page |
| [`redcap_data_entry_form`](redcap_data_entry_form.md) | Modify data entry form pages (excluding surveys) |
| [`redcap_save_record`](redcap_save_record.md) | Perform actions immediately *after* a record is saved (both forms and surveys) |

---

## ⚙️ Administrative & Backend Process Hooks
Use when **modifying REDCap platform-level pages**:

| Hook | Purpose |
|:-----|:--------|
| [`redcap_control_center`](redcap_control_center.md) | Modify the Control Center pages |
| [`redcap_user_rights`](redcap_user_rights.md) | Modify the User Rights page |
| [`redcap_project_home_page`](redcap_project_home_page.md) | Modify the Project Home page inside projects |

---

## 🌐 Global Application-Wide Hooks
Use when **affecting every page** in REDCap:

| Hook | Purpose |
|:-----|:--------|
| [`redcap_every_page_top`](redcap_every_page_top.md) | Inject content at the very top of every page |
| [`redcap_every_page_before_render`](redcap_every_page_before_render.md) | Backend operations before any page renders |

---

## ✉️ Messaging and File Handling Hooks
Special use cases for **email and PDF operations**:

| Hook | Purpose |
|:-----|:--------|
| [`redcap_email`](redcap_email.md) | Intercept or modify outgoing emails |
| [`redcap_pdf`](redcap_pdf.md) | Intercept or modify PDF content generation |

---

✅ *Remember:* Hooks **require** a Hook Functions PHP file to be properly configured in your REDCap Control Center.

---
