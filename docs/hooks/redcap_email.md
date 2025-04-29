# 📧 REDCap Hook: `redcap_email`

**Available since**: REDCap 9.5.0  
**Returns**: `boolean` (return `FALSE` or `0` to prevent default send behavior)  
**Execution point**: Just before REDCap calls its native email send method (`REDCap::email()`)

## 🧠 Purpose
Intercept or modify any outgoing email from REDCap before it’s sent. Common use cases:
- Custom email routing or overrides
- Alternative SMTP gateways
- Conditional email suppression
- Custom formatting or logging

## 🧾 Parameters
- `$to` — recipient(s), separated by semicolons
- `$from` — sender email address
- `$subject` — email subject line
- `$message` — email body (HTML/plain text)
- `$cc` — CC list (optional)
- `$bcc` — BCC list (optional)
- `$fromName` — sender display name (optional)
- `$attachments` — associative array of attachments (`filename => server_path`)

## 📤 Return Logic
- `FALSE` or `0` → cancels the native REDCap email from being sent
- `TRUE` or no return → proceeds with REDCap’s normal email logic

## 🧪 Examples

### Example 1 – Let REDCap Send the Email
```php
function redcap_email($to, $from, $subject, $message, $cc, $bcc, $fromName, $attachments)
{
    // No interference; proceed normally
    return TRUE;
}
```

### Example 2 – Send via Custom SMTP if Gmail Detected
```php
function redcap_email($to, $from, $subject, $message, $cc, $bcc, $fromName, $attachments)
{
    if (stristr($from, '@gmail.com') !== false) {
        // Send with Gmail SMTP...

        // Block default REDCap mailer
        return FALSE;
    }
    return TRUE;
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
