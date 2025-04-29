# 🔧 REDCap Hook: `redcap_add_edit_records_page`

**Available since**: REDCap 6.8.0  
**Returns**: `void`  
**Execution point**: At the top of the “Add/Edit Records” page (after the menu, before page render)

## 🧠 Purpose
Use this hook to perform custom logic or modify the user interface on the Add/Edit Records page. This includes:
- Printing HTML announcements or banners
- Injecting JavaScript/CSS
- Triggering PHP logic (e.g., data insert/update)

## 🧾 Parameters
- `$project_id` — REDCap project ID
- `$instrument` — Instrument unique name (Column B of the Data Dictionary)
- `$event_id` — Event ID (one per classic project, many in longitudinal)

## 🧪 Examples

### Example 1 – Static HTML
```php
function redcap_add_edit_records_page($project_id, $instrument, $event_id)
{
    print '<div class="yellow">Special announcement text to display at the top of the page.</div>';
}
```

### Example 2 – Project-Specific Logic
```php
function redcap_add_edit_records_page($project_id, $instrument, $event_id)
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

### Example 3 – Sandboxed Per-Project Scripts
```php
function redcap_add_edit_records_page($project_id, $instrument, $event_id)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_add_edit_records_page.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
