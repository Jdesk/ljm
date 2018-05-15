---


---

<p>CRAFT:</p>
<h3 id="injection">Injection:</h3>
<p>Craft/Yii uses <a href="http://php.net/manual/en/book.pdo.php">PDO</a> for all database queries, so all dynamic values are parameterized helping prevent SQL injection attacks.</p>
<h3 id="broken-authentication-and-session-management">Broken Authentication and Session Management:</h3>
<p>as of right now, there is no official two-factor authentication plugin for craft cms - this is the best way to handle broken auth and session management vulnerabilities. My recommendation is to hire a developer that can create a custom two factor authentication login system for craft cms.</p>
<h3 id="cross-site-scripting">Cross Site Scripting:</h3>
<p>elevated user sessions. The way it works is this: all high-target actions within Craft now require an “elevated user session”, meaning that the user must have entered their password in the past 5 minutes (configurable), not counting the time they logged in. This drastically narrows the window when an XSS vulnerability can be exploited.</p>
<ul>
<li>What will need to be done to mitigate the risks further - add elevated sessions as requirements for custom plugin form submissions. Eg admin area form submissions.</li>
</ul>
<h3 id="broken-access-control">Broken Access Control:</h3>
<p>craft folder is sitting above webroot and .htaccess rules are in place to prevent sensitive files from being accessed by endusers. Apache must be configured to parse .htaccess files. I have checked and Apache is indeed parsing .htaccess files.</p>
<h3 id="sensative-data-exposure--">Sensative Data Exposure -</h3>
<p>I have checked and craft folder is sitting above webroot and .htaccess rules are in place to prevent sensitive files from being accessed by endusers.</p>
<h3 id="cross-site-request-forgery--">Cross Site Request Forgery -</h3>
<p>I have checked and CSRF protection is enabled in config/general.php. I have also checked System report to make sure that the latest version of PHP and Craft are being used.</p>
<h3 id="underprotected-apis--">Underprotected APIS -</h3>
<p>Ensure that you have secured communications between the client and your APIs. Sherlock plugin will make sure that all communications are secured between your front and back end. I have personally checked and the Craft CSRF Token system is active and has a strong encryption method. The token system is protecting your front and backend APIS against attacks.</p>
<ol>
<li>
<p>Ensure that you have a strong authentication scheme for your APIs, and that all credentials, keys, and tokens have been secured. This is in place.</p>
</li>
<li>
<p>Ensure that whatever data format your requests use, the parser configuration is hardened against attack.</p>
</li>
<li>
<p>Implement an access control scheme that protects APIs from being improperly invoked, including unauthorized function and data references.</p>
</li>
<li>
<p>Protect against injection of all forms, as these attacks are just as viable through APIs as they are for normal apps.</p>
</li>
</ol>
<h3 id="insufficient-attack-protection">Insufficient Attack Protection:</h3>
<p>install sherlock plugin for craft cms. <a href="https://www.putyourlightson.net/craft-sherlock">https://www.putyourlightson.net/craft-sherlock</a></p>
<p>Using Components with known security vulnerabilities - Craft CMS before 2.6.2974 allows XSS attacks. - we are using a later version so we are good to go there. This can be checked off.</p>
<h1 id="securing-craft">Securing Craft</h1>
<p>There are a number of things that should be done to ensure your Craft install is as secure as possible.</p>
<h3 id="place-your-craft-folder-above-your-webroot-">Place your craft/ folder above your webroot <a href="https://craftcms.com/support/securing-craft#place-your-craft-folder-above-your-webroot">#</a></h3>
<p>The safest way to ensure that Craft’s PHP files and other sensitive information is not directly accessible over HTTP traffic is to put your entire craft/ folder above your webroot.</p>
<p>If, for whatever reason, you have to put your craft/ folder in webroot, you should ensure that users cannot directly access the contents of any files/folders in the craft/ folder. Craft ships with an .htaccess and a web.config file that denies access, but if you’re using nginx or Apache/IIS isn’t configured to parse .htaccess/web.config files, you’ll need to take extra steps to secure the files.</p>
<h3 id="install-an-ssl-certificate-and-enforce-it-">Install an SSL certificate and enforce it <a href="https://craftcms.com/support/securing-craft#install-an-ssl-certificate-and-enforce-it">#</a></h3>
<p>If you don’t already have an SSL certificate, talk to your host about how to get one installed. Once you have one in place, you should, at a minimum, enforce that all Control Panel traffic gets <a href="https://craftcms.com/support/force-ssl">sent over SSL</a>. Ideally, front-end traffic should use SSL as well, especially whenever private/sensitive information is being transmitted to/from the server.</p>
<h3 id="enable-all-“purify-html”-rich-text-field-settings-">Enable all “Purify HTML?” Rich Text field settings <a href="https://craftcms.com/support/securing-craft#enable-all-purify-html-rich-text-field-settings">#</a></h3>
<p>When the “Purify HTML?” Rich Text field setting is enabled, its values will always be run through <a href="http://htmlpurifier.org/">HTML Purifier</a> on save. That will ensure there is no JavaScript code in the field’s value, preventing potential XSS vulnerabilities that could be used for permission escalation and various other exploits.</p>
<h3 id="enable-csrf-protection-">Enable CSRF protection <a href="https://craftcms.com/support/securing-craft#enable-csrf-protection">#</a></h3>
<p>Enable <a href="https://craftcms.com/docs/config-settings#enableCsrfProtection">CSRF protection</a> in your craft/config/general.php file, then <a href="https://craftcms.com/support/csrf-protection">update your templates</a> to take advantage of it.</p>
<h3 id="make-sure-you’re-running-a-recent-version-of-php-">Make sure you’re running a recent version of PHP <a href="https://craftcms.com/support/securing-craft#make-sure-youre-running-a-recent-version-of-php">#</a></h3>
<p>Craft 3 requires PHP 7+. Craft 2 supports PHP 5.3.0 - 7.1.x but recommend 5.6+. PHP 5.5 is <a href="https://secure.php.net/supported-versions.php">officially no longer supported</a>. If at all possible, you should be running PHP 7+.</p>
<h3 id="keep-craft-and-all-of-your-installed-plugins-updated-">Keep Craft and all of your installed plugins updated <a href="https://craftcms.com/support/securing-craft#keep-craft-and-all-of-your-installed-plugins-updated">#</a></h3>
<p>All software has bugs. Older software has more bugs. Some bugs are security vulnerabilities. Keep your software updated to have less security vulnerabilities.</p>
<h3 id="check-your-permissions-">Check your permissions <a href="https://craftcms.com/support/securing-craft#check-your-permissions">#</a></h3>
<p>Craft has recommended permissions for its files to get up and running listed in the <a href="https://craftcms.com/docs/installing#step-2-set-the-permissions">installation instructions</a>, but you can certainly lock them down more depending on how your server is configured. Here is a handy <a href="https://gist.github.com/khalwat/e518fea8438a426a6049">shell script</a> you can use to configure and set permissions on a per-project basis on *nix based systems.</p>
<h3 id="review-config-settings-on-a-per-site-basis-">Review config settings on a per-site basis <a href="https://craftcms.com/support/securing-craft#review-config-settings-on-a-per-site-basis">#</a></h3>
<p>Each of these config settings have security implications and should be reviewed on a per-site basis. Craft ships with reasonable defaults for them, but depending on the site requirements, they can be adjusted to be more secure.</p>
<ul>
<li>
<p><a href="https://craftcms.com/docs/config-settings#cooldownDuration">cooldownDuration</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#invalidLoginWindowDuration">invalidLoginWindowDuration</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#maxInvalidLogins">maxInvalidLogins</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#rememberedUserSessionDuration">rememberedUserSessionDuration</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#userSessionDuration">userSessionDuration</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#requireMatchingUserAgentForSession">requireMatchingUserAgentForSession</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#requireUserAgentAndIpForSession">requireUserAgentAndIpForSession</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#verificationCodeDuration">verificationCodeDuration</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#defaultTokenDuration">defaultTokenDuration</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#blowfishHashCost">blowfishHashCost</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#preventUserEnumeration">preventUserEnumeration</a></p>
</li>
<li>
<p><a href="https://craftcms.com/docs/config-settings#validateUnsafeRequestParams">validateUnsafeRequestParams</a></p>
</li>
</ul>
<h3 id="set-security-headers-for-the-front-end-site-">Set security headers for the front-end site <a href="https://craftcms.com/support/securing-craft#set-security-headers-for-the-front-end-site">#</a></h3>
<p>Your server should be configured to send these security headers:</p>
<ul>
<li>
<p><a href="https://www.owasp.org/index.php/HTTP_Strict_Transport_Security">Strict-Transport-Security</a></p>
</li>
<li>
<p><a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/X-Frame-Options">X-Frame-Options</a></p>
</li>
<li>
<p><a href="https://www.owasp.org/index.php/List_of_useful_HTTP_headers">X-XSS-Protection</a></p>
</li>
<li>
<p><a href="https://www.owasp.org/index.php/List_of_useful_HTTP_headers">X-Content-Type-Options</a></p>
</li>
<li>
<p><a href="https://www.owasp.org/index.php/Content_Security_Policy">Content-Security-Policy</a></p>
</li>
<li>
<p><a href="https://developer.mozilla.org/en-US/docs/Web/Security/Public_Key_Pinning">Public-Key-Pins</a></p>
</li>
</ul>
<p>You can run your domain through a site like <a href="https://securityheaders.io/">securityheaders.io</a> to check for recommended header settings.</p>

