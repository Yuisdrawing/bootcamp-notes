<!--
Student takeaway:
By the end of this lesson, the student should know:
* What a domain is
* What a hosting is
* How to transfer files via FileZilla
-->

# Getting Your Site Online

See this lesson in [video format](https://youtu.be/5q_BfpuSuVU).

## Domains & Hostings

Here at Juno, we are all about promoting your online presence. Every developer needs a website to host their portfolio and a bit about them.

When purchasing your website, it's important to understand the two main components of owning a website.

### Hosting
Hosting refers to the actual server that holds the files your website is comprised of. Servers can be located anywhere in the world and hold millions of other users files.

Each server has an IP (internet protocol) address that can be reached via the browser. For example your localhost, `127.0.0.1`.

When a website is 'live', that means that files have been moved from a users computer onto the hosting server.

### Domain Names
Since accessing servers via long numbers like `127.0.0.1` is difficult, domain names are used as friendlier options that point to the long addresses.

For example, when you visit 'http://junocollege.com' in your browser, the domain name is mapped to the numbered server address. This is called domain name resolving.

Domain names can be purchased together with hosting, or separately. When purchased separately, you need to point your DNS (Domain Name Servers) from your domain registrar to your hosting company. In these cases, you will need to ask your **hosting** company for which name servers to use (ns1.bluehost.com, ns2.bluehost.com), and change accordingly in your domain registrar's settings. If this is the case, reach out to the domain and hosting companies support, or an instructor.

**To learn more about how your browser connects to a website**, check out this cute but informative comic, [How DNS Works](https://howdns.works)! Also here is a great comic on how [HTTPS works](https://howhttps.works/) as well!

> **Disclosure:**
> Juno receives remuneration from the following companies when you use our affiliate links below. All proceeds we receive from affiliate partnerships are used for awesome alumni programming, such as Visibility:Hidden!

Domains:

* [Hover](https://hover.com/IbL8v5UV)
* [Namecheap](http://www.jdoqocy.com/click-8951841-11426545)

Hosting:

* [DreamHost](http://www.dreamhost.com/r.cgi?2137548)
* [SiteGround](https://www.siteground.com/index.htm?afcode=8d0b6cfbb3392c6083f2310e4d1ae00a)
* [GreenGeeks](https://www.greengeeks.com/track/hackeryou/cp-default)
* [HostGator](https://partners.hostgator.com/hackeryou)
* [Bluehost](http://www.bluehost.com/track/hackeryou)


## FTP

FTP stands for **file transfer protocol**. It allows us to connect to a server and upload files to it.

There are many ways to deploy your files to a web server, for example, developers working with a language called Ruby on Rail often use tools like Capistrano or Heroku. However, FTP is the simplest and most common for developers like yourself.

To connect to FTP, we need a FTP client. You may have a favourite FTP client already, and you are welcome to use it. These are the most popular and do more than enough.

**Mac and Windows:** [FileZilla](http://filezilla-project.org/download.php?type=client)

**Mac:** [Transmit](http://panic.com/transmit/)

### FTP Username and Password

You will have to setup a FTP account with your hosting.  The connection details are required for the FTP client.

* Host
* Port
* Username
* Password

> **Note:**
> Put your username and password somewhere safe. If you use a password manager, we **highly** recommend putting your username and password in there now.

## Configuring FileZilla

Start new connection with _File_ > _Site Manager_ then click _New Site_ to enter your credentials:

* Rename `New Site` to whatever you like
* Host: Your Domain Name or server IP address (e.g. ftp.yourdomainname.com)
* Port: 21
* Protocol: FTP - File Transfer Protocol
* Encryption: Use plain FTP
* Logon Type: Ask for Password
* User: Username of your FTP account

Go ahead and click _Connect_, you should be prompted for your password and connected to your server.

FileZilla will now show a listing of all the files on your **local** machine on left hand side and all the files in the **root** directory of your **remote** webserver on right hand side. 

You can navigate around the files and directories on both sides like in Explorer or Finder. To upload to the server, drag and drop from the left side to the right.

The server works just like your computer, upload an `index.html` and checkout your domain _www.yourdomain.com_ to see live updates. Note that with some server configurations, you'll need to place your files in the _public_html_ directory.

Similarly, you can upload a folder called `final-project` and find it live at _www.yourdomain.com/final-project_ to see it.

A best practice is to edit your website locally (on your computer) until you are happy with your progress. Then drag and drop the entire folders contents onto your server.
