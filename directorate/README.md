# HTTP Directorate Review Guidelines

Thank you for agreeing to be a reviewer for the HTTP Directorate. This document captures guidelines about how the directorate operates, and how you should approach the reviews you write.

## General

HTTP directorate reviews should usually happen early in the lifetime of a draft, to give authors ample time to correct issues before they get any deployment and are more difficult to change.

IETF stream documents that specify extensions to HTTP or applications that use HTTP are always in scope for Directorate reviews. The Directorate might also review similar documents outside the IETF stream upon request -- e.g., from the ISE, W3C, or similar.


## Review Topics

In general, your review should cover at least:

* If the draft specifies an application that uses HTTP (e.g., a "HTTP API"), how well does it fit with the advice in [Building Protocols with HTTP](https://httpwg.org/specs/rfc9205.html)? This document is a BCP, and so should be followed. However, note that there are few hard requirements in it.

* Do extensions conform to the appropriate advice in [HTTP Semantics](https://httpwg.org/specs/rfc9110.html#extending)? Have they been discussed with a wider community than just the application at hand, if they're generic (e.g., a method or status code)?

* Do HTTP header and trailer fields use [Structured Fields](https://httpwg.org/specs/rfc8941.html)? There are sometimes good reasons not to use them, but often they're not used because authors aren't aware of them early in the drafting process.

* Does the draft conform to the conventions in the [HTTP Editor Style Guide](https://httpwg.org/admin/editors/style-guide)? When documents specifying HTTP-related things use similar conventions and terminology, it improves readability and aids understanding.

* Does the document refer to HTTP correctly?

When writing your review, it's important to distinguish between stylistic / aesthetic suggestions and issues that will harm interoperability or security. Not all of the uses of HTTP in the IETF will be "pretty", and we can try to gently improve those cases, but we need to reserve more insistent feedback for practices that will actually break something.

