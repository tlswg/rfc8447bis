---
title: IANA Registry Updates for TLS and DTLS
abbrev: (D)TLS IANA Registry Updates
docname: draft-ietf-tls-rfc8447bis-latest
submissiontype: IETF
category: std
updates: 8447
v: 3

ipr: trust200902
area: "Security"
workgroup: "Transport Layer Security"
keyword: Internet-Draft
venue:
  group: "Transport Layer Security"
  type: "Working Group"
  mail: "tls@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/tls/"
  github: "tlswg/rfc8447bis"

stand_alone: yes
smart_quotes: no
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: J. Salowey
    name: Joe Salowey
    organization: Venafi
    email: joe@salowey.net
 -
    ins: S. Turner
    name: Sean Turner
    organization: sn3rd
    email: sean@sn3rd.com

normative:

informative:

--- abstract

This document updates the changes to TLS and DTLS IANA registries
made in RFC 8447. It adds a new value "D" for discouraged
to the Recommended column of the selected TLS registries and
adds a "Comment" column to all active registries that do not
already have a "Comment" column. Finally, it updates the
registration request instructions.

This document updates RFC 8447.

--- middle

# Introduction

This document instructs IANA to make changes to a number of the IANA
registries related to Transport Layer Security (TLS) and Datagram
Transport Layer Security (DTLS). These changes update the changes made
in {{!RFC8447}}.

<aside markdown="block">
  RFC EDITOR NOTE: Please remove the note that follows.
</aside>

<aside markdown="block">
  NOTE for IANA: This document specifies changes to the registry to update
  the changes made in {{RFC8447}}.
</aside>

This specification adds a new value "D" for discouraged to the Recommended
column of the selected TLS registries and adds a "Comment" column to all
active registries that do not already have a "Comment" column.

This specication also updates the registration request instructions.

# Terminology

{::boilerplate bcp14-tagged}

# Updating "Recommended" Column's Values

The instructions in this document update the Recommended column,
originally added in {{RFC8447}} to add a third value, "D",
indicating that a value is "Discouraged". The permitted values
of the "Recommended" column are:

Y:
: Indicates that the IETF has consensus that the
    item is RECOMMENDED. This only means that the associated
    mechanism is fit for the purpose for which it was defined.
    Careful reading of the documentation for the mechanism is
    necessary to understand the applicability of that mechanism.
    The IETF could recommend mechanisms that have limited
    applicability, but will provide applicability statements that
    describe any limitations of the mechanism or necessary constraints
    on its use.

N:
: Indicates that the item has not been evaluated by
    the IETF and that the IETF has made no statement about the
    suitability of the associated mechanism. This does not necessarily
    mean that the mechanism is flawed, only that no consensus exists.
    The IETF might have consensus to leave an items marked as "N" on
    the basis of its having limited applicability or usage constraints.

D:
: Indicates that the item is discouraged. This marking could be used to identify
    mechanisms that might result in problems if they are used, such as
    a weak cryptographic algorithm or a mechanism that might cause
    interoperability problems in deployment. When marking a registry entry as
    “D”, either the References or the Comments Column MUST include sufficient
    information to determine why the marking has been applied. Implementers and
    users SHOULD consult the linked references associated with the item to
    determine the conditions under which the item SHOULD NOT or MUST NOT be used.

Setting a value to "Y" or "D" or transitioning the value from "Y" or "D" in the "Recommended" column requires
IETF Standards Action with Expert Review or IESG Approval {{!RFC8126}}. Not all items defined
in Standards Track RFCs need to be set
to "Y" or "D". Any item not otherwise specified is set to "N". The column is
blank for values that are unassigned or reserved unless specifically set.

## Recommended Note {#rec-note}

Existing registries have a note on the meaning of the Recommended column. For the
registries discussed in the subsequent sections this note is updated
with a sentence describing the "D" value as follows:

Note:

: If "Recommended" column is set to "N", it does not necessarily mean
that it is flawed; rather, it indicates that the item either has not
been through the IETF consensus process, has limited applicability, or
is intended only for specific use cases.  If the "Recommended" column
is set to "D" the item is discouraged and SHOULD NOT or MUST NOT be used,
depending upon the situation; consult the item’s references for clarity.


# TLS ExtensionType Values Registry

In order to reflect the changes in the Recommended column allocation,
IANA is requested to update the TLS ExtensionType Values registry as follows:

- Adjust the registration procedure related to setting the “Recommended” column as follows:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D" in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Update the "Recommended" column with the changes as listed below.  Entries
  keep their existing "Y" and "N" entries except for the entries in following table.
  IANA is requested to add a reference to this document for these entries.

|Value | Extension                                | Recommended |
|:-----|:------------------------------------|------------:|
|4  |truncated_hmac                  |         D |
|53 |connection_id (deprecated)      |         D |
|40 |Reserved                        |         D |
|46 |Reserved                        |         D |

