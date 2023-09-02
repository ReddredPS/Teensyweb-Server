# Teensyweb-Server Redistribution


TeensyWeb Server 0.2.0
======================

The TeensyWeb server is the site you are looking at.  It's written in Ruby and built on 
Rails.  It's made up of four coupled applications or controllers.

TeensyWeb 0.1.0 has been released.  It may be downloaded from <a 
href=ftp://sourcery.dyndns.org/pub/ruby/teensyweb.tar.gz>here</a>.

It requires rails, bluecloth, syntax be installed, which you can get from gems.
In order to use subversion and graphwiz you must have those installed and the commands 
accessible from the path.

See license and contributions file for license information.

The subversion repository may be accessed at <http://sourcery.dyndns.org/svn/teensyweb>.


Installation
------------

1. Modify config/database.yaml to set up your database name and type
2. Modify config/wiki_config.yaml to set up your site name and email information.
3. Runthe command...`rake migrate` ...to create the database.
4. Either setup apache, lightttpd or run `script\server` to run under webbrick.


Notifications
-------------

This is an email notification system.  It constructs and sends emails for signup and 
forgotten passwords.  The application is configured so that anyone should be able to browse
the forums and wiki pages.  To do anything more than that you need to click on the 
signup link above.  Signup asks you for a login name and an email address.  A password 
will be generated and sent to that email address.  Once you get it you should be able
 to login to the site by clicking the login link or by executing an action that 
requires you to be logged in.  Once you are logged in other options appear.  You can 
change your email address or pick a new password by clicking on the preferences link.  If 
you ever forget your password, you can click on the forgot password button from the login 
screen.  A new password will be generated and sent to you.

* Email addresses are not visible on the site, except by those with the admin flag.


Accounts
--------

The account system authenticates users, manages their preferences, and checks for 
authorization to perform administrative maintenance functions.

Wiki
----

### Wiki features ###

1. Create pages by clicking on undefined wikiwords (indicated by the ? link), or by typing a 
page name in the text box at the bottom of a page and clicking the Create button.   There is 
strict checking on valid page names.  Currently an error throws you into editing the 
HomePage, but since I've locked the Homepage here, you'll just be shown it.
2. Errors displayed in red just under the navigation bar at the top.
3. List all pages - click All on navigation bar.
4. Show the pages changed in the last 7 days - click Recently Revised on the navigation bar.
5. Show page back references.  Click on the page name at the top of the page.  Back 
references list all the pages that reference the page you are on.  Only WikiWords are 
counted as references.
6. All page revisions are saved.  Clicking the revisions link at the bottom the page 
presents you with a list of revisions.  The highest numbered revision is current page.  
Clicking on revision puts you in edit mode on that revision.  Saving it then becomes the 
current page.  Thus you can roll back edits in this way.  Or you can go fetch things you 
accidently deleted via cut, hit cancel and go back to edit the current page and paste it 
into the page.
7. The search box at the top allows simple words or regular expressions.  It only searches 
the wiki pages.

### Markup ###

The Wiki uses BlueCloth as it's markup language.  When editing a page a you'll see a list of 
the most common formatting codes.  

BlueCloth is a markup language based on 
[Markdown](http://daringfireball.net/projects/markdown/).  You should find the full syntax 
there.

In addition to BlueCloth, WikiWords are turned into links and ruby code is marked up by
Syntax.  To indicate Ruby code you surrounded it with...  

[ruby]  
..code..   
[/ruby]  

You can embed Graphwiz commands to generate graphs with...

[graph nameofgraph]
..dot commands..
[/graph]

* There is currently no way to escape certain constructs like WikiWords and other markup.

Forum
-----

The Forum code does not use any markup language.  It will turn WikiWords into links and 
allow you to markup ruby code as above.

### Forum features ###

2. Reply will auto quote the post you are replying to.  It uses a format common to how many 
email readers quote.
1. The search box at the top allows simple words or regular expressions.  It only searches 
the posts, not the wiki pages.

Repository
----------

### Repository features ###

The repository application allows you to browse the subversion repsitory.

1. Changelog shows the last 10 log entries.
2. Files matching known code extensions are formatted using ruby Syntax.
Todo/Requested feature lists
============================

Wiki
----

* HTML needs to be properly sanitized.
* Rename page and wikilinks ability.
* Delete page ability.
* Ftp links not working.  Must use html.
* Wanted pages list?  
* Orphaned pages list?
* Search that looks at both forum posts and wiki pages?
* Just why do I have this comment field?  I don't use it.
* Allow revision diffing.
* Potential performance enhancements if needed.
  * Rendering cache
  * Store WikiWords in page table.
* Render wikiwords into meta keywords header
* Recently Revised ought to have options to look back further.
 

Forums
------

* HTML needs to be properly sanitized.
* BlueCloth won't work here because quoting is formatted into blockquotes.  An odd situation 
because the philosophy is the same.  so...
  * some of Bluecloth ought to be integrated bold/italics/underline.
* While topic list is sorted descending on create date, it might be better to sort it by the 
last posts date.  That way old topics are bumped to the top if someone posts on them.

Accounts
--------

* Remember me option on preferences that reads and writes login cookies.
* Option to enable email display?
* Allow other vanity information like...
  * Website name
  * ICQ, AIM stuff
  * Alias field / real name
* Optional stylesheet 
* Allow specifying time to view for recent posts and recent pages

  
Repository
----------

* Binary files are not handled correctly.  They are just dumped to the user.
