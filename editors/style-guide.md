

# HTTP Editorial Style Guide

This page collects guidance for HTTP specification editors, to promote consistency and ease of use for the document set. **HTTP WG document editors should follow these guidelines** and reference this document when asked by the RFC Editor Production Center.

See also the [RFC Editor style guide](https://www.rfc-editor.org/styleguide/).

**NOTE**: This guide is always being improved; discuss improvements to it on the [issues list](https://github.com/httpwg/admin/labels/style-guide).

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Terminology](#terminology)
- [Header and Trailer Fields](#header-and-trailer-fields)
  - [Structured Fields](#structured-fields)
- [Content](#content)
- [Methods](#methods)
- [Status Codes](#status-codes)
- [Example Messages](#example-messages)
- [Reference Style](#reference-style)
- [Not HTTP Specific](#not-http-specific)
  - [Creating and Modifying Registries](#creating-and-modifying-registries)
  - [Self-References](#self-references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## Terminology

Terminology should always be consistent with the core documents:

* [RFC 9110](https://httpwg.org/specs/rfc9110.html) - HTTP Semantics
* [RFC 9111](https://httpwg.org/specs/rfc9111.html) - HTTP Caching
* [RFC 9112](https://httpwg.org/specs/rfc9112.html) - HTTP/1.1
* [RFC 9113](https://httpwg.org/specs/rfc9113.html) - HTTP/2

## Header and Trailer Fields

When defining a field, the first instance should be quoted; e.g.,

> This document defines the "Foo" response header field.

If the field is specific to headers, trailers, requests, and/or responses, the definition should include the relevant terms, as above.

When referring to a field defined in a different document, the first instance should include a reference, and all instances should be unquoted. For example:

> Add the Foo-Example header field (see {% raw %}{{RFCxxxx}}){% endraw %} to the response.

Subsequent occurrences should be unquoted, but always be followed by "field", "header field", or "trailer field" as appropriate.

See also [Considerations for New Fields](https://httpwg.org/specs/rfc9110.html#considerations.for.new.fields).

### Structured Fields

Most HTTP headers defined by the Working Group should be [Structured Fields](https://httpwg.org/specs/rfc8941.html). This isn't an official policy, but many folks argue for them. 

When specifying a Structured Field in prose, preferred practice is to add the following to your "Notational Conventions" section:

~~~ markdown
This document uses the following terminology from {% raw %}{{Section 3 of STRUCTURED-FIELDS}}{% endraw %}
to specify syntax and parsing: List, Dictionary, and Integer.
~~~

adjusting the terms listed as appropriate. Then, when using one of the terms, just use the bare, capitalised term; e.g.,

> The Foo header field's value is a List of Integers.

All references to structured types should be made to [Section 3](https://httpwg.org/specs/rfc8941.html#rfc.section.3) of the Structured Fields specification, **not** Section 4.

Although ABNF is defined for structured types, we do not recommend its use.


## Content

Use 'content', not 'body' or 'payload'.


## Methods

Just use the bare method name (without quotes or emphasis); e.g.,

> Send a request with the GET method.

Stating that it is a HTTP method is optional; this is equally acceptable:

> Send a GET request.

See also [Considerations for New Methods](https://httpwg.org/specs/rfc9110.html#considerations.for.new.methods).


## Status Codes

Use the bare status code number, followed by the reason phrase in parentheses. For example:

> The 500 (Internal Server Error) status code.

When referring to multiple individual status codes, the reason phrase can be omitted; for example:

> If the status code is 200, 202, or 204, proceed.

To refer to a range of status codes, use "xx" notation:

> The 4xx range of status codes.

When discussing status codes in general, the correct reference is [Section 15 of HTTP](https://httpwg.org/http-core/draft-ietf-httpbis-semantics-latest.html#status.codes). Use 'status code', not 'Status Code'.

See also [Considerations for New Status Codes](https://httpwg.org/specs/rfc9110.html#considerations.for.new.status.codes).


## Example Messages

If your specification has examples of HTTP messages (and it probably should), they should give enough context for readers to understand. Generally, this means showing a substantial portion of the message; e.g., not just a header field in isolation, but an entire request or response message (with a truncated body). Where appropriate, an entire exchange (request and response) can be illustrated using two subsequent example sections.

Examples should be in HTTP/1.1 format unless they are specific to another version of the protocol. HTTP/1.1 examples should be labeled with the `http-message` type so that the [validator](https://github.com/mnot/rfc-http-validate) can check them.

For example (in Markdown):

    ~~~ http-message
    HTTP/1.1 200 OK
    Content-Type: text/plain
    Example-Header: foo

    [ content ]
    ~~~

Examples with long lines (over 78 characters) should be wrapped using the line folding convention where possible. For example:

    ~~~ http-message
    HTTP/1.1 200 OK
    Content-Type: text/plain
    Example-Header: this content is very long so we
       fold it to the next line and indent

    [ content ]
    ~~~

If the too-long content cannot include whitespace, use [RFC8792](https://www.rfc-editor.org/rfc/rfc8792.html) encoding:

    ~~~ http-message
    # NOTE: '\' line wrapping per RFC 8792

    HTTP/1.1 200 OK
    Content-Type: text/plain
    Example-Header: abcedfghijlkmnopqrstuvwxyzabcedfghijlkmnopqrstuvwxyzabc\
         edfghijlkmnopqrstuvwxyz

    [ content ]
    ~~~

Note that the notice header has to occur on each section that uses this encoding.


## Reference Style

Generally, named references are preferred for "core" specifications like HTTP and TLS. In addition to giving readers a cue about the purpose of the reference, this is a small hint that the RFC number is not the identifier they should be remembering. For example:

~~~ markdown
{% raw %}This document defines a HTTP {{HTTP}} header field that uses the conventions
in {{STRUCTURED-FIELDS}} to convey information about the TLS ({{TLS}}) session.{% endraw %}
~~~

The following reference names are preferred:

* `HTTP` - [HTTP Semantics](https://httpwg.org/http-core/draft-ietf-httpbis-semantics-latest.html)
* `HTTP-CACHING` - [HTTP Caching](https://httpwg.org/http-core/draft-ietf-httpbis-cache-latest.html)
* `HTTP/1.1` - [HTTP/1.1](https://httpwg.org/http-core/draft-ietf-httpbis-messaging-latest.html)
* `HTTP/2` - [HTTP/2](https://httpwg.org/http2-spec/draft-ietf-httpbis-http2bis.html)
* `HTTP/3` - [HTTP/3](https://quicwg.org/base-drafts/draft-ietf-quic-http.html)
* `STRUCTURED-FIELDS` - [Structured Field Values for HTTP](https://httpwg.org/specs/rfc8941.html)
* `COOKIES` - [Cookies: HTTP State Management Mechanism](https://httpwg.org/http-extensions/draft-ietf-httpbis-rfc6265bis.html)
* `TLS` - [The Transport Layer Security (TLS) Protocol Version 1.3](https://www.rfc-editor.org/rfc/rfc8446.html)

Note that to include `/` in an anchor name in markdown, the reference needs to be declared in the YAML header like this:

~~~ yaml
normative:
  RFC9112:
    display: HTTP/1.1
~~~



## Not HTTP Specific

The following are useful tips for reducing the amount of editing that the RPC needs to do, leading to cleaner diffs at the end of the process.

### Creating and Modifying Registries

When referring to an IANA registry, quote its name. For example,

> The Foo header field has been registered in the "Hypertext Transfer Protocol (HTTP) Field Name Registry".

Create registry entries as Definition Lists. For example,

~~~ markdown
Name
: dns_timeout

Description
: The intermediary encountered a timeout when trying to find an IP address for the next hop hostname.

Extra Parameters
: None.

Recommended HTTP status code
: 504

Response only generated by intermediaries
: true

Reference
: {% raw %}{{&SELF}}{% endraw %}
~~~

### Self-References

If referring to the your document's RFC number (e.g., in a registry entry), add this to your document's YAML header:

~~~ yaml
entity:
  SELF: "RFC nnnn"
~~~

... and then for each reference, use `{% raw %}{{&SELF}}{% endraw %}`, for example:

~~~ markdown
Reference
: {% raw %}{{&SELF}}{% endraw %}
~~~

