---
title: IANA Registry Updates for TLS and DTLS
abbrev: (D)TLS IANA Registry Updates
docname: draft-ietf-tls-rfc8447bis-latest
category: std
obsoletes: 8447
updates: 3749, 5077, 4680, 5246, 5705, 5878, 6520, 7301
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
    organization: Salesforce
    email: joe@salowey.net
 -
    ins: S. Turner
    name: Sean Turner
    organization: sn3rd
    email: sean@sn3rd.com

normative:

informative:

--- abstract

This document describes a number of changes to TLS and DTLS IANA registries
that range from adding notes to the registry all the way to changing
the registration policy.  These changes were mostly motivated by WG
review of the TLS- and DTLS-related registries undertaken as part of the
TLS 1.3 development process.

This document obsoletes RFC 8447 and updates the following RFCs:
3749, 5077, 4680, 5246, 5705, 5878, 6520, and 7301.

--- middle

# Introduction

This document instructs IANA to make changes to a number of the IANA
registries related to Transport Layer Security (TLS) and Datagram
Transport Layer Security (DTLS).

<aside markdown="block">
  NOTE for IANA: Where we make new changes we used [SHALL / has].
  Otherwise, we left it as has, i.e., it matches the text in
  {{?RFC8447}}.
</aside>

Most of the instructions included herein and previously included in
{{?RFC8447}}, which this document obsoletes, were motivated by the
development of TLS 1.3 {{?RFC8446}}. The changes ranged from simple,
e.g., adding notes, to complex, e.g., changing a registry's registration
policy. Instead of listing the changes and their rationale here in the
introduction, each section provides rationale for the proposed
change(s). The instructions in this document revise the values of
"Recommended" column, applies the new value to the registries, and adds
this column as noted in {{orphaned-registries}}. There are also instructions to
update references, including replacing references to {{?RFC8446}} with
{{!I-D.ietf-tls-rfc8446bis}} and {{?RFC8447}} with {{!I-D.ietf-tls-rfc8447bis}}.

This document proposes no changes to the registration policies for TLS
Alerts {{!I-D.ietf-tls-rfc8446bis}}, TLS ContentType {{!I-D.ietf-tls-rfc8446bis}},
TLS HandshakeType {{!I-D.ietf-tls-rfc8446bis}}, and TLS Certificate Status
Types {{?RFC6961}} registries; the existing policies (Standards Action
for the first three; IETF Review for the last), are appropriate for
these one-byte code points because of their scarcity.

# Terminology

{::boilerplate bcp14-tagged}

# Adding "TLS" to Registry Names

For consistency amongst TLS registries, IANA
has prepended "TLS" to the following registries:

- Application-Layer Protocol Negotiation (ALPN) Protocol IDs {{!RFC7301}},
- ExtensionType Values,
- Heartbeat Message Types {{!RFC6520}}, and
- Heartbeat Modes {{RFC6520}}.

IANA [SHALL update/has updated] the reference for these four registries
to also refer to this document.  The remainder of this document will
use the registry names with the "TLS" prefix.

# Aligning with RFC 8126

Many of the TLS-related IANA registries had the registration procedure
"IETF Consensus", which was changed to "IETF Review" by {{!RFC8126}}.
To align with the new terminology, IANA has updated the following
registries to "IETF Review":

- TLS Authorization Data Formats {{!RFC4680}}
- TLS Supplemental Data Formats (SupplementalDataType) {{!RFC5878}}

This is not a universal change, as some registries originally defined
with "IETF Consensus" are undergoing other changes either as a result
of this document or {{?RFC8422}}.

IANA [SHALL update/has updated] the reference for these two registries
to also refer to this document.

# Adding "Recommended" Column

The instructions in this document update the Recommended column,
originally added in {{?RFC8447}} to add a third value, "D",
indicating that a value is "Discouraged". The permitted values
are:

- Y: Indicates that the IETF has consensus that the
    item is RECOMMENDED. This only means that the associated
    mechanism is fit for the purpose for which it was defined.
    Careful reading of the documentation for the mechanism is
    necessary to understand the applicability of that mechanism.
    The IETF could recommend mechanisms that have limited
    applicability, but will provide applicability statements that
    describe any limitations of the mechanism or necessary constraints
    on its use.
