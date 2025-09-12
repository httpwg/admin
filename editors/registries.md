# Registering New HTTP Protocol Elements

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [How do I create a new HTTP header?](#how-do-i-create-a-new-http-header)
- [How do I create a new HTTP method?](#how-do-i-create-a-new-http-method)
- [How do I create a new HTTP status code?](#how-do-i-create-a-new-http-status-code)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## How do I create a new HTTP header?

The best place to start is [Considerations for New Header
Fields](https://httpwg.org/specs/rfc9110.html#considerations.for.new.fields)
in RFC 9110; it covers most common questions, and has a checklist for
header authors.

If you have questions, the best place to ask is the [HTTP Working Group mailing
list](https://lists.w3.org/Archives/Public/ietf-http-wg/).

New HTTP headers ought to be registered, to assure that you don't collide with
other headers, and so that people can more easily find out more about your
header when they see it. [RFC 9110 explains how](https://httpwg.org/specs/rfc9110.html#fields.registry)).



## How do I create a new HTTP method?

New HTTP methods are relatively uncommon, because a lot of the value in HTTP is
having a constrained, generic set of methods.

[Considerations for New
Methods](https://httpwg.org/specs/rfc9110.html#considerations.for.new.methods) in RFC 9110
is a good place to start for those thinking about creating a method.

If your idea for a new method seems like a good idea after reading that, the
best thing to do is to bring it up on the [HTTP Working Group mailing
list](http://lists.w3.org/Archives/Public/ietf-http-wg/).


## How do I create a new HTTP status code?

Like methods, new HTTP status codes are fairly rare -- not least because there
are only a limited number of unused codes available.

[Considerations for New Status
Codes](https://httpwg.org/specs/rfc9110.html#considerations.for.new.status.codes) in RFC 9110
is a good place to start for those thinking about creating a status code.

If you have an idea for a new status code, the best thing to do is to bring it
up on the [HTTP Working Group mailing
list](http://lists.w3.org/Archives/Public/ietf-http-wg/), where people can
discuss it and point you in the right direction if this isn't the best solution
for your problem.
