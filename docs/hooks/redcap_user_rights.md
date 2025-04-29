# 👥 REDCap Hook: `redcap_user_rights`

**Available since**: REDCap 5.11.0  
**Returns**: `void`  
**Execution point**: Bottom of the **User Rights** page in every project

## 🧠 Purpose
Use this hook to:
- Add custom HTML, JavaScript, or messages to the User Rights page
- Perform backend logic related to users or roles
- Highlight important user management instructions

## 🧾 Parameters
- `$project_id` — project ID

## 🧪 Examples

### Example 1 – Announcement Box Using jQuery
```php
function redcap_user_rights()
{
    print '<div class="yellow" id="my_custom_user_rights_div">
        Special announcement text to display right below the instructional text on every User Rights page.
    </div>';

    print "<script type='text/javascript'>
            $(document).ready(function(){
                $( 'div#user_rights_roles_table_parent' ).before( $('div#my_custom_user_rights_div') );
            });
           </script>";
}
```

### Example 2 – Project-Specific Actions
```php
function redcap_user_rights($project_id)
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
function redcap_user_rights($project_id)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/redcap_user_rights.php";
    if (file_exists($project_handler_script)) include $project_handler_script;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
