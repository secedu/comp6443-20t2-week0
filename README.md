project_path: /_project.yaml
book_path: /_book.yaml


Note: this document also lives on https://www.quoccabank.com/week0

# Getting Started

Welcome to Web Application Security! This course is very practical and as such we expect you to be able to use a couple of core tools so you can get knee deep in some exercises once the trimester starts.

Objective: Follow through this document to set up the basic tooling you'll need for this course and have a crack at the small exercises, this is not marked or assessed but not being able to get through this document may be a sign that web application security is something you want to attempt further down the line in your computing degree.

Throughout this course, you will be entering an exciting journey to learn about some of the common web application vulnerabilities and apply what you learn to QuoccaBank, one of Australia's leading banking services who claims to be the "Cyber-Friendly" bank. You're a curious customer who just opened an account at this bank, but as you go on in the course, you'll note that the bank might not be as secure as you think, and you'll uncover more insights as you go further. Maybe you'll even join the bank as a staff later!

## Important Disclaimer

QuoccaBank is a fictitious company, designed by the Course Staff of UNSW COMP6443 20T2. It is not a real financial service provider, nor is any of the customer/staff/financial information true in the real world. You have been granted permission to perform penetration testing on \*.quoccabank.com during the course.

Warning: This does not allow you to do any sort of physical attacks, social engineering on any of the course staff members or your fellow students, or any kind of Denial of Service attack on our infrastructure. Good faith policies apply. For any targets outside this scope, we do not have the authority to give you attacking permission. Under no circumstances can you attack UNSW infrastructure (*.unsw.edu.au).

If you have any concerns regarding this, please contact course staff at cs6443@cse.unsw.edu.au.

<h2 class="hide-from-toc">Logging into your bank</h2>
## Setting up mTLS authentication

You should be already familiar with PKI (Public-Key Infrastructure) from COMP6441. But in case you forgot, we'll cover that briefly during Week 1's lecture as well. You don't need to know any of the RSA/AES/ECC arithmetics for this course, it's nice to have a general idea about how certificates work.

Password is too 20-th century, as an innovative bank that's keen to use the latest technologies and best practices. We use mTLS (mutual TLS) authentication here at Quaccabank (hmmm I hear you say 2FA, we'll talk about that later in the course)!

