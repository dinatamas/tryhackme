Walking An Application
======================

Manually review a web application for security issues using only your browsers
developer tools. Hacking with just your browser, no tools or scripts.

## Walking An Application

### (1)

_I confirm that I have deployed the virtual machine and opened the website._

> N/A

## Exploring The Website

Spot interactive parts of the website (forms, javascript, etc.)

Manual link walking: table with Feature | URL | Summary (notes) columns.

### (1)

_Read the above._

> N/A

## Viewing The Page Source

Look for comments in the code.

Private-use website areas.

External file paths may reveal listable directories (w/ source code, backups, etc).

Detect web frameworks and their known vulnerabilities (may use an older version).

### (1)

_What is the flag from the HTML comment?_

> THM{HTML_COMMENTS_ARE_DANGEROUS}

### (2)

_What is the flag from the secret link?_

> THM{NOT_A_SECRET_ANYMORE}

### (3)

_What is the directory listing flag?_

> THM{INVALID_DIRECTORY_PERMISSIONS}

### (4)

_What is the framework flag?_

> THM{KEEP_YOUR_SOFTWARE_UPDATED}

## Developer Tools - Inspector

## Developer Tools - Debugger

## Developer Tools - Network