- Update note on the Recommended column with text in {{rec-note}}.

- For the truncated_hmac, add the following link to Reference column:
https://www.iacr.org/archive/asiacrypt2011/70730368/70730368.pdf

- For the two Reserved values above, add the following link in the Reference column:
https://mailarchive.ietf.org/arch/msg/tls-reg-review/5BD62HBFjo_AsW-Y8ohVuWEe1gI/


# TLS Cipher Suites Registry

Several categories of ciphersuites are discouraged for general use and
are marked as "D".

Ciphersuites that use NULL encryption do not provide the confidentiality
normally expected of TLS. Protocols and applications are often designed
to require confidentiality as a security property. These
ciphersuites MUST NOT be used in those cases.

Ciphersuites marked as EXPORT use weak ciphers and were deprecated in
TLS 1.1 {{!RFC4346}}.

Cipher suites marked as anon do not provide any authentication and are
vulnerable to on-path attacks and are deprecated in TLS 1.1
{{!RFC4346}}.

RC4 is a weak cipher and is deprecated in {{!RFC7465}}.

DES and IDEA are not considered secure for general use and are deprecated
in {{!RFC5469}}. Nor is MD5 or SHA-1 and these are deprecated in {{!RFC9155}}.

In order to reflect the changes in the Recommended column allocation,
IANA is requested to update the TLS ExtensionType Values registry as follows:

- Adjust the registration procedure related to setting the “Recommended” column as follows:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D" in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Update the "Recommended" column with the changes as listed below.  Entries
  keep their existing "Y" and "N" entries except for the entries in following table.
  IANA is requested to add a reference to this document for these entries. This document does not
  make any changes to the DTLS-OK column.

| Value | Cipher Suite Name                             | Recommended |
|:------|:---------------------------------------------|-----------:|
| 0x00,0x1E | TLS_KRB5_WITH_DES_CBC_SHA            |   D  |
| 0x00,0x20 | TLS_KRB5_WITH_RC4_128_SHA            |   D  |
| 0x00,0x21 | TLS_KRB5_WITH_IDEA_CBC_SHA            |   D  |
| 0x00,0x22 | TLS_KRB5_WITH_DES_CBC_MD5            |   D  |
| 0x00,0x24 | TLS_KRB5_WITH_RC4_128_MD5            |   D  |
| 0x00,0x25 | TLS_KRB5_WITH_IDEA_CBC_MD5           |   D  |
| 0x00,0x26 | TLS_KRB5_EXPORT_WITH_DES_CBC_40_SHA  | D |
| 0x00,0x27 | TLS_KRB5_EXPORT_WITH_RC2_CBC_40_SHA | D |
| 0x00,0x28 | TLS_KRB5_EXPORT_WITH_RC4_40_SHA | D |
| 0x00,0x29 | TLS_KRB5_EXPORT_WITH_DES_CBC_40_MD5 | D |
| 0x00,0x2A | TLS_KRB5_EXPORT_WITH_RC2_CBC_40_MD5 | D |
| 0x00,0x2B | TLS_KRB5_EXPORT_WITH_RC4_40_MD5 | D |
| 0x00,0x2C | TLS_PSK_WITH_NULL_SHA | D |
| 0x00,0x8A | TLS_PSK_WITH_RC4_128_SHA | D |
| 0x00,0xB0 | TLS_PSK_WITH_NULL_SHA256 | D |
| 0x00,0xB1 | TLS_PSK_WITH_NULL_SHA384 | D |
| 0xC0,0x06 | TLS_ECDHE_ECDSA_WITH_NULL_SHA | D |
| 0xC0,0x07 | TLS_ECDHE_ECDSA_WITH_RC4_128_SHA | D |
| 0xC0,0x10 | TLS_ECDHE_RSA_WITH_NULL_SHA | D |
| 0xC0,0x11 | TLS_ECDHE_RSA_WITH_RC4_128_SHA | D |
| 0xC0,0x33 | TLS_ECDHE_PSK_WITH_RC4_128_SHA | D |
| 0xC0,0x39 | TLS_ECDHE_PSK_WITH_NULL_SHA | D |
| 0xC0,0x3A | TLS_ECDHE_PSK_WITH_NULL_SHA256 | D |
| 0xC0,0x3B | TLS_ECDHE_PSK_WITH_NULL_SHA384 | D |
| 0xC0,0xB4 | TLS_SHA256_SHA256 | D |
| 0xC0,0xB5 | TLS_SHA384_SHA384 | D |

- Update note on the Recommended column with text in {{rec-note}}.


# TLS Supported Groups Registry

In order to reflect the changes in the Recommended column allocation,
IANA is requested to update the TLS Supported Groups registry as follows:

- Update the registration policy to include:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D" in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Update the "Recommended" column with the changes as listed below.  Entries
  keep their existing "Y" and "N" entries except for the entries in following table.
  IANA is requested to add a reference to this document for these entries.

| Value | Curve | Recommended |
|:-|:-|-:|
| 1 |sect163k1 | D |
| 2 | sect163r1 | D |
| 3 | sect163r2 | D |
| 4 | sect193r1 | D |
| 5 | sect193r2 | D |
| 6 | sect233k1 | D |
| 7 | sect233r1 | D |
| 8 | sect239k1 | D |
| 15 | secp160k1 | D |
| 16 | secp160r1 | D |
| 17 | secp160r2 | D |
| 18 | secp192k1 | D |
| 19 | secp192r1 | D |
| 20 | secp224k1 | D |
| 21 | secp224r1 | D |

- Update note on the Recommended column with text in {{rec-note}}.

- Remove the "Elliptic curve groups" note from the registration
  procedures table.

- For each of the entries above, add the following link to the
  Comment column:
https://datatracker.ietf.org/meeting/118/materials/slides-118-tls-rfc8447bis-00


# TLS Exporter Labels Registry

This document updates the registration procedure for the TLS Exporter
Labels registry and updates the Recommended column allocation.
IANA is requested to update the TLS Exporter Labels Registry as follows:

- Change the registration procedure from Specification Required to
  Expert Review and update it to include:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D" in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Entries keep their existing Recommended column "Y" and "N" entries

- Update note on the Recommended column with text in {{rec-note}}.

- Update the note on the role of the expert reviewer as follows.

Note:
: The role of the designated expert is described in {{RFC8447, Section 17}}.
Even though this registry does not require a specification, the
designated expert {{!RFC8126}} will strongly encourage registrants
to provide a link to a publicly available specification. An
Internet-Draft (that is posted and never published as an RFC)
or a document from another standards body, industry consortium,
university site, etc. are suitable for these purposes.
The expert may provide more in-depth reviews, but their approval
should not be taken as an endorsement of the exporter label.  The
expert also verifies that the label is a string consisting of
printable ASCII characters beginning with "EXPORTER".  IANA MUST
also verify that one label is not a prefix of any other label.
For example, labels "key" or "master secretary" are forbidden.

- Rename the Note column to Comment column.

# TLS Certificate Types Registry

In order to reflect the changes in the Recommended column allocation,
IANA is requested to update the TLS Certificate Types registry as follows:

- Adjust the registration procedure related to setting the “Recommended” column as follows:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D" in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Entries keep their existing Recommended column "Y" and "N" entries.

- Update note on the Recommended column with text in {{rec-note}}.


# TLS HashAlgorithm Registry

Though TLS 1.0 and TLS 1.1 were deprecated {{!RFC8996}}, TLS 1.2 will
be in use for some time. In order to reflect the changes in the Recommended
column allocation, IANA is requested to update the TLS HashAlgorithm Registry
as follows:

- Update the registration procedure to include:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D"  in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Update the TLS HashAlgorithm registry to add a "Recommended" column
  as follows:

| Value | Description | Recommended |
|:----  |:-------------|------------:|
| 0 | none | Y |
| 1 | md5  | D |
| 2 | sha1 | D |
| 3 | sha224 | D |
| 4 | sha256 | Y |
| 5 | sha384 | Y |
| 6 | sha512 | Y |
| 8 | Intrinsic | Y |

- Add note on the Recommended column with text in {{rec-note}}.


# TLS SignatureAlgorithm Registry

Though TLS 1.0 and TLS 1.1 were deprecated {{!RFC8996}}, TLS 1.2 will
be in use for some time. In order to reflect the changes in the Recommended
column allocation, IANA is requested to update the TLS SignatureAlgorithm registry
as follows:

- Update the registration procedure to include:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D"  in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Update the TLS SignatureAlgorithm registry to add a "Recommended"
  column as follows:

|Value | Description | Recommended |
|:-----|:-------------|------------:|
| 0 | anonymous| N |
| 1 | rsa | Y |
| 2 | dsa | N |
| 3 | ecdsa | Y |
| 7 | ed25519 | Y |
| 8 | ed448 | Y |
| 64 | gostr34102012_256 | N |
| 65 | gostr34102012_512 | N |

- Add note on the Recommended column with text in {{rec-note}}.

# TLS ClientCertificateType Identifiers Registry

Though TLS 1.0 and TLS 1.1 were deprecated {{!RFC8996}}, TLS 1.2 will
be in use for some time. In order to refect the changes in the Recommended
column allocation, IANA is requested to update the TLS ClientCertificateType Identifiers
registry as follows:

- Update the registration procedure to include:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D"  in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Update the TLS ClientCertificateType Identifiers registry to add a "Recommended"
column as follows:

| Value | Description | Recommended |
|:------|:-------------|------------:|
| 1 | rsa_sign | Y |
| 2 | dss_sign | N |
| 3 | rsa_fixed_dh | N |
| 4 | dss_fixed_dh | N |
| 5 | rsa_ephemeral_dh_RESERVED | D |
| 6 | dss_ephemeral_dh_RESERVED | D |
| 20 | fortezza_dms_RESERVED | D |
| 64 | ecdsa_sign | Y |
| 65 | rsa_fixed_ecdh | N |
| 66 | ecdsa_fixed_ecdh | N |
| 67 | gost_sign256 | N |
| 68 | gost_sign512 | N |

- Add note on the Recommended column with text in {{rec-note}}.

# TLS PskKeyExchangeMode Registry

In order to reflect the changes in the Recommended column allocation,
IANA is requested to update the TLS PskKeyExchangeMode registry as follows:

- Update the registration procedure to include:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D"  in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- Add a reference to this document under the reference heading.

- Entries keep their existing Recommended column "Y" and "N" entries.

- Update note on the Recommended column with text in {{rec-note}}.

# TLS SignatureScheme Registry

In order to reflect the changes in the Recommended column allocation,
IANA is requested to update the TLS SignatureScheme registry as follows:

- Update the registration procedure to include:

~~~
    Setting a value to "Y" or "D" or transitioning the value from
    "Y" or "D"  in the "Recommended" column requires
    IETF Standards Action with Expert Review or IESG Approval [RFC8126].
~~~

- IANA is requested to add a reference to this document under the reference heading.

- Entries keep their existing Recommended column "Y" and "N" entries.

- Update note on the Recommended column with text in {{rec-note}}.

# Adding "Comment" Column

IANA is requested to add a "Comment" column to the following registries:

- TLS ExtensionType Values
- TLS Application-Layer Protocol Negotiation (ALPN) Protocol IDs
- TLS CachedInformationType Values
- TLS Certificate Compression Algorithm IDs
- TLS ClientCertificateType Identifiers
- TLS Cipher Suites
- TLS ContentType
- TLS EC Point Formats
- TLS EC Curve Types
- TLS Supplemental Data Formats (SupplementalDataType)
- TLS UserMappingType Values
- TLS Signature Algorithm
- TLS Hash Algorithm
- TLS Authorization Data Formats
- TLS Heartbeat Message Types
- TLS Heartbeat Modes
- TLS SignatureScheme
- TLS PskKeyExchangeMode
- TLS KDF Identifiers
- TLS SSLKEYLOGFILE Labels

This list of registries is all registries that do not already have a
"Comment" or "Notes" column or that were not orphaned by TLS 1.3.

IANA is requested to rename the "Note" column to "Comment" column in
TLS Exporter Labels registry.

# Expert Review of Current and Potential IETF and IRTF Documents

The intent of the Specification Required choice for TLS code points
is to allow for easy registration for code points associated with
protocols and algorithms that are not being actively developed inside
IETF or IRTF. When TLS-based technologies are being developed inside
the IRTF/IETF they should be done in coordination with the TLS WG in
order to provide appropriate review. For this reason, unless the TLS WG
chairs indicate otherwise via email, designated
experts should decline code point registrations for documents which
have already been adopted or are being proposed for adoption by IETF
working groups or IRTF research groups.

# Registration Requests

Registration requests MUST be submitted in one of two ways:

1. By sending email to iana@iana.org; this email SHOULD
use an appropriate subject (e.g., "Request to register value in TLS
bar registry").

3. Using the online form at
https://www.iana.org/form/protocol-assignment.

Specification Required {{RFC8126}} registry requests are registered after
a three-week review period on the advice of one or more designated
experts. However, to allow for the allocation of values prior to
publication, the designated experts may approve registration once they
are satisfied that such a specification will be published.

# Security Considerations

Recommended algorithms are regarded as secure for general use at the
time of registration; however, cryptographic algorithms and parameters
will be broken or weakened over time.  It is possible that the
"Recommended" status in the registry lags behind the most recent advances
in cryptanalysis.  Implementers and users need to check that the
cryptographic algorithms listed continue to provide the expected level
of security.

Designated experts ensure the specification is publicly available.  They may
provide more in-depth reviews.  Their review should not be taken as an
endorsement of the cipher suite, extension, supported group, etc.


# IANA Considerations

This document is entirely about changes to TLS-related IANA registries.

IANA is requested to modify the note applied to all TLS Specification
Required registries instructing where to send registration requests as
follows:

<aside markdown="block">
  RFC EDITOR: Please replace "This RFC" in the following with the RFC number
  assigned to this specification.
</aside>

Requests for assignments from the registry's Specification Required
range should be sent to the mailing list described in [This RFC, Section 16].
If approved, designated experts should notify IANA within three weeks. For
assistance, please contact iana@iana.org.

--- back
