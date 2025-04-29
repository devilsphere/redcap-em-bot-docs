# 🏠 REDCap Hook: `redcap_project_home_page`

**Available since**: REDCap 6.9.0  
**Returns**: `void`  
**Execution point**: Near the **top** of the "Project Home" page (below the navigation tabs)

## 🧠 Purpose
Use this hook to customize or inject content into the Project Home page, such as:
- Displaying project announcements
- Adding reminder banners
- Running backend operations on page load

## 🧾 Parameters
- `$project_id` — REDCap project ID

## 🧪 Examples

### Example 1 – Static Announcement
```php
function redcap_project_home_page($project_id)
{
    print '<div class="yellow">Special announcement text to display at the top of the home page.</div>';
}
```

### Example 2 – Project-Specific Logic
```php
function redcap_project_home_page($project_id)
{
    switch ($project_id) {
        case 212:
            // special home page logic for project 212
            break;
        case 4775:
            // special home page logic for project 4775
            break;
    }
}
```

### Example 3 – Sandboxed Per-Project Handler
```php
function redcap_project_home_page($project_id)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_project_home_page.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
