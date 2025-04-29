# 🔧 REDCap Hook: `redcap_data_entry_form`

**Available since**: REDCap 5.11.0  
**Returns**: `void`  
**Execution point**: At the **bottom** of every data entry form (excluding surveys)

## 🧠 Purpose
Use this hook to perform actions on a data entry form such as:
- Adding backend logic
- Injecting HTML/CSS/JS
- Displaying banners, messages, or validation UI

## 🧾 Parameters
- `$project_id` — REDCap project ID
- `$record` — Record name (may be `NULL` for new records)
- `$instrument` — Instrument unique name (from Data Dictionary)
- `$event_id` — Event ID for longitudinal projects
- `$group_id` — Data Access Group ID (or `NULL`)
- `$repeat_instance` — Repeating instrument/event instance (default = 1; added in REDCap 7.3.4)

## 🧪 Examples

### Example 1 – Static Footer Content
```php
function redcap_data_entry_form($project_id, $record, $instrument, $event_id, $group_id, $repeat_instance)
{
    print '<div class="yellow">Special announcement text to display at the very bottom of every data entry form.</div>';
}
```

### Example 2 – Project-Specific Logic
```php
function redcap_data_entry_form($project_id, $record, $instrument, $event_id, $group_id, $repeat_instance)
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

### Example 3 – Sandboxed Per-Project Logic
```php
function redcap_data_entry_form($project_id, $record, $instrument, $event_id, $group_id, $repeat_instance)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_data_entry_form.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
