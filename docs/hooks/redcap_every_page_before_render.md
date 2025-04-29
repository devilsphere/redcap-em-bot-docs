# 🌐 REDCap Hook: `redcap_every_page_before_render`

**Available since**: REDCap 6.14.0  
**Returns**: `void`  
**Execution point**: Called by *every* PHP script before rendering begins (end of REDCap’s config script)

## 🧠 Purpose
Allows global control of REDCap behavior on **every page** (projects and admin-level), such as:
- Setting global session variables
- Injecting UI logic for specific pages
- Performing project-specific operations early in page load
- Initializing frameworks or global helpers

> ⚠️ The REDCap copyright **must remain visible**. If modified or moved, it must be restored using `REDCap::getCopyright`.

## 🧾 Parameters
- `$project_id` — REDCap project ID (will be `NULL` on non-project pages)

## 🧪 Examples

### Example 1 – Add Session Variable for Specific Users
```php
function redcap_every_page_before_render($project_id)
{
    if (SUPER_USER || USERID == 'paul.harris') {
        $_SESSION['show_special_features'] = true;
    }
}
```

### Example 2 – Page-Specific Logic
```php
function redcap_every_page_before_render($project_id)
{
    if (PAGE == 'Design/online_designer.php') {
        // do something on Online Designer
    } elseif ($project_id == 759 && PAGE == 'FileRepositoryController:index') {
        // project-specific logic
    }
}
```

### Example 3 – Load Frameworks on All Pages
```php
function redcap_every_page_before_render($project_id)
{
    require "/framework_path/my_framework.php";
    $framework = new FrameworkObject();
}
```

### Example 4 – Project-Specific Switch
```php
function redcap_every_page_before_render($project_id)
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

### Example 5 – Sandboxed Project Logic
```php
function redcap_every_page_before_render($project_id)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_every_page_before_render.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
