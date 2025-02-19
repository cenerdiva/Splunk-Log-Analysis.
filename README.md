# Splunk-Log-Analysis: Digging into Firewall and SSH Logs

## Objective
Understanding how to analyze security logs using Splunk, focusing on firewall events and SSH authentication logs.

## Skills Learned
- Querying logs in Splunk
- Detecting failed/successful login attempts
- Identifying security threats

## Tools Used
- Splunk
- Syslog
- Firewall logs
- SSH logs

## Searching Firewall Logs

If you're diving into Splunk to analyze security logs, you're in the right place. In this walkthrough, I'll break down how I used Splunk to search for firewall events and SSH authentication attempts, complete with screenshots.

First up, I ran a query to pull firewall logs from my syslog data:

```
index=main sourcetype=syslog "Firewall"
```

This returned events related to firewall activity, helping me spot connections and traffic patterns. The logs showed packet details, including source and destination IPs, MAC addresses, and protocol info.

## Tracking Failed SSH Logins

Next, I wanted to see if someone was hammering my SSH service with failed login attempts. I searched for:

```
index=main sourcetype=syslog "failed password"
```

Boom—there it was. Multiple failed login attempts from a sketchy IP. Classic brute-force attack behavior.

## Checking Successful SSH Logins

To compare, I also checked for successful SSH logins using:

```
index=main sourcetype=syslog "sshd"
```

This gave me a mix of failed and accepted logins, which helped paint a clearer picture of who was actually getting in vs. who was trying (and failing).

## Wrapping Up

Splunk makes it super easy to sift through logs and find potential security threats. Whether it's tracking firewall activity or spotting unauthorized SSH attempts, having the right queries makes all the difference.

Got any other Splunk tips? Hit me up—I'm always down to learn more! 🚀

