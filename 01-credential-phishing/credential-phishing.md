# Microsoft 365 Credential Phishing



## Summary

**Subject:** Action Required: Your password expires in 24 hours

The email impersonates Microsoft 365 Security, claims that unusual sign-in activity was detected, and wanted the recipient to verify their account immediately.



## Evidence

1. **Sender impersonation** - The display name is Microsoft 365 Security, And the sender address is security-alert@micros0ft-support[.]com, Which it uses 0 zero rather than o.

2. **Email authentication** — header reports
spf=fail for the sender domain smtp.mailfrom=mailer-x7.top And the IP '203[.]0[.]113[.]45';
dkim=none (message not signed);
dmarc=fail for the sender domain 'micros0ft-support[.]com'

3. **Misleading links** — the visible URL hxxps[:]//login[.]microsoftonline[.]com but The hyperlink to it is  href="hxxp[:]//203[.]0[.]113[.]45/login/office365/verify", **The keep my password link** href="hxxps[:]//bit[.]ly/3xR9kQp".

4. **HTML attachment** - filename= "Password_Reset_Form.pdf.html" Its contains a form that asks for an email and password to submit your Credential to the Misleading link.



## Verdict
**High-confidence credential phishing.** The Microsoft impersonation, The Misleading links, And the filename= "Password_Reset_Form.pdf.html" form those support the Verdict.



## User Impact and Next Steps

User impact is unknown. The email sample alone cannot establish whether anyone clicked a link, opened the attachment, or submitted credentials.

In a live incident, I would:

1. **Identify affected recipients.** Search email gateway logs in Splunk for the sender, subject, and attachment name. Check which mailboxes received the message.
2. **Check for user interaction.** Review web proxy and endpoint logs around the delivery time for requests to the link destination or signs that the HTML attachment was opened. Ask affected recipients whether they entered credentials.
3. **Contain the incident.** If a recipient reports submitting credentials, escalate it.