- N: Indicates that the item has not been evaluated by
    the IETF and that the IETF has made no statement about the
    suitability of the associated mechanism. This does not necessarily
    mean that the mechanism is flawed, only that no consensus exists.
    The IETF might have consensus to leave an items marked as "N" on
    the basis of it having limited applicability or usage constraints.
- D: Indicates that the item is discouraged and SHOULD
    NOT or MUST NOT be used. This marking could be used to identify
    mechanisms that might result in problems if they are used, such as
    a weak cryptographic algorithm or a mechanism that might cause
    interoperability problems in deployment.

Setting the Recommended item to "Y" or "D" or changing a
item whose current value is "Y" or "D" requires Standards Action {{!RFC8126}}.
Not all items defined in Standards Track RFCs need to be
marked as Recommended. Changing the Recommended status of an item in a
Standards Track RFC requires Standards Action {{!RFC8126}}.

<aside markdown="block">
  Note: the registries in the rest of the document will need to have the
  recommended column updated appropriately, specifically to deprecate MD5
  and SHA-1, etc.
</aside>

# Session Ticket TLS Extension

The nomenclature for the registry entries in the TLS ExtensionType
Values registry correspond to the presentation language field name
except for entry 35.  To ensure that the values in the registry are
consistently identified in the registry, IANA:

- has renamed entry 35 to "session_ticket (renamed from
  "SessionTicket TLS")" {{!RFC5077}}.

- [SHALL replace/has replaced] the reference to {{?RFC8447}} with a
  reference to this document in the "Reference" column for entry 35.

# TLS ExtensionType Values

Experience has shown that the IETF Review registry policy for TLS
extensions was too strict.  Based on WG consensus, the decision was
taken to change the registration policy to Specification Required
while reserving a small part of the code space for Private Use
{{!RFC8126}}.  Therefore, IANA [SHALL update/has updated] the TLS
ExtensionType Values registry as follows:

- Changed the registry policy to:

~~~
    Values with the first byte in the range 0-254 (decimal) are assigned
    via Specification Required [RFC8126].  Values with the first byte
    255 (decimal) are reserved for Private Use [RFC8126].
~~~

- Updated the "Reference" to refer to this document instead of {{?RFC8447}}.

See {{expert-pool}} for additional information about the designated
expert pool.

Despite wanting to "loosen" the registration policies for TLS
extensions, it is still useful to indicate in the IANA registry which
extensions the WG recommends be supported.  Therefore, IANA [SHALL
update/has updated] the TLS ExtensionType Values registry as follows:

- Add a "Recommended" column with the contents as listed below.  This
  table has been generated by marking Standards Track RFCs as "Y",
  "truncated_hmac" (4) and "connection_id (deprecated)" (53) as "D",
  and all others as "N". The "Recommended" column is assigned a
  value of "N" unless explicitly requested, and adding a value with
  a "Recommended" value of "Y" requires Standards Action {{!RFC8126}}.
  IESG Approval is REQUIRED for a Y->N, Y->D, and D->Y|N transitions.

<aside markdown="block">
  Note: Should we also mark the Reserved 40 and 46 as "D"?
</aside>

| Extension                                | Recommended |
|:-----------------------------------------|------------:|
| server_name                     |         Y |
| max_fragment_length             |         N |
| client_certificate_url          |         Y |
| trusted_ca_keys                 |         Y |
| truncated_hmac                  |         D |
| status_request                  |         Y |
| user_mapping                    |         Y |
| client_authz                    |          N |
| server_authz                    |          N |
| cert_type                       |          N |
| supported_groups                |         Y |
| ec_point_formats                |         Y |
| srp                             |          N |
| signature_algorithms            |         Y |
| use_srtp                        |         Y |
| heartbeat                       |         Y |
| application_layer_protocol_negotiation  | Y |
| status_request_v2               |         Y |
| signed_certificate_timestamp    |          N |
| client_certificate_type         |         Y |
| server_certificate_type         |         Y |
| padding                         |         Y |
| encrypt_then_mac                |         Y |
| extended_master_secret          |         Y |
| cached_info                     |         Y |
| session_ticket                  |         Y |
| renegotiation_info              |         Y |
| connection_id (deprecated)      |         D |

