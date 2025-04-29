# 📝 REDCap Hook: `redcap_survey_complete`

**Available since**: REDCap 5.11.0  
**Returns**: `void`  
**Execution point**: Immediately after survey completion (backend)

## 🧠 Purpose
Use this hook to:
- Process survey results backend immediately
- Trigger automated workflows
- Update external databases
- Initiate notifications based on completed responses

> ⚠️ **Important**:  
> Use `redcap_survey_acknowledgement_page` if you want to **modify page output** after survey completion.  
> This hook is backend-focused and runs during potential redirects.

## 🧾 Parameters
- `$project_id` — project ID
- `$record` — record name (or `NULL`)
- `$instrument` — form unique name
- `$event_id` — event ID
- `$group_id` — DAG ID (or `NULL`)
- `$survey_hash` — public survey hash
- `$response_id` — response ID (or `NULL`)
- `$repeat_instance` — repeat instance (default `1`)

## 🧪 Examples

### Example 1 – Project-Specific Logic
```php
function redcap_survey_complete($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    switch ($project_id) {
        case 212:
            // Project 212 custom processing
            break;
        case 4775:
            // Project 4775 custom processing
            break;
    }
}
```

### Example 2 – Sandboxed Per-Project Handler
```php
function redcap_survey_complete($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_survey_complete.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

### Example 3 – Redirect Participant After Survey Completion
```php
// Inside /hooks/pid1256/redcap_survey_complete.php
if ($instrument == 'diabetes_questionnaire') {
    redirect("https://mywebsite.edu/redcap/plugins/process_questionnaires.php?record=" . $record);
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
