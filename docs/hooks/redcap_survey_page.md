# 📄 REDCap Hook: `redcap_survey_page`

**Available since**: REDCap 5.11.0  
**Returns**: `void`  
**Execution point**: At the very bottom of every survey page

## 🧠 Purpose
Use this hook to:
- Inject custom HTML, CSS, or JavaScript into live survey pages
- Perform backend tasks during live survey filling
- Dynamically adjust survey page content

> ⚠️ **Important**: This hook **does not fire** after survey completion.  
> Use `redcap_survey_acknowledgement_page` for actions after submission.

## 🧾 Parameters
- `$project_id` — project ID
- `$record` — record name (or `NULL`)
- `$instrument` — instrument unique name
- `$event_id` — event ID
- `$group_id` — DAG ID (or `NULL`)
- `$survey_hash` — survey URL hash
- `$response_id` — survey response ID
- `$repeat_instance` — repeat instance (default `1`)

## 🧪 Examples

### Example 1 – Static Text at Bottom of All Surveys
```php
function redcap_survey_page($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    print '<div class="yellow">Special announcement text to display at the very bottom of every survey.</div>';
}
```

### Example 2 – Project-Specific Behavior
```php
function redcap_survey_page($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    switch ($project_id) {
        case 212:
            // project-specific logic
            break;
        case 4775:
            // another project's logic
            break;
    }
}
```

### Example 3 – Sandboxed Per-Project Handler
```php
function redcap_survey_page($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_survey_page.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
