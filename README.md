# huawei_simple
Remote access to a Huawei B818-263 LTE 4G router (experimental)

Since a few weeks I own a Huawei LTE Router and use it as a backup for my DSL-Connection. Since I acquired an LTE tariff with everything flat (phone, sms, internet with unlimited up- as well as download, I am looking for ways to make the best of everything. While the internet access is better than my DSL 8 120Mbit/s up & 35 Mbit/s down) I was looking forward to put the other options to use as well.

The Phone part is presently not usable from the router, I have a SIP account connected with it, but thats not what I really want. According to rukours it's technically possible to use the SIM cards telephone account, but for unknown reasons it's been disabled. :-)

But the good old SMS is useable and flat, so I kept looking for ways to remotely access this service.

There is little useful information to that end, either outdated or plain wrong, or connected to some high level language, which I also resent, as every project you touch uses a different language with different toolset and dependencies. So, most of the time I try to use bash to keep things simple.

I found two projects that basically work -and- use bash:

https://github.com/theRealAJR/LTE-Router-Huawei-B618s-22d and https://github.com/cmaion/huawei_router

They use different approaches to achieve basically identical functionality, but also leave room for exploring and building your own from there.

Then there are a few python or Java based APIs, which provide additional information that can be used to advantage.

https://pypi.org/project/huawei-lte-api/
https://github.com/siphomateke/huawei-router-api
https://github.com/jinxo13/HuaweiB525Router
https://www.mrt-prodz.com/blog/view/2015/05/huawei-modem-api-and-data-plan-monitor
https://github.com/if0xx/Huawei-Hilink-API
https://www.lteforum.at/mobilfunk/toolbox-fuer-huawei-router-mit-hilink.1872/seite-5.html

Since there is not really helpful information available from Huawei, except an app for Android and iPhone
which proves that remote access is possible, but does nothing to disclose the inner workings, I had (and still have) to follow the path the referenced prople took: trial & error and reengenineering.

As far as I could find out the communication with the device follows a sequence of events from issuing a SessionID as cookie and a Verification Token, that must be acuired before every access is granted. In addition, there are requests that are served without authorization and others that enforce authorization.

In addition every sequence of events has to be terminated by loggging out, otherwise the session wikk stay active for approximately 5 minutes, before it is terminated automagically.

Then there requests which only need a http:// get to a certain api endpoint, whereas others need to submit an xml string to speify your desire.

This information is also not easy to get at, some of it can be dug from the referenced api projects, some of them by simply analyzing the transfer between browser and webui of the gadget.

What I can supply here is simply a list of api endpoints that I tried on my device and a basic script for getting in touch with the router and add more functionality from there.

As I use GitHUB as notebook for my own use, things will be added over time, so stay tuned.

Feel free to share insights and snippets of information gathered, I will gladly add them.

March, 8th 2021 mulmic
