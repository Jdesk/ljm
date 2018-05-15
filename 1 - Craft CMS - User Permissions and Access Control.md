---


---

<hr>
<h1 id="craft-cms-user-access-control">Craft CMS User Access Control</h1>
<p>Setting up Granular User Access Controls (high-level):</p>
<ul>
<li>Go to Settings &gt;&gt; Users</li>
<li>Create a New User Group</li>
<li>Setup Permissions for that Particular User Group</li>
</ul>
<h1 id="users">Users</h1>
<p>Craft calls all member accounts of the system “users”.</p>
<p>The first user account is created during  <a href="https://docs.craftcms.com/v2/installing.html">installation</a>. If you stick with the Solo edition, this is the only account you will be able to create. If you need more you can upgrade to the Pro edition, which offers additional user accounts.</p>
<h2 id="admin-accounts">Admin Accounts</h2>
<p>Admin accounts are special accounts that can do absolutely everything within Craft, including some things that there aren’t even explicit permissions for:</p>
<ul>
<li>Everything within the Settings section</li>
<li>Make other users Admins (Craft Pro only)</li>
<li>Administrate other Admins (Craft Pro only)</li>
</ul>
<p>The user account you create during installation is an admin by default.</p>
<p>TIP</p>
<p>Considering the amount of damage an admin can do, it’s strongly recommended that you be conservative with creating new admin accounts. Only do it if you trust that they know what they’re doing.</p>
<h2 id="user-groups">User Groups</h2>
<p>If you have Craft Pro, you can create User Groups to help organize your site’s user accounts, as well as batch-set permissions on them.</p>
<p>To create a new User Group, go to Settings → Users and click the “New Group” button. You can give your group a Name and Handle, plus any permissions you want every user within the group to have.</p>
<p>Once your groups have been created, you can assign users to groups by going into their account settings and clicking on the Permissions tab.</p>
<h2 id="permissions">Permissions</h2>
<p>Craft Pro allows you to set permissions on users and groups, such as the ability to access the control panel, edit content within certain sections, etc. They can be applied directly to user accounts as well as to user groups. When permissions are applied to a user group, all users that belong to that group will inherit them.</p>
<p>The permissions Craft comes with are:</p>
<p>Permission</p>
<p>Handle</p>
<p>Access the site when the system is off</p>
<p><code>accessSiteWhenSystemIsOff</code></p>
<p>Access the CP</p>
<p><code>accessCp</code></p>
<p>↳ Access the CP when the system is off</p>
<p><code>accessCpWhenSystemIsOff</code></p>
<p>↳ Perform Craft and plugin updates</p>
<p><code>performUpdates</code></p>
<p>↳ Access  <em>[Plugin Name]</em></p>
<p><code>accessPlugin-[PluginHandle]</code></p>
<p>Edit users</p>
<p><code>editUsers</code></p>
<p>↳ Register users</p>
<p><code>registerUsers</code></p>
<p>↳ Assign permissions</p>
<p><code>assignUserPermissions</code></p>
<p>↳ Administrate users</p>
<p><code>administrateUsers</code></p>
<p>Delete users</p>
<p><code>deleteUsers</code></p>
<p>Edit  <em>[Locale Name]</em></p>
<p><code>editLocale:[LocaleID]</code></p>
<p>Edit entries</p>
<p><code>editEntries:[SectionID]</code></p>
<p>↳ Create entries</p>
<p><code>createEntries:[SectionID]</code></p>
<p>↳ Publish entries</p>
<p><code>publishEntries:[SectionID]</code></p>
<p>↳ Delete entries</p>
<p><code>deleteEntries:[SectionID]</code></p>
<p>↳ Edit other authors’ entries</p>
<p><code>editPeerEntries:[SectionID]</code></p>
<pre><code>  ↳  Publish other authors’ entries | `publishPeerEntries:[SectionID]`
  
  ↳  Delete other authors’ entries | `deletePeerEntries:[SectionID]`

</code></pre>
<p>↳ Edit other authors’ drafts |  <code>editPeerEntryDrafts:[SectionID]</code></p>
<p>↳ Publish other authors’ drafts |  <code>publishPeerEntryDrafts:[SectionID]</code></p>
<p>↳ Delete other authors’ drafts |  <code>deletePeerEntryDrafts:[SectionID]</code></p>
<p>Edit  <em>[Global Set Name]</em>  |  <code>editGlobalSet:[GlobalSetID]</code></p>
<p>Edit  <em>[Category Group Name]</em>|  <code>editCategories:[CategoryGroupID]</code></p>
<p>View  <em>[Asset Source Name]</em>  |  <code>viewAssetSource:[SourceID]</code></p>
<p>↳ Upload files |  <code>uploadToAssetSource:[SourceID]</code></p>
<p>↳ Create subfolders |  <code>createSubfoldersInAssetSource:[SourceID]</code></p>
<p>↳ Remove files |  <code>removeFromAssetSource:[SourceID]</code></p>
<h2 id="public-registration">Public Registration</h2>
<p>Craft Pro has the option of allowing public user registration. It is not enabled by default, though. To enable it, you must go to Settings → Users → Settings, and check the “Allow public registration?” setting. With that checked, you will also be given the ability to choose a default user group that publicly-registered users are assigned to.</p>
<p><img src="https://docs.craftcms.com/v2/assets/img/users-settings-publicregistration.a9a4f169.jpg" alt="Users Settings Public Registration"></p>
<p>Once your site is set up to allow public user registration, the last step is to create a  <a href="https://docs.craftcms.com/v2/templating/user-registration-form.html">user registration form</a>  on your site’s front end.</p>
<h2 id="forms-access-control">Forms Access Control</h2>
<h3 id="go-to-settings--users">1.  Go to Settings &gt;&gt; Users</h3>
<h3 id="create-a-user-group-for-form-admins---call-it-form-admins">2.  Create a User Group for Form Admins - Call it “Form Admins”</h3>
<h3 id="setup-permissions-for-forms-admins">3.  Setup Permissions for Forms Admins</h3>
<h3 id="select-all-freeform-permission-levels">4.  Select all Freeform Permission Levels:</h3>
<ul>
<li>Access Submissions
<ul>
<li>Manage All Submissions</li>
<li>For 24JE Signup</li>
<li>For BasicTest</li>
<li>For Campus Chapter</li>
<li>For Churches Mobilization</li>
<li>For Contact Us</li>
<li>For Email Capture</li>
<li>For Freedom Sunday</li>
<li>For Partnerships</li>
<li>For Prayer Partner</li>
<li>For Request Speaker</li>
<li>For Rotary</li>
<li>For Team Freedom</li>
</ul>
</li>
<li>Access Forms
<ul>
<li>Manage Forms</li>
</ul>
</li>
<li>Access Fields
<ul>
<li>Manage Fields</li>
</ul>
</li>
<li>Access Email Templates
<ul>
<li>Manage Email Templates</li>
</ul>
</li>
<li>Access Export Profiles
<ul>
<li>Manage Export Profiles</li>
</ul>
</li>
<li>Access Settings</li>
</ul>
<h3 id="add-users-to-form-admin-user-group.--go-to-users--select-user--permissions-.">5. Add Users to Form Admin user group.  Go to Users &gt;&gt; Select User &gt;&gt; Permissions .</h3>
<h3 id="check-the-box-next-to-forms-admin-to-allow-this-user-access-to-the-user-group-allowing-administration-of-forms-data.">6. Check the box next to Forms Admin to allow this user access to the user group allowing administration of forms data.</h3>

