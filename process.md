
_This is general advice for document editors regarding the IETF process. If you have any questions, contact the chairs!_

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Working Group Last Call](#working-group-last-call)
- [AD Evaluation and IETF Last Call](#ad-evaluation-and-ietf-last-call)
- [IESG Evaluation](#iesg-evaluation)
- [AUTH48](#auth48)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Working Group Last Call

Once you and the chair(s) agree that all issues have been addressed and the document is ready, the chair(s) will announce Working Group Last Call (WGLC).

WGLC generally lasts two to four weeks, depending on the length and complexity of the document. The goal is to make sure that there are no lingering design or editorial issues in the document, and that the Working Group agrees that it's ready for publication.

As such, it's important to track the status of issues raised in WGLC, to make sure that nothing is overlooked. Large changes in WGLC are discouraged unless there's good consensus to make them; last-minute changes often introduce errors. On the other hand, fixing a problem before the document ships is preferable to fixing it in an updated RFC.

Once the WGLC period is over, the chair(s) will assess whether consensus was achieved. If only small changes are necessary to the document, this is easy to establish; if major surgery was necessary, an additional (often briefer) WGLC might be required.

As part of the WGLC process, the chair(s) will nominate a Document Shepherd; it is often a chair, but it could be someone else. The Shepherd is responsible for creating a [writeup for the IESG](http://ietf.org/iesg/template/doc-writeup.html) that describes the document's history and consensus around it, so that the IESG has a better idea of what they're looking at.

## AD Evaluation and IETF Last Call

After the Working Group has approved a document, the Document Shepherd will forward their writeup to the responsible Area Director. The AD may make some comments on the document in a preliminary review; once they're addressed (by you and/or the chairs, depending on their nature), and a new draft revision issued if necessary, an announcement will go out for IETF Last Call, announced on the [ietf-announce list](https://mailarchive.ietf.org/arch/browse/ietf-announce/).

IETF LC usually lasts two weeks, and while some discussion will CC the Working Group mailing list, some may not; as a result, it's best to temporarily sign up to the [list-call mailing list](https://www.ietf.org/mailman/listinfo/last-call) if you haven't already.

The chairs will add issues to reflect any major points raised, and it is the whole Working Group's responsibility to answer them. Purely editorial clarifications remain the editors' responsibility and prerogative.

## IESG Evaluation

Once IETF Last Call has finished, the document will enter IESG evaluation. Area Directors will provide three kinds of feedback:

* **DISCUSS** means that they want a discussion of a particular point. This effectively puts your document on hold until the DISCUSS is resolved; as a result, there are [established criteria](https://ietf.org/about/groups/iesg/statements/iesg-discuss-criteria/) for what's in scope, and if you feel that they've been exceeded, you should talk to the WG chair(s). Otherwise, you should respond to the point raised.

* **COMMENT** is just that; something that the AD noticed that they're commenting on. It's polite to respond to COMMENTs with an explanation of what something is like it is, or a short note saying that the suggestion has been incorporated. However, COMMENTs do not hold up progress on the document, so the _can_ be ignored.

* A **NIT** is a small thing that the AD noticed; it is usually an editorial correction. We encourage ADs to submit editorial corrections in PRs, but some may come in their reviews too. However they are submitted, you can do as you see fit with nits; if you do not incorporate them, the RFC Editor will may any necessary corrections (see below).

Area Directors may also request _directorate reviews_, which are done by volunteers, each with a particular focus (e.g., security, applications, general). Directorate reviews typically classify their feedback into categories similar to those above.

The chairs will create issues for all AD and directorate comments in the repository, and will assign purely editorial ones to you. The Working Group will address design (i.e., non-editorial) issues and work with you to incorporate any updates. That said, as a document author, it helps if you take an active role in these discussions -- especially if ADs or directorate reviewers raise questions that you can answer.

In all cases, an Area Director's word is not law; if you believe that they are incorrect, don't have all of the context, or are going against consensus established in the WG, this should be said. See also the [IESG's perspective](https://www.ietf.org/about/groups/iesg/statements/handling-ballot-positions/) on how they handle ballot positions.

IESG evaluation may take some time; most ADs will read the document, and have a number of other documents they'll be processing in parallel. Keep an eye on your document's datatracker status page to see when it's on the agenda for a call; generally, they'll send most feedback right before it.

Usually, IESG evaluation results in changes to the document. When this is the case, a new version of the draft will need to be published, incorporating the agreed-to changes.

## AUTH48

Once your document is approved by the IESG, it will go to the [RFC Editor](https://rfc-editor.org/) for editing. This may take some time, depending on their workload, the document's complexity, and so on. Once completed, they will contact you with an AUTH48 notice.

That e-mail will likely contain a number of questions about the document, along with suggested changes and links to XML files and diffs for what they propose.

The chairs will create issues for each of the questions they ask and assign them to you. 

Additionally, because errors can be and have been introduced by the RFC Editor, we **strongly recommend** checking the actual XML source file for other changes by following this process:

1. Download the latest XML file for the RFC-to-be (the RFC Editor will provide a link).

2. Locally diff that XML file to one generated from the repo (e.g., `make draft-ietf-httpbis-mydraft.xml`). Do **not** use the RFC Editor's supplied diff, and do **not** diff the text file; we recommend using a tool that's able to ignore changes in whitespace (like Apple's FileMerge). Using `rfcdiff` is not recommended, as it hides many differences.

3. For each difference you see:

   a. Ignore changes to non-semantic whitespace, default XML attributes and similar things. Over time, we aim to remove these differences from the XML generated by our toolchain.

   b. If the change is acceptable, commit the corresponding edit to the repo document.

   c. If you have issues with the change, bring it up clearly with the RFC Editor.

4. Return to step 1 until you and the RFC Editor are both satisfied that the document has no issues.

5. Generate text and HTML versions (e.g., `make draft-ietf-httpbis-mydraft.[txt,xml]`) of the specification and verify that there are no rendering issues.

6. Once you are certain there are no issues remaining, respond to the RFC Editor's e-mail and explicitly approve publication (e.g., "I approve publication").

Note that the XML you approve is not the XML that will be published; that will be generated by running the approved XML through `xml2rfc --preptool`. We are currently evaluating whether this step needs further oversight.