IANA [SHALL update/has added] the following notes:

Note:
: The role of the designated expert is described in {{!I-D.ietf-tls-rfc8447bis}}.
The designated expert {{!RFC8126}} ensures that the specification is
publicly available.  It is sufficient to have an Internet-Draft (that
is posted and never published as an RFC) or a document from another
standards body, industry consortium, university site, etc.  The expert
may provide more in-depth reviews, but their approval should not be
taken as an endorsement of the extension.

Note:
: As specified in {{!RFC8126}}, assignments made in the Private Use
space are not generally useful for broad interoperability.  It is
the responsibility of those making use of the Private Use range to
ensure that no conflicts occur (within the intended scope of use).
For widespread experiments, temporary reservations are available.

Note:
: If an item is not marked as "Recommended", it does not necessarily mean
that it is flawed; rather, it indicates that the item either has not
been through the IETF consensus process, has limited applicability, or
is intended only for specific use cases.

The extensions added by {{!I-D.ietf-tls-rfc8446bis}} are omitted from the
above table. Likewise, extensions defined after {{?RFC8447}} are also not
listed in the table as those RFCs specify the value of the extension's
"Recommended"; extensions points defined after {{?RFC8447}} include
token_binding, compress_certificate, record_size_limit, pwd_protect,
pwd_clear, password_salt, ticket_pinning, tls_cert_with_extern_psk,
delegated_credentials, supported_ekt_ciphers, connection_id,
external_id_hash, external_session_id, quic_transport_parameters,
ticket_request, and dnssec_chain.

{{!I-D.ietf-tls-rfc8446bis}} also uses the TLS ExtensionType Values
registry originally created in {{?RFC4366}}. The following text is
from {{!I-D.ietf-tls-rfc8446bis}} and is included here to ensure
alignment between these specifications.

-  IANA [SHALL update/has updated] this registry to include the
   "key_share", "pre_shared_key", "psk_key_exchange_modes",
   "early_data", "cookie", "supported_versions",
   "certificate_authorities", "oid_filters", "post_handshake_auth",
   and "signature_algorithms_cert", extensions with the values
   defined in {{!I-D.ietf-tls-rfc8446bis}} and the "Recommended" value of "Y".

-  IANA [SHALL update/has updated] this registry to include a "TLS
   1.3" column that lists the messages in which the extension may
   appear.  This column [SHALL be/has been] initially populated from
   the table in Section 4.2 of {{!I-D.ietf-tls-rfc8446bis}} with any
   extension not listed there marked as "-" to indicate that it is not
   used by TLS 1.3.

# TLS Cipher Suites Registry

<aside markdown="block">
  Note: Review in light of {{!I-D.ietf-tls-deprecate-obsolete-kex}}.
</aside>

Experience has shown that the IETF Consensus registry policy for TLS
Cipher Suites was too strict.  Based on WG consensus, the decision was
taken to change the TLS Cipher Suites registry's registration policy
to Specification Required while reserving a small part of the code
space for Experimental and Private Use {{!RFC8126}}.  Therefore, IANA
has updated the TLS Cipher Suites registry's policy as follows:

~~~
    Values with the first byte in the range 0-254 (decimal) are
    assigned via Specification Required [RFC8126].  Values with the
    first byte 255 (decimal) are reserved for Private Use [RFC8126].
~~~

See {{expert-pool}} for additional information about the designated
expert pool.

The TLS Cipher Suites registry has grown significantly and will continue to
do so.  To better guide those not intimately involved in TLS, IANA
[SHALL update/has updated] the TLS Cipher Suites registry as follows:

<aside markdown="block">
  The following text needs to be update to reflect the new recommended policy.
</aside>

