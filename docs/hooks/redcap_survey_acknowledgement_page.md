# ✅ REDCap Hook: `redcap_survey_acknowledgement_page`

**Available since**: REDCap 10.2.0  
**Returns**: `void`  
**Execution point**: After survey completion and acknowledgement text is displayed

## 🧠 Purpose
Use this hook to:
- Display custom messaging after survey completion
- Trigger backend processes
- Redirect users to custom URLs
- Modify acknowledgement page with additional HTML, JavaScript, or CSS

## 🧾 Parameters
- `$project_id` — project ID
- `$record` — record name (may be `NULL`)
- `$instrument` — instrument unique name
- `$event_id` — event ID
- `$group_id` — DAG ID (or `NULL`)
- `$survey_hash` — survey hash (unique to each public survey)
- `$response_id` — survey response ID (or `NULL`)
- `$repeat_instance` — repeat instance number (default `1`)

## 🧪 Examples

### Example 1 – Static Announcement
```php
function redcap_survey_acknowledgement_page($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    print '<div class="yellow">Special announcement text to display right below the survey acknowledgment text.</div>';
}
```

### Example 2 – Project-Specific Logic
```php
function redcap_survey_acknowledgement_page($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    switch ($project_id) {
        case 212:
            // custom thank-you actions
            break;
        case 4775:
            // another project's actions
            break;
    }
}
```

### Example 3 – Sandboxed Per-Project Handler
```php
function redcap_survey_acknowledgement_page($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_survey_acknowledgement_page.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

### Example 4 – Redirect Participant After Survey
```php
// Inside hooks/pid1256/redcap_survey_acknowledgement_page.php
if ($instrument == 'diabetes_questionnaire') {
    redirect("https://mywebsite.edu/redcap/plugins/process_questionnaires.php?record=" . $record);
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
