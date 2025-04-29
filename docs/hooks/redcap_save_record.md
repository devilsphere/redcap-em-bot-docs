# 💾 REDCap Hook: `redcap_save_record`

**Available since**: REDCap 5.11.0  
**Returns**: `void`  
**Execution point**: Immediately after a record is saved (via form or survey)

## 🧠 Purpose
Use this hook to perform actions immediately after a record is created or updated:
- Trigger backend processes
- Send notifications
- Auto-calculate or copy fields
- Implement conditional logic

> ⚡ Executes **during post-processing**, before page render.

## 🧾 Parameters
- `$project_id` — project ID
- `$record` — record name (may be `NULL` when first created)
- `$instrument` — form name (Column B in Data Dictionary)
- `$event_id` — event ID (for longitudinal use)
- `$group_id` — DAG ID (or `NULL`)
- `$survey_hash` — survey hash value (only for surveys)
- `$response_id` — survey response ID (only for surveys)
- `$repeat_instance` — repeat instance (default `1`, added in 7.3.4)

## 🧪 Examples

### Example 1 – Basic Project-Specific Logic
```php
function redcap_save_record($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    switch ($project_id) {
        case 212:
            // Project 212 logic
            break;
        case 4775:
            // Project 4775 logic
            break;
    }
}
```

### Example 2 – Sandboxed Per-Project Handler
```php
function redcap_save_record($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_save_record.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

### Example 3 – Email Alert Based on Survey Response
```php
// In /hooks/pid998/redcap_save_record.php
if ($instrument == 'mental_health_survey' && $_POST['suicidal'] == '1' && $response_id != null)
{
    $email_text = "A participant (record '$record') noted on the survey that they are suicidal. "
                . "Please take appropriate actions immediately to contact them.";
    REDCap::email('surveyadmin@mystudy.com', 'redcap@yoursite.edu', 'Suicide alert', $email_text);
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