- Added a "Recommended" column to the TLS Cipher Suites registry.  The
  cipher suites that follow in the two tables are marked as "Y".
  All other cipher suites are marked as "N".  The "Recommended"
  column is assigned a value of "N" unless explicitly requested, and
  adding a value with a "Recommended" value of "Y" requires
  Standards Action {{!RFC8126}}.  IESG Approval is REQUIRED for a Y->N
  transition.

  The cipher suites that follow are Standards Track server-authenticated
  (and optionally client-authenticated) cipher suites that are
  currently available in TLS 1.2.

RFC EDITOR: The previous paragraph is for document reviewers and is not
meant for the registry.

~~~
Cipher Suite Name                             | Value
----------------------------------------------+------------
TLS_DHE_RSA_WITH_AES_128_GCM_SHA256           | {0x00,0x9E}
TLS_DHE_RSA_WITH_AES_256_GCM_SHA384           | {0x00,0x9F}
TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256       | {0xC0,0x2B}
TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384       | {0xC0,0x2C}
TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256         | {0xC0,0x2F}
TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384         | {0xC0,0x30}
TLS_DHE_RSA_WITH_AES_128_CCM                  | {0xC0,0x9E}
TLS_DHE_RSA_WITH_AES_256_CCM                  | {0xC0,0x9F}
TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256   | {0xCC,0xA8}
TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 | {0xCC,0xA9}
TLS_DHE_RSA_WITH_CHACHA20_POLY1305_SHA256     | {0xCC,0xAA}
~~~

  The cipher suites that follow are Standards Track ephemeral pre-shared
  key cipher suites that are available in TLS 1.2.

RFC EDITOR: The previous paragraph is for document reviewers and is not
meant for the registry.

~~~
Cipher Suite Name                             | Value
----------------------------------------------+------------
TLS_DHE_PSK_WITH_AES_128_GCM_SHA256           | {0x00,0xAA}
TLS_DHE_PSK_WITH_AES_256_GCM_SHA384           | {0x00,0xAB}
TLS_DHE_PSK_WITH_AES_128_CCM                  | {0xC0,0xA6}
TLS_DHE_PSK_WITH_AES_256_CCM                  | {0xC0,0xA7}
TLS_ECDHE_PSK_WITH_AES_128_GCM_SHA256         | {0xD0,0x01}
TLS_ECDHE_PSK_WITH_AES_256_GCM_SHA384         | {0xD0,0x02}
TLS_ECDHE_PSK_WITH_AES_128_CCM_SHA256         | {0xD0,0x05}
TLS_ECDHE_PSK_WITH_CHACHA20_POLY1305_SHA256   | {0xCC,0xAC}
TLS_DHE_PSK_WITH_CHACHA20_POLY1305_SHA256     | {0xCC,0xAD}
~~~

The TLS 1.3 cipher suites specified by {{!I-D.ietf-tls-rfc8446bis}} are
not listed here; that document provides for their "Recommended" status.

Despite the following behavior being misguided, experience has shown
that some customers use the IANA registry as a checklist against which
to measure an implementation's completeness, and some implementers
blindly implement cipher suites.  Therefore, IANA has added the
following warning to the registry:

WARNING:
: Cryptographic algorithms and parameters will be broken or weakened
over time.  Blindly implementing cipher suites listed here is not
advised.  Implementers and users need to check that the cryptographic
algorithms listed continue to provide the expected level of security.

IANA has added the following note to ensure that those that focus on
IANA registries are aware that TLS 1.3 {{!I-D.ietf-tls-rfc8446bis}}
uses the same registry but defines ciphers differently:

Note:
: Although TLS 1.3 uses the same cipher suite space as previous
versions of TLS, TLS 1.3 cipher suites are defined differently, only
specifying the symmetric ciphers and hash functions, and cannot be
used for TLS 1.2.  Similarly, TLS 1.2 and lower cipher suite values
cannot be used with TLS 1.3.

IANA [SHALL add/has added] the following notes to document the rules
for populating the "Recommended" column:

Note:
: CCM_8 cipher suites are not marked as "Recommended".  These cipher
suites have a significantly truncated authentication tag that represents
a security trade-off that may not be appropriate for general
environments.

