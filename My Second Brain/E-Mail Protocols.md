---
tags: [networks]
Created: 2023-09-02T13:01:44+10:00
Modified: 2024-07-03T19:35:33+10:00
---
All three email protocol are [[Transmission Control Protocol|TCP]] based protocols to ensure reliable delivery of large messages.

Summary:
- POP3 and IMAP are for mail retrievals and SMPT is for sending email messages 
- IMAP is designed to store messages on the mail server. It stores incoming and outgoing messages on the server in folders
- POP3 is designed to store messages on the local device.
# Post Office Protocol
E-mail clients use the Post Office protocol version 3 (POP3) protocol to download incoming messages from an e-mail server to their local desktop. POP3 clients download e-mail from the mail server running at the user's ISP and these messages are then deleted from the server. POP3 uses TCP port 110
# Internet Message Access Protocol
Internet Message Access Protocol version 4 (IMAP4) has advanced message controls, including the capability to manage messages locally yet store them on a server, plus numerous fault-tolerance features. IMAP4 downloads only e-mail headers initially and then downloads the message body and attachments when the message is selected. IMAP4 uses TCP port 143.
# Simple Mail Transfer Protocol
Simple Mail Transfer Protocol (SMTP) is the standard protocol for sending e-mail over the [[Internet, Intranet, Extranet|Internet]]. POP3 is used to retrieve e-mail and SMTP is used to send it. SMTP uses TCP port 25. 