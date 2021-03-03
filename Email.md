Header 
the Reply-To is used to specify the recipient when you reply to the email. If it is different from what's originally shown on the screen, you may accidentally send your reply to someone else. The other thing to keep your eye on, is the Return-Path. This is used when an email cannot be delivered to its recipients, and it “bounces back”. Spammers don't want all the undelivered emails to end up in their inboxes.

One way to increase your trust in an email is checking whether it has been authenticated in a trustworthy way. SPF (Sender Policy Framework), DKIM (DomainKeys Identified Mail) and DMARC (Domain-based Message Authentication, Reporting and Conformance) are ways to authenticate your mail server and to prove to ISPs, mail services, and other receiving mail servers that senders are truly authorized to send emails. When properly set up, all three prove that the sender is legitimate.

SPF is an email authentication method that specifies which IP addresses and/or servers are allowed to send email from that particular domain. The list of authorized sending hosts and IP addresses is published in the DNS TXT record for that domain.

DKIM, also known as email signing, validates the authenticity of email messages. Every email is signed with a private key when it's sent out and that signature is validated by the receiving email server or the internet service provider. The goal is to prove that the integrity of an email message has not been affected – that neither the message itself nor its headers have been tampered with.

DMARC confirms that a sender's email messages are protected by both SPF and DKIM. If the messages don't pass the check, they can either be delivered, quarantined or rejected, as per instructions within DMARC records.

The authentication results can be found under the Authentication-Results header.