Note:
: If an item is not marked as "Recommended", it does not necessarily mean
that it is flawed; rather, it indicates that the item either has not
been through the IETF consensus process, has limited applicability, or
is intended only for specific use cases.

IANA [SHALL add/has added] the following notes for additional
information:

Note:
: The role of the designated expert is described in {{!I-D.ietf-tls-rfc8447bis}}.
The designated expert {{!RFC8126}} ensures that the specification is
publicly available.  It is sufficient to have an Internet-Draft (that
is posted and never published as an RFC) or a document from another
standards body, industry consortium, university site, etc.  The expert
may provide more in-depth reviews, but their approval should not be
taken as an endorsement of the cipher suite.

Note:
: As specified in {{!RFC8126}}, assignments made in the Private Use
space are not generally useful for broad interoperability.  It is the
responsibility of those making use of the Private Use range to ensure
that no conflicts occur (within the intended scope of use).  For
widespread experiments, temporary reservations are available.

IANA [SHALL update/has updated] the reference for this registry to
refer to this document instead of {{RFC8447}}.

# TLS Supported Groups

Similar to cipher suites, supported groups have proliferated over time,
and some use the registry to measure implementations.  Therefore, IANA
[SHALL add/has added] a ???Recommended??? column with a "Y" for secp256r1,
secp384r1, x25519, and x448, while all others are "N".  These "Y"
groups are taken from Standards Track RFCs; {{?RFC8422}} elevates
secp256r1 and secp384r1 to Standards Track.  Not all groups from
{{?RFC8422}}, which is Standards Track, are marked as "Y"; these groups
apply to TLS 1.3 {{!I-D.ietf-tls-rfc8446bis}} and previous versions of
TLS.  The "Recommended" column is assigned a value of "N" unless
explicitly requested, and adding a value with a "Recommended" value of "Y"
requires Standards Action {{!RFC8126}}.  IESG Approval is
REQUIRED for a Y->N transition.

IANA [SHALL add/has added] the following notes:

Note:
: If an item is not marked as "Recommended" it does not necessarily mean
that it is flawed; rather, it indicates that the item either has not
been through the IETF consensus process, has limited applicability, or
is intended only for specific use cases.

Note:
: The role of the designated expert is described in {{!I-D.ietf-tls-rfc8447bis}}.
The designated expert {{!RFC8126}} ensures that the specification is
publicly available.  It is sufficient to have an Internet-Draft (that
is posted and never published as an RFC) or a document from another
standards body, industry consortium, university site, etc.  The expert
may provide more in-depth reviews, but their approval should not be
taken as an endorsement of the supported groups.

Despite the following behavior being misguided, experience has shown
that some customers use the IANA registry as a checklist against which
to measure an implementation's completeness, and some implementers
blindly implement supported group.  Therefore, IANA has added the
following warning to the registry:

WARNING:
: Cryptographic algorithms and parameters will be broken or weakened
over time.  Blindly implementing supported groups listed here is not
advised.  Implementers and users need to check that the cryptographic
algorithms listed continue to provide the expected level of security.

IANA [SHALL update/has updated] the reference for this registry to
refer to this document instead of {{?RFC8447}}.

The value 0 (0x0000) has been marked as reserved.

# TLS ClientCertificateType Identifiers

Experience has shown that the IETF Consensus registry policy for TLS
ClientCertificateType Identifiers is too strict.  Based on WG
consensus, the decision was taken to change the registration policy to
Specification Required while reserving some of the code
space for Standards Track usage and a small part of the code space
for Private Use {{!RFC8126}}.  Therefore, IANA has updated the TLS
ClientCertificateType Identifiers registry's policy as follows:

~~~~
      Values in the range 0-63 are assigned via Standards Action [RFC8126].
      Values 64-223 are assigned via Specification Required [RFC8126].
      Values 224-255 are reserved for Private Use [RFC8126].
~~~~

See {{expert-pool}} for additional information about the designated
expert pool.

IANA [SHALL add/has added] the following notes:

