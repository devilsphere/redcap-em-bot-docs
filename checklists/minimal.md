# ✅ Minimal REDCap EM Development Checklist

- [ ] Create `config.json` with basic metadata: name, namespace, authors, version
- [ ] Add at least one setting (project or system)
- [ ] Register module with REDCap in `/modules` directory
- [ ] Implement a PHP `ExternalModule.php` file extending `Vanderbilt\ExternalModule\AbstractExternalModule`