Follow the instructions on [https://login.quoccabank.com/](https://login.quoccabank.com/) to sign and install your certificate. If everything works out, when you visit [https://whoami.quoccabank.com/](https://whoami.quoccabank.com/), it should show you something like this:

    Hello Adam Yi! You are authenticated as z5231521@quoccabank.com.

Note: for installing certificates, due to the change of location for that setting on different browser versions (online guides might not refer to the location in the latest version), it might be easier to just search for "cert" in Chrome/Firefox settings (chrome://settings or about:preferences in Firefox) and import it there. After installing, if your browser doesn't prompt you to pick a certificate when visiting whoami.quoccabank.com, try restarting your browser process (the entire browser OS process, not just a window or a tab)

If you have any issues with mTLS authentication, please contact us via cs6443@cse.unsw.edu.au

<h2 class="hide-from-toc">Wow what's that</h2>
## Flag Submission

Throughout the course, you'll be asked to hack many targets. Most of them will have a flag in it. A flag is a special string hidden somewhere in the application. Unless otherwise specified, it's usually of the syntax `COMP6443{xxxxxxx}` or `COMP6843{xxxxxxxx}`.

As a demo, and a gesture of welcoming you to the course, here are two free flags for you! Visit [https://welcome.quoccabank.com](https://welcome.quoccabank.com) to claim them (they are not assessable and will not count towards course marks but do have CTFd points associated).

After you got the flags, submit them on [https://ctfd.quoccabank.com](https://ctfd.quoccabank.com/). We'll use this as a submission platform for most of the practical assignment and exam challenges, so make sure you're familiar with it. You can verify your submission is successful by clicking "Profile" on the top-right corner of CTFd. Each flag will be associated with certain points, and there's a scoreboard on CTFd. While CTFd points are not directly associated with your assessment marks, they will be highly relevant (CTFd gives you your points sum for all challenges while for marking we only sum up the assessable ones for that specific assignment/exam, and weightings could be adjusted). Plus, the CTFd scoreboard is a nice way for you to flex (weird but ok)!

While we encourage working together, directly sharing flags with other students before deadlines is strictly prohibited, and doing so is considered as plagiarism. We have monitoring mechanisms in place.

<h2 class="hide-from-toc">Creating your bank account</h2>
## Getting to Know Browser Developer Tools

You can use any browser really but we highly recommend using either Chrome or Firefox. Make sure you run the latest version for best compatibility and security patches.

Regardless of what you pick you need to have some familiarity with the developer tools, right-click "inspect element" or go to the tools/settings dropdown of your browser and open developer tools. On Chrome this is `top right dropdown > More Tools > Developer Tools` and on Firefox it is `top right dropdown > Web Developer > Toggle Tools`

You'll see a pop up in which you can edit the html (in case you're a nerd, you're actually editing the DOM tree rendered by your browser), see JavaScript output and via the network tab you can see network requests the page makes.

See the relevant docs for more info but it's pretty self explanatory and stack-overflowable.

* Chrome: [https://developers.google.com/web/tools/chrome-devtools/](https://developers.google.com/web/tools/chrome-devtools/])
* Firefox: [https://developer.mozilla.org/en-US/docs/Tools](https://developer.mozilla.org/en-US/docs/Tools)

<h3 class="hide-from-toc">Now, Let's Get a QuoccaBank Account!</h3>

Go to [https://account.quoccabank.com/](https://account.quoccabank.com/) and create your very first QuoccaBank Account!

By default, it denied your application but you can use browser developer tools to approve it!

<h2 class="hide-from-toc">A side note</h2>
## Browser profiles

Although not necessary you may find it useful to create another user in your browser called "hack0r" or similar. This account will have its own history, accounts, remembered passwords and extensions which is useful so you don't mix work and pleasure. If you don't want your browser to remember anything locally, the Incognito profile also works quite good (it doesn't hide your traffic, but just doesn't store local history). Once you start messing with websites you don't want form payloads to be saved and then accidentally enter them into another website when just trying to browse. Having a somewhat isolated environment for hacking is useful.

<h2 class="hide-from-toc">That's yummy</h2>
## Cookies

Once we start learning about cookies it becomes really useful to edit and fiddle with them, you can do this by hand and mess with headers and http requests but it gets tedious. It's useful to have an extension to make this easy. Go ahead and install one of the below

* Chrome: [https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=en](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=en)
* Firefox: [https://addons.mozilla.org/en-US/firefox/addon/edit-cookie/](https://addons.mozilla.org/en-US/firefox/addon/edit-cookie/)

<h3 class="hide-from-toc">It's time for cookies!</h3>

Even though we are a bank, at its core, we are still a tech company. So we deeply understand the most important thing in the tech industry: swags! We are giving out our customized QuoccaBank-branded cookies (I heard they are delicious) to randomly chosen customers, go check [https://cookies.quoccabank.com/](https://cookies.quoccabank.com/) and see if you are lucky enough to get your customized cookie!

<h2 class="hide-from-toc">Shipping your MasterCard (request)</h2>
## Installing Burp Suite

<h3 class="hide-from-toc">HTTP Request</h3>

Ever wondering what actually happens after you click that "enter" button after putting in an url in your browser? You are probably already familiar with this by doing COMP1531/3331/9331/etc., but don't worry if you don't know. Here's a brief intro: on a really high level, it sends an HTTP request and waits for a response from the server. Each part contains a header and a body. It looks like this:

```http
GET / HTTP/1.1
Host: intro-to-ctf.nsa.group
User-Agent: curl/7.64.1
Accept: */*

HTTP/1.1 200
content-type: text/html; charset=utf-8
vary: Accept-Encoding
x-cloud-trace-context: ad6d3c143a04d77b3ebee8362c386736;o=1
date: Sat, 23 May 2020 15:44:37 GMT
server: Google Frontend
content-length: 195

Hello World
```

You can see this from your browser's developer tool we just talked about. In the next section, you'll install Burp Suite, a nice tool that sits as a proxy between your browser and the server so that you can see the actual traffic payload at a lower level of the network stack. You can even modify the request/response before sending that to the server/the browser. It's super useful for almost all web app testing.

<h3 class="hide-from-toc">Install</h3>

Burp Suite is a really powerful application that will act as a proxy between the Internet and you, any requests coming in and out of your computer gets stopped by burp suite allowing you to edit them. You can also use it to do some basic brute forcing and other really neat things.

Start by installing it, the free version should be more than enough for this course but note that if you want to pursue Web application testing the premium version is a pretty invaluable tool.

[https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

Now Burp Suite doesn't work unless you set up a proxy so burp suite can step between you and servers. It's really useful to be able to switch back and forth between using this proxy and not since it can slow down your internet significantly, so although not 100% needed it's a good idea to install a proxy switcher.

* Chrome: [https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif/related](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif/related)
* Firefox: [https://addons.mozilla.org/en-US/firefox/addon/switchyomega/](https://addons.mozilla.org/en-US/firefox/addon/switchyomega/)

<h3 class="hide-from-toc">Proxy</h3>

If you used the proxy switched suggested above do the following

1. click on the proxy icon in the toolbar
2. go to "options"
3. click on "proxy" under profiles
4. edit the entry
5. Click on "apply changes" under actions on the left

Otherwise refer to the following links

* Chrome: [https://support.portswigger.net/customer/portal/articles/1783065-configuring-chrome-to-work-with-burp](https://support.portswigger.net/customer/portal/articles/1783065-configuring-chrome-to-work-with-burp)
* Firefox: [https://support.portswigger.net/customer/portal/articles/1783066-configuring-firefox-to-work-with-burp](https://support.portswigger.net/customer/portal/articles/1783066-configuring-firefox-to-work-with-burp)

Once that's done you can try to use Burp suite. Open the application, go to the proxy tab and make sure "intercept is on" is toggled. Then open a browser on which the proxy is activated. If you used the suggested extension just click on the extension icon on the top right and select "proxy". if you visit any site it should hang and the burp suite window will show the the attempted request your browser made that was intercepted, you can forward this to let it leave the computer but chances are you'll also get this in your browser.

This is because the proxy doesn't have a valid Certificate. To remedy this you just have to tell ur computer that's it's ok and ur just hacking yourself.

Use the following links to install burps CA Certificate: [https://support.portswigger.net/customer/portal/articles/1783075-Installing_Installing CA Certificate.html](https://support.portswigger.net/customer/portal/articles/1783075-Installing_Installing CA Certificate.html)

After this give everything a good restart and you should be able to intercept requests.

<h3 class="hide-from-toc">mTLS in Burp</h3>

**Do not install your mTLS certificate as a CA certificate. If you have accidentally done this jump to Resetting your Burp certificate setup**

In order to install your mTLS certificate in Burpsuite:

1. Go to Burp > User Options > TLS.
2. You should see a fieldset titled "Client TLS Certificates".
3. Click on "Add" button to the left of the table.
4. This should bring up a popup asking you for a "Destination host" and "Certificate type".
5. Set the destination host to `*.quoccabank.com` and select the radio button next to `File (PKCS#12)`.
6. You should now be asked to browse to your "Certificate file" and enter a "Password".
7. Select your mTLS certificate for "Certificate file", and the password that you received during certificate creation for the "Password" field.
8. This should add the mTLS certificate (you should now see it in the Client TLS Certificates table)

Please refer to [https://portswigger.net/burp/documentation/desktop/options/tls#client-tls-certificates](https://portswigger.net/burp/documentation/desktop/options/tls#client-tls-certificates) for official documentation.

<h4 class="hide-from-toc">Resetting your Burp certificate setup</h4>

If you have imported your certificate as a CA certificate, or otherwise broken your Burp certificate setup you can reset it with the steps below.

1. Remove the Burp CA certificate you installed in your browser.
2. Go to Burp > Proxy > Options.
3. In the Proxy Listeners fieldset click the "Regenerate CA certificate" button. (Note: this will invalidate other burp CA certificates you have installed anywhere else)
4. Navigate back to http://burp and download/install a new CA cer.tificate
5. Follow the instructions above to install your mTLS certificate.

<h3 class="hide-from-toc">Let's get your MasterCard shipped</h3>

Now that you've set up your account, let's get a card as well! Visit [https://card.quoccabank.com](https://card.quoccabank.com) to ship your card. However, you need to pay a shipping fee for your card and you don't have any money in your account. I wonder what you can do...

Note: Burp is not your only option here, but it's the most widely-used option in the industry. OWASP ZAP, Charles, and many others also offer similar features, but we won't cover how to use them in this course. You can even try writing your own proxy!

<h2 class="hide-from-toc">I can script that!</h2>
## Python

A lot of penetration testing relies on automation and although you could do everything by hand it really isn't going to get you very far. As such we need to be comfortable with scripting exploits and tooling in python. You can use other languages but python has a lot of very good libraries and tooling and is what we recommend.

Despite python 2's EOL, for compatibility reasons, we recommend installing both Python 2 and 3.

[https://realpython.com/installing-python/](https://realpython.com/installing-python/)

<h3 class="hide-from-toc">Are you a true hacker?</h3>

A useful library is the requests library, pip install it.

Use it to request [https://en.wikipedia.org/wiki/Hacker](https://en.wikipedia.org/wiki/Hacker) and print out every link on the page (i.e /wiki/locksmithing)

This isn't COMP2041, we don't care if you miss a couple links, just make sure you understand how you can write a script to make requests and search through responses.

Note: Python is quite slow, and its default implementation CPython has some performance issues due to some of the design choices. It's good for this course and most of your day-to-day life. But if you want to make a really performance-critical tool that runs distributively at a large scale in your automation infrastructure, you might want to consider some of the compiled and more concurrency-friendly languages, but that's outside the scope of this course.

<h3 class="hide-from-toc">Working with mTLS in scripts</h3>

Running automating tooling against quoccabank maybe made complex by the fact that quoccabank requires mTLS for authentication. Here we outline two approaches that you can use to make mTLS work with your scripts. For example, try running curl against whoami.quoccabank.com.

```bash
$ curl -i https://whoami.quoccabank.com
content-type: text/plain
date: Mon, 01 Jun 2020 09:21:18 GMT
server: whoami
x-ctf-trace-context: 00000000-0000-0000-0000-000000000000
content-length: 65

You have not logged in! Please visit https://login.quoccabank.com
```

As you can see we are not signed in.

<h4 class="hide-from-toc">Proxying Traffic through Burp</h4>

If you have Burp setup properly, you can simply proxy your traffic through Burp's proxy in order to associate it with your mTLS certificate. Most tools have builtin support for http proxies, alternatively you could also set a system proxy through the `http[s]_proxy` variable. Note that taking this approach will log all your requests in burp, which may be something you don't want if you are running a massive bruteforce attack.

To do this all we need to find the is host/port Burp is listening on. This can be retrieved from Burp > Proxy > Options > Proxy Listeners. This address can immediately be used for most tooling. For example you can run curl as follows.

```bash
$ curl --proxy http://127.0.0.1:8080 -k -i https://whoami.quoccabank.com
HTTP/1.0 200 Connection established

HTTP/1.1 200 OK
Content-Length: 58
Content-Type: text/plain
Date: Mon, 01 Jun 2020 10:14:22 GMT
Server: whoami
X-Ctfproxy-Trace-Context: 00000000-0000-0000-0000-0000000000
Connection: close

Hello @todo! You are authenticated as todo@quoccabank.com.
```

Note that we needed to use the `-k` flag to allow insecure certificates. If you really want to avoid having to specify this option, you can add Burp's certificate as a system trusted certificate, this is probably best done at your own risk in a dedicated environment (if there's an alternative I would love to know - @todo). In order to do this you first need to export Burp's certificate (Burp > Proxy > Options > Import/Export Certificate > Export.Certificate in DER Format). You can then convert this to a pem and add it to your system's ca-certificates. _This was tested on Ubuntu @ WSL2_

```bash
% openssl x509 -in exported_cert.der -inform DER -out portswigger.crt -outform PEM
% mkdir /usr/local/share/ca-certificates/comp6443
% mv portswigger.crt /usr/local/share/ca-certificates/comp6443
% update-ca-certificates
```

If you want to do this more generally you could also install and configure a tool like proxychains (proxychains-ng).

<h5 class="hide-from-toc">Optional: Setting up Burp</h5>

Personally I (@todo) like to have automated tools and manual browsing to go through different Burp proxies. This allows you to filter your proxy history to only contain manual browsing. We can add a new proxy as follows:

1. Go to Burp > Proxy > Options
2. In the fieldset Proxy Listeners click Add
3. Add a new port to listen on in the "Bind to port" field and select the address you would like the proxy to bind to (loopback only is usually fine, if you're running WSL[2] or using a VM you may have to set a specifc address)
4. Use this address and port instead of the default Burp proxy for your automated tooling.
5. You can then navigate to your HTTP history, click on the filter bar up the top, and filter based on proxy port.

<h4 class="hide-from-toc">Extracting Certificates from the PKCS#12 archive</h4>

If you are writing your own scripts or don't want to proxy your traffic through burp, you can also extract the certificate and key from within the PKCS#12 file. You will need openssl installed and your installation key on hand.

```bash
$ openssl pkcs12 -in 6443.p12 -nodes
```

This will ask you for your import password, and print the certificate and key to stdout. Copy the content of the certificate and key (beginning with `-----BEGIN XXX -----` (inclusive)) and save it as two separate files.

Once you have these two files, you can use them in your scripts. For example, curl might look like this:

```bash
$ curl --cert /home/me/certs/6443.pem --key /home/me/certs/6443.key -i https://whoami.quoccabank.com
HTTP/2 200
content-type: text/plain
date: Tue, 02 Jun 2020 01:54:51 GMT
server: whoami
x-ctfproxy-trace-content: 00000000-0000-0000-0000-000000000000
content-length: 58

Hello @todo! You are authenticated as todo@quoccabank.com.
```

A simple nc style connection might look like this:

```bash
$ openssl s_client -quiet -ign_eof -cert ~/certs/6443.pem -key ~/certs/6443.key -connect whoami.quoccabank.com:443
```

Or you can use the certificates in python requests

```python
import requests

print(requests.get(
    'https://whoami.quoccabank.com',
    cert=('/home/todo/certs/6443.pem', '/home/todo/certs/6443.key'
).text)

# Out: Hello todo! You are authenticated as todo@quoccabank.com
```

Note: These certificates identify you to the course, treat them like you would a username and password. Make sure not to share them, either intentionally, or by accidentally uploading them to a shared server or github repository. Ideally keep these in a secure directory separate from all your main work. If you do share or otherwise lose control over your certificates, please notify course staff (cs6443@cse.unsw.edu.au).

