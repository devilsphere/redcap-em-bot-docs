# 🧾 REDCap Hook: `redcap_pdf`

**Available since**: REDCap 9.5.0  
**Returns**: `array` (only if modifying data/metadata)  
**Execution point**: Just before PDF generation (PdfController:index before `PDF::renderPDF()`)

## 🧠 Purpose
Use this hook to intercept or modify PDF output by:
- Adjusting PDF field metadata (e.g., labels)
- Filtering or manipulating record data
- Applying global logic to suppress/redact values

## 🧾 Parameters
- `$project_id` — the REDCap project ID
- `$metadata` — array of field metadata used to render structure
- `$data` — array of actual record data
- `$instrument` — instrument name (or `NULL` for all)
- `$record` — record ID (or `NULL` for blank form export)
- `$event_id` — event context (for longitudinal use)
- `$instance` — repeating instrument/event instance (default `1`)

## 📤 Return Format
Only return when modifying `$metadata` or `$data`:
```php
return array('metadata' => $metadata, 'data' => $data);
```

## 🧪 Examples

### Example 1 – Modify Labels and Remove a Record
```php
function redcap_pdf($project_id, $metadata, $data, $instrument=null, $record=null, $event_id=null, $instance=1)
{
    foreach ($metadata as &$attr) {
        $attr['element_label'] = "This is a field label.";
    }
    unset($data['101']);
    return array('metadata' => $metadata, 'data' => $data);
}
```

### Example 2 – Sandboxed Per-Project Handler
```php
function redcap_pdf($project_id, $metadata, $data, $instrument=null, $record=null, $event_id=null, $instance=1)
{
    $project_handler_script = dirname(__FILE__) . "/hooks/pid{$project_id}/" . __FUNCTION__ . ".php";
    if (file_exists($project_handler_script)) include $project_handler_script;

    return array('metadata' => $metadata, 'data' => $data);
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
