%%%
Title = "Using SipHash for Secret Key Transaction Authentication for DNS"
abbrev = "siphash-for-tsig"
docname = "@DOCNAME@"
category = "std"
ipr = "trust200902"
area = "Internet"
workgroup = "DNSOP Working Group"
updates = [7873]
date = 2019-04-17T00:00:00Z

[seriesInfo]
name = "Internet-Draft"
value = "@DOCNAME@"
stream = "IETF"
status = "standard"

[[author]]
initials = "O."
surname = "Sury"
fullname = "Ondrej Sury"
organization = "Internet Systems Consortium"
[author.address]
 email = "ondrej@isc.org"
[author.address.postal]
 country = "CZ"
%%%


.# Abstract

TSIG, as specified in RFC 2845, is a message authentication code
mechanism for authenticating DNS messages.

This document add SipHash-2-4 algorithm as new algorithm for TSIG.

This document updates RFC2845.

{mainmatter}

# Introduction

TSIG, as specified in [@!RFC2845], is a mechanism for transaction
level authentication using shared secrets and one way hashing.  It can
be used to authenticate dynamic updates as coming from an approved
client, or to authenticate responses as coming from an approved
recursive name server.

[@SipHash-2-4] is a pseudorandom function that's suitable to be used
as message authentication code (MAC).

This document defines the use of SipHash-2-4 as algorithm for TSIG.

## Definitions

The key words "**MUST**", "**MUST NOT**", "**REQUIRED**", 
"**SHALL**", "**SHALL NOT**", "**SHOULD**", "**SHOULD NOT**",
"**RECOMMENDED**", "**NOT RECOMMENDED**", "**MAY**", and
"**OPTIONAL**" in this document are to be interpreted as described in
BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all
capitals, as shown here.

# Algorithm

An SipHash-2-4 key consist of 16-octet value.  The algorithm uses the
DNS Message and the key to calculate 128-bit message authentication code.

## Truncation

HMAC output Truncation, as specified in [@!RFC4635] Section 3, is forbidden
to be used with SipHash-2-4.

## Mnemonics

The mnemonics for SipHash-2-4 is siphash-2-4.

# IANA Considerations

This document updates the IANA registry "Secret Key Transaction
Authentication for DNS (TSIG) Algorithm Names".  The following entries
have been added to the registry:

Algorithm Name | Reference
:--------------|:-------------
siphash-2-4    | This document

<reference anchor='SipHash-2-4' target='https://131002.net/siphash/'>
    <front>
        <title>SipHash: a fast short-input PRF</title>
	<author fullname="Jean-Philippe Aumasson" initials="J." surname="Aumasson" />
	<author fullname="Daniel J. Bernstein" initials="D. J." surname="Bernstein" />
	<date year="2012"/>
    </front>
</reference>

{backmatter}
