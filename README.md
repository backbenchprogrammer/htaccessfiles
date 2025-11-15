# htaccessfiles
This project includes two custom .htaccess files to ensure the Laravel application runs correctly when deployed on servers that do not place the project directly inside the public directory. These files also add important security improvements.

## 1. Root .htaccess

Located in the project root.

Purpose:

Redirect all incoming requests to the /public directory so the Laravel app works normally.

Allow access to storage files (storage/app/public) without requiring a symlink.

Prevent access to hidden files (e.g., .env) for security.

Disable directory listing.

Serve existing files and folders directly when they exist.

Why it's needed:
Many shared hosting environments do not support custom document root settings, so this file ensures the project still functions as expected.

2. Public/.htaccess

Located inside the public directory.

Purpose:

Handle Laravel’s normal routing (forward unknown requests to index.php).

Preserve authorization headers for API authentication.

Allow direct access to the /storage directory if a symlink is present.

Remove trailing slashes from URLs.

Why it's needed:
This file ensures that Laravel routing, API requests, and static file loading work exactly as intended.

Summary

Together, these .htaccess files:

Secure the application by blocking hidden file access

Ensure Laravel routes work correctly

Allow the project to run normally even when a custom document root can't be set

Keep storage files accessible without breaking security
