# 🔝 REDCap Hook: `redcap_survey_page_top`

**Available since**: REDCap 6.8.0  
**Returns**: `void`  
**Execution point**: At the very **top** of every survey page (near BODY tag)

## 🧠 Purpose
Use this hook to:
- Output HTML, CSS, or JavaScript **at the very top** of survey pages
- Perform backend operations early during page load
- Add banners, alerts, or preload resources

> ⚠️ **Important**: This hook **does not fire** after survey completion.  
> Use `redcap_survey_complete` or `redcap_survey_acknowledgement_page` for post-completion actions.

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

### Example 1 – Static Banner at Top
```php
function redcap_survey_page_top($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    print '<div class="yellow">Special announcement text to display at the top of every survey.</div>';
}
```

### Example 2 – Project-Specific Actions
```php
function redcap_survey_page_top($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    switch ($project_id) {
        case 212:
            // logic for project 212
            break;
        case 4775:
            // logic for project 4775
            break;
    }
}
```

### Example 3 – Sandboxed Per-Project Handler
```php
function redcap_survey_page_top($project_id, $record, $instrument, $event_id, $group_id, $survey_hash, $response_id, $repeat_instance)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_survey_page_top.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
