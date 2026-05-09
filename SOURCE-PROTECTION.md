# Source Code Protection for Shadow Realm Website

This document explains the source code protection measures implemented for the Shadow Realm website.

## Overview

While it's impossible to completely prevent users from viewing the source code of a website (since browsers need to download and process the HTML, CSS, and JavaScript to display the page), we've implemented several techniques to make it more difficult.

## Protection Measures

### 1. Enhanced Client-Side Protection

The website now includes several enhanced protection scripts:

- **JS/enhanced-protection.js**: Comprehensive client-side protection
- **JS/html-encryptor.js**: HTML content encryption and decryption
- **JS/apply-protection.js**: Automatically applies protection to page elements

These scripts provide the following protections:

- Disables right-click context menu
- Blocks keyboard shortcuts for viewing source (F12, Ctrl+U, Ctrl+Shift+I, etc.)
- Detects and responds to DevTools opening
- Disables text selection and copying
- Overrides console methods
- Prevents drag and drop
- Encrypts sensitive HTML content
- Prevents iframe embedding

### 2. Content Encryption

The `JS/html-encryptor.js` script provides advanced content protection:

- Content is encrypted using XOR encryption with a custom key
- Encrypted content is encoded in base64 format
- Content is decrypted at runtime only when needed
- Makes it significantly harder to view the original content in the source code

### 3. Server-Side Protection (When Using Node.js)

The Express server in `JS/app.js` adds several security headers:

- X-Frame-Options
- X-Content-Type-Options
- X-XSS-Protection
- Content-Security-Policy
- Cache-Control headers to prevent caching

### 4. JavaScript Obfuscation

The build process obfuscates JavaScript files to make them harder to read and understand.

## How to Use

### Method 1: Manual Implementation (For Individual Pages)

Add the following code to the `<head>` section of your HTML file:

```html
<!-- Source Protection Scripts -->
<script src="/JS/html-encryptor.js"></script>
```

Add the following code just before the closing `</body>` tag:

```html
<!-- Source Protection Scripts -->
<script src="/JS/enhanced-protection.js"></script>
<script src="/JS/apply-protection.js"></script>
```

### Method 2: Using the Batch File (For All Pages)

1. Run the `add-protection-to-all.bat` file
2. The script will automatically add the protection scripts to all HTML files in your website

### Method 3: Using the Web Interface

1. Open `apply-protection-to-all.html` in your browser
2. Follow the instructions provided on the page

### Protecting Sensitive Content

To protect specific sections of your HTML, add the `data-protect` attribute:

```html
<div data-protect>
    This content will be encrypted when the page loads.
</div>
```

You can also specify a custom encryption key:

```html
<div data-protect data-protect-key="YourCustomKey">
    This content will be encrypted with a custom key.
</div>
```

For pre-encrypted content:

```html
<div data-encrypted="ENCRYPTED_CONTENT_HERE" data-key="YourKey"></div>
```

### Running the Website with Node.js Protection (Optional)

If you're using Node.js:

1. Install dependencies:
   ```
   npm install
   ```

2. Start the server:
   ```
   npm start
   ```

## Limitations

These protection measures are not foolproof. Determined users can still access your source code through various means:

- Disabling JavaScript
- Using specialized browser extensions
- Accessing the network tab in DevTools
- Using command-line tools like curl or wget

The goal is to deter casual users from viewing or copying your source code, not to provide absolute protection.

## Examples and Tools

- `apply-protection-to-all.html`: Web interface for applying protection
- `add-protection-to-all.bat`: Batch script for applying protection to all HTML files
- `JS/encrypt-content-tool.js`: Tool for pre-encrypting content
- `examples/encoded-content-example.html`: Demonstration of the encoded content feature