Note:
: The role of the designated expert is described in {{!I-D.ietf-tls-rfc8447bis}}.
The designated expert {{!RFC8126}} ensures that the specification is
publicly available.  It is sufficient to have an Internet-Draft
(that is posted and never published as an RFC) or a document from
another standards body, industry consortium, university site, etc.
The expert may provide more in-depth reviews, but their approval
should not be taken as an endorsement of the identifier.

Note:
: As specified in {{!RFC8126}}, assignments made in the Private Use
space are not generally useful for broad interoperability.  It is
the responsibility of those making use of the Private Use range to
ensure that no conflicts occur (within the intended scope of use).
For widespread experiments, temporary reservations are available.

# New Session Ticket TLS Handshake Message Type

To align with TLS implementations and to align the naming nomenclature
with other Handshake message types, IANA:

- has renamed entry 4 in the TLS HandshakeType registry to
"new_session_ticket (renamed from NewSessionTicket)" {{!RFC5077}}.

- [SHALL replace/has replaced] a reference to {{?RFC8447}} with a
reference to this document in the "Reference" column for entry 4 in
the TLS HandshakeType registry.

# TLS Exporter Labels Registry

To aid those reviewers who start with the IANA registry, IANA [SHALL
add/has added]:

- The following note to the TLS Exporter Labels registry:

    Note:
    : {{!RFC5705}} defines keying material exporters for TLS in terms of
    the TLS PRF.  {{!I-D.ietf-tls-rfc8446bis}} replaced the PRF with HKDF, thus
    requiring a new construction. The exporter interface remains the same;
    however, the value is computed differently.

- A "Recommended" column to the TLS Exporter Labels registry.  The table
that follows has been generated by marking Standards Track RFCs as "Y" and
all others as "N".  The "Recommended" column is assigned a value of "N"
unless explicitly requested, and adding a value with a "Recommended" value
of "Y" requires Standards Action {{!RFC8126}}. IESG Approval is REQUIRED for a
Y->N, Y->D, or D->Y|N transitions.

| Exporter Value                 | Recommended |
|:------------------------------:|:-----------:|
client finished                 |         Y |
server finished                 |         Y |
master secret                   |         Y |
key expansion                   |         Y |
client EAP encryption           |         Y |
ttls keying material            |         N |
ttls challenge                  |         N |
EXTRACTOR-dtls_srtp             |         Y |
EXPORTER_DTLS_OVER_SCTP         |         Y |
EXPORTER: teap session key seed |         Y |

To provide additional information for the designated experts, IANA
[SHALL add/has added] the following notes:

Note:
: The role of the designated expert is described in {{!I-D.ietf-tls-rfc8447bis}}.
The designated expert {{!RFC8126}} ensures that the specification is
publicly available.  It is sufficient to have an Internet-Draft
(that is posted and never published as an RFC) or a document from
another standards body, industry consortium, university site, etc.
The expert may provide more in-depth reviews, but their approval
should not be taken as an endorsement of the exporter label.  The
expert also verifies that the label is a string consisting of
printable ASCII characters beginning with "EXPORTER".  IANA MUST
also verify that one label is not a prefix of any other label.
For example, labels "key" or "master secretary" are forbidden.

Note:
: If an item is not marked as "Recommended", it does not
necessarily mean that it is flawed; rather, it indicates that the
item either has not been through the IETF consensus process, has
limited applicability, or is intended only for specific use cases.

IANA [SHALL update/has updated] the reference for this registry to refer
to refer to this document instead of {{?RFC8447}}.

# Adding Missing Item to TLS Alerts Registry

IANA has added the following entry to the TLS Alerts registry;
the entry was omitted from the IANA instructions in {{!RFC7301}}:

~~~
    120   no_application_protocol  Y  [RFC7301][This-document]
~~~

# TLS Certificate Types

Experience has shown that the IETF Consensus registry policy for TLS
Certificate Types is too strict.  Based on WG consensus, the decision
was taken to change registration policy to Specification Required
while reserving a small part of the code space for Private Use {{!RFC8126}}.
Therefore, IANA has changed the TLS Certificate Types registry as follows:

- Changed the registry policy to:

~~~
    Values in the range 0-223 (decimal) are assigned via Specification
    Required [RFC8126]. Values in the range 224-255 (decimal) are
    reserved for Private Use [RFC8126].
~~~

- Added a "Recommended" column to the registry.  X.509 and Raw
  Public Key are "Y".  All others are "N".  The "Recommended" column
  is assigned a value of "N" unless explicitly requested, and adding
  a value with a "Recommended" value of "Y" requires Standards
  Action {{!RFC8126}}.  IESG Approval is REQUIRED for
  a Y->N, Y->D, and D->Y|N transitions.

See {{expert-pool}} for additional information about the designated
expert pool.

IANA [SHALL add/has added] the following note:

Note:
: The role of the designated expert is described in {{!I-D.ietf-tls-rfc8447bis}}.
The designated expert {{!RFC8126}} ensures that the specification is
publicly available.  It is sufficient to have an Internet-Draft
(that is posted and never published as an RFC) or a document from
another standards body, industry consortium, university site, etc.
The expert may provide more in-depth reviews, but their approval
should not be taken as an endorsement of the certificate type.

Note:
: If an item is not marked as "Recommended", it does not
necessarily mean that it is flawed; rather, it indicates that the
item either has not been through the IETF consensus process, has
limited applicability, or is intended only for specific use cases.

IANA [SHALL update/has updated] the reference for this registry to
refer this document instead of {{?RFC8447}}.

# Orphaned Registries

To make it clear that (D)TLS 1.3 has orphaned certain registries (i.e.,
they are only applicable to version of (D)TLS protocol versions prior
to 1.3), IANA:

- has added the following to the TLS Compression Method Identifiers
  registry {{!RFC3749}}:

    Note:
    : Value 0 (NULL) is the only value in this registry applicable to (D)TLS
    protocol version 1.3 or later.

- has added the following to the TLS HashAlgorithm {{!RFC5246}}
  and TLS SignatureAlgorithm registries {{!RFC5246}}:

    Note:
    : The values in this registry are only applicable to (D)TLS protocol
    versions prior to 1.3.  (D)TLS 1.3 and later versions' values are
    registered in the TLS SignatureScheme registry.

- [SHALL update/has updated] the "Reference" field in the TLS
  Compression Method Identifiers, TLS HashAlgorithm and TLS
  SignatureAlgorithm registries to refer to this document instead of
  {{?RFC8447}}.

- has updated the TLS HashAlgorithm registry to list
  values 7 and 9-223 as "Reserved" and the TLS SignatureAlgorithm
  registry to list values 4-6 and 9-223 as "Reserved".

- has added the following to the TLS ClientCertificateType
  Identifiers registry {{!RFC5246}}:

    Note:
    : The values in this registry are only applicable to (D)TLS
    protocol versions prior to 1.3.

Despite the fact that the TLS HashAlgorithm and SignatureAlgorithm
registries are orphaned, it is still important to warn implementers
of pre-TLS1.3 implementations about the dangers of blindly
implementing cryptographic algorithms.  Therefore, IANA has added the
following warning to the TLS HashAlgorithm and SignatureAlgorithm
registries:

WARNING:
: Cryptographic algorithms and parameters will be broken or weakened
over time.  Blindly implementing the cryptographic algorithms listed
here is not advised.  Implementers and users need to check that the
cryptographic algorithms listed continue to provide the expected level
of security.

Though TLS 1.0 and TLS 1.1 were deprecated {{!RFC8996}}, TLS 1.2 will
be in use for some time. IANA [SHALL update/has updated] the TLS
HashAlgorithm, TLS SignatureAlgorithm, and TLS ClientCertificateTypes
registries to add a "Recommended" column as follows:

TLS HashAlgorithm registry:

| Descsription | Recommended |
|:-------------|------------:|
| none | Y |
| md5  | D |
| sha1 | D |
| sha224 | D |
| sha256 | Y |
| sha384 | Y |
| sha512 | Y |
| Intrinsic | Y |

TLS SignatureAlgorithm registry:

