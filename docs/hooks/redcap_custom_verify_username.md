# 🔧 REDCap Hook: `redcap_custom_verify_username`

**Available since**: REDCap 5.8.0  
**Returns**: `array` (`status` => TRUE/FALSE, `message` => string)  
**Execution point**: On the **User Rights** page when someone attempts to add or assign a user

## 🧠 Purpose
This hook allows verification of a user's identity using external authentication systems (e.g., LDAP, Shibboleth) before they are granted access to a project.

Use cases:
- Prevent adding unauthorized users
- Display validation errors
- Show custom advisory messages for specific user conditions

## 🧾 Parameters
- `$username` — the user’s REDCap username being checked

## 📤 Return Format
```php
return array(
    'status'  => TRUE or FALSE,
    'message' => 'Text to display (if any)'
);
```

- If `status` is `FALSE`, the user will **not** be added
- If `status` is `TRUE`, the user **is added**, and message is optionally shown
- If `message` is blank or `null`, no message is shown

## 🧪 Examples

### Example 1 – Invalid User
```php
function redcap_custom_verify_username($username) {
    return array('status'=>FALSE, 'message'=>'ERROR: User $username is not a valid username!');
}
```

### Example 2 – Valid User, No Message
```php
function redcap_custom_verify_username($username) {
    return array('status'=>TRUE, 'message'=>'');
}
```

### Example 3 – Valid User with Advisory Message
```php
function redcap_custom_verify_username($username) {
    return array('status'=>TRUE, 'message'=>'Although this user is valid, please be sure to [DO WHATEVER] before adding them.');
}
```

## ⚠️ Setup Requirement
Hooks **will not work** unless you create a Hook Functions PHP file and define its full server path under:
**Control Center → General Configuration → Path to Hook Functions File**

---

[🔙 Return to Hook Reference Index](index.md)
