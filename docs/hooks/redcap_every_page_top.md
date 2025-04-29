# 🧩 REDCap Hook: `redcap_every_page_top`

**Available since**: REDCap 6.14.0  
**Returns**: `void`  
**Execution point**: At the **very top** of every REDCap page (right after `<body>`)

## 🧠 Purpose
Use this hook to globally affect page appearance and behavior:
- Inject custom CSS or JavaScript
- Set session variables globally
- Perform early project-based logic
- Render UI elements at the very top of the page

> ⚠️ You **must preserve** the REDCap copyright.

## 🧾 Parameters
- `$project_id` — REDCap project ID (or `NULL` if on non-project pages)

## 🧪 Examples

### Example 1 – Add Global Stylesheet
```php
function redcap_every_page_top($project_id)
{
    ?><link rel="stylesheet" type="text/css" href="/plugins/fancy/style.css" media="screen"><?php
}
```

### Example 2 – Session Variable for Super Users
```php
function redcap_every_page_top($project_id)
{
    if (SUPER_USER || USERID == 'paul.harris') {
        $_SESSION['show_special_features'] = true;
    }
}
```

### Example 3 – Page-Based Logic
```php
function redcap_every_page_top($project_id)
{
    if (PAGE == 'Design/online_designer.php') {
        // custom logic for Online Designer
    } elseif ($project_id == 759 && PAGE == 'FileRepositoryController:index') {
        // project/page-specific logic
    }
}
```

### Example 4 – Load a Framework on All Pages
```php
function redcap_every_page_top($project_id)
{
    require "/framework_path/my_framework.php";
    $framework = new FrameworkObject();
}
```

### Example 5 – Project-Specific Switch
```php
function redcap_every_page_top($project_id)
{
    switch ($project_id) {
        case 212:
            // project-specific logic
            break;
        case 4775:
            // project-specific logic
            break;
    }
}
```

### Example 6 – Sandboxed Per-Project Logic
```php
function redcap_every_page_top($project_id)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_every_page_top.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