| Descsription | Recommended |
|:-------------|------------:|
| anonymous| N |
| rsa | Y |
| dsa | N |
| ecdsa | Y |
| ed25519 | Y |
| ed448 | Y |
| gostr34102012_256 | N |
| gostr34102012_512 | N |

TLS ClientCertificateTypes registry:

| Descsription | Recommended |
|:-------------|------------:|
| rsa_sign | Y |
| dss_sign | N |
| rsa_fixed_dh | N |
| dss_fixed_dh | N |
| rsa_ephemeral_dh_RESERVED | D |
| dss_ephemeral_dh_RESERVED | D |
| fortezza_dms_RESERVED | D |
| ecdsa_sign | Y |
| rsa_fixed_ecdh | N |
| ecdsa_fixed_ecdh | N |
| gost_sign256 | N |
| gost_sign512 | N |

In the TLS HashAlgorithm, TLS SignatureAlgorithm, and TLS
ClientCertificateTypes registries, all unassigned and reserved values
have a "Recommended" that is blank.

# Additional Notes {#Notes}

IANA has added the following warning and note to the TLS
SignatureScheme registry:

WARNING:
: Cryptographic algorithms and parameters will be broken or
weakened over time.  Blindly implementing signature schemes listed
here is not advised.  Implementers and users need to check that
the cryptographic algorithms listed continue to provide the
expected level of security.

Note:
: As specified in {{!RFC8126}}, assignments made in the Private Use
space are not generally useful for broad interoperability.  It is
the responsibility of those making use of the Private Use range to
ensure that no conflicts occur (within the intended scope of use).
For widespread experiments, temporary reservations are available.

IANA [SHALL update/has updated] added the following notes to the
TLS PskKeyExchangeMode registry:

Note:
: If an item is not marked as "Recommended", it does not
necessarily mean that it is flawed; rather, it indicates that the
item either has not been through the IETF consensus process, has
limited applicability, or is intended only for specific use cases.

Note:
: The role of the designated expert is described in {{!I-D.ietf-tls-rfc8447bis}}.
The designated expert {{!RFC8126}} ensures that the specification is
publicly available.  It is sufficient to have an Internet-Draft
(that is posted and never published as an RFC) or a document from
another standards body, industry consortium, university site, etc.
The expert may provide more in depth reviews, but their approval
should not be taken as an endorsement of the key exchange mode.

# Designated Expert Pool {#expert-pool}

Specification Required {{!RFC8126}} registry requests are registered
after a three-week review period on the <tls-reg-review@ietf.org>
mailing list, on the advice of one or more designated experts.
However, to allow for the allocation of values prior to publication,
the designated experts may approve registration once they are
satisfied that such a specification will be published.

Registration requests sent to the mailing list for review SHOULD use an
appropriate subject (e.g., "Request to register value in TLS bar
registry").

Within the review period, the designated experts will either approve or
deny the registration request, communicating this decision to the review
list and IANA.  Denials SHOULD include an explanation and, if applicable,
suggestions as to how to make the request successful.  Registration
requests that are undetermined for a period longer than 21 days can be
brought to the IESG's attention (using the <iesg@ietf.org> mailing list)
for resolution.

Criteria that SHOULD be applied by the designated experts includes
determining whether the proposed registration duplicates existing
functionality, whether it is likely to be of general applicability
or useful only for a single application, and whether the registration
description is clear.

IANA MUST only accept registry updates from the designated experts and
SHOULD direct all requests for registration to the review mailing list.

It is suggested that multiple designated experts be appointed who are
able to represent the perspectives of different applications using this
specification, in order to enable broadly informed review of
registration decisions.  In cases where a registration decision could
be perceived as creating a conflict of interest for a particular
Expert, that Expert SHOULD defer to the judgment of the other Experts.

# Security Considerations

The change to Specification Required from IETF Review lowers the amount
of review provided by the WG for cipher suites and supported groups.
This change reflects reality in that the WG essentially provided no
cryptographic review of the cipher suites or supported groups.  This
was especially true of national cipher suites.

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


--- back
