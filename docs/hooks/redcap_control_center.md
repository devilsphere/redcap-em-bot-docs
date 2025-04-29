# 🔧 REDCap Hook: `redcap_control_center`

**Available since**: REDCap 5.11.0  
**Returns**: `void`  
**Execution point**: At the bottom of **every page** in the REDCap Control Center

## 🧠 Purpose
Use this hook to perform custom actions within the Control Center, such as:
- Modifying the UI (e.g. custom menu links, styles)
- Running admin-level PHP logic
- Injecting JavaScript/CSS across all Control Center pages

## 🧾 Parameters
- None — the function takes no parameters

## 🧪 Example

### Add a custom link to the Control Center menu
```php
function redcap_control_center()
{
    // Output a link inside a div onto the page
    print  "<div id='my_custom_cc_link'>
                <a href='https://mysite.edu/otherpage/'>My Custom link to another page</a>
            </div>";

    // Use JavaScript/jQuery to append our link to the bottom of the left-hand menu
    print  "<script type='text/javascript'>
            $(document).ready(function(){
                // Append link to left-hand menu
                $( 'div#my_custom_cc_link' ).appendTo( 'div#control_center_menu' );
            });
            </script>";
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
