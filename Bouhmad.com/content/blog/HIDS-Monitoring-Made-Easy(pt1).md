+++
author = "Theme author"
categories = [""]
date = "2017-09-17"
description = "HIDS Made Easy(pt1)"
featured = "wazuh-dash.png"
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "HIDS Monitoring Made Easy"
type = "post"

+++

## Author's Note

This Blog, let alone this blog post, has been something I've been meaning to get off
the ground for quite some time. Because of this, I will attempt to curb my extreme 
enthusiasm as I attempt to write a meaningful post on one of my favorite technologies, HIDS. This is supposed to be a fairly high-level look at a few different providers in the space. 

I hope you all enjoy the blog, and please, if you have questions or want me to talk/elaborate on a specific technology please email me at adbouhmad@gmail.com, or send me a DM on twitter @adambouhmad. 

Thanks all, and enjoy!

## What is a HIDS

HIDS stands for Host-Based Intrustion Detection System. A HIDS is meant to monitor an individual host for possible malicious activity. 
Examples of malicious activity a HIDS could monitor and alert on could be anything from brute-force attempts on SSH to RCE like [CVE-2017-5638](https://nvd.nist.gov/vuln/detail/CVE-2017-5638). HIDS fall under the broad term that enterprise vendors like to call 'Endpoint Security'. 

Whereas previously Endpoint Security strategies focused heavily on signature based antivirus software, now adays quite a bit more is important, as signatures don't always tell the tale. Here's a few examples of features that are necessary: 

- Querying of filesystem(Linux)
- FIM(File Integrity Monitoring)
- Some form of rootkit detection
- Log Monitoring/Analysis 

Let's now break each of these down into their respective parts and how each vendor addresses the feature. 


## Wazuh

Not to be confused with Seclists Open Source Security Mailing list(OS-SEC), OSSEC is an open source host-based intrusion detection system aimed at helping you have visibility into actions happening on a machine. Unfortunately, I've sucummbed to my innate bias and have started off with one of my favorite HIDS, WAZUH. You may be scratching your forehead, as you begin to wonder why you've never heard of Wazuh before. Well, Wazuh is actually a fork of the OSSEC project, focused specifically on maintaining some newer rulesets. It also provides support for AWS & PCI DSS controls. 

![Wazuh Dash](/img/2017/09/wazuh-dash.png)

Alternatively, outside of traditional HIDS functionality, OSSEC can also be used simply as a log analysis tool. Here's the traditional flow of Wazuh events. 

You can create your own rulesets. Through my experience with OSSEC as a HIDS/SEM, I must say that out of the box it is already configured to have quite a few rulesets. With these rulesets you can do a variety of things: 

EXAMPLE
- Detect nginx attacks
this can be anything from enumeration of specific directories on a website to even buffer overflows. You alternatively can define your own rule specific alerts...think recent apache vulnerabilities. 

It will also allow you to triage alerts with syslog info. What do I mean by this? Well, because all event information gets forwarded onto the OSSEC manager if your client is set to be in server-client relationship, you can actually index all log data that you deem necessary. You can define this in the /var/ossec/etc/shared/agent.conf file specifically per host/subnet, or whathave you. 

Wazuh also integrated with cloud platforms such as Amazon Web Services(AWS) out of the box, allowing for Cloudtrail logs to be ingested and have actionable alerts to follow. The Wazuh community is increasingly growing, and their [mailing list](https://groups.google.com/forum/#!forum/wazuh) is extremely active. 
