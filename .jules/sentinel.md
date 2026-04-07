## 2025-05-14 - Restricted Permissions for Persistent State
**Vulnerability:** Persistent session state was being saved with default umask permissions, potentially making sensitive data readable by other users on the same system.
**Learning:** Frameworks that persist state to the user's home directory (e.g., `~/.klix/sessions/`) must explicitly enforce restricted permissions to ensure data privacy in multi-user environments.
**Prevention:** Use `Path.chmod(0o700)` for directories and `Path.chmod(0o600)` for files immediately after creation to override loose umask settings.
