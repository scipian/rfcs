Scipian RFCs
============

Our goal is to develop Scipian in the open and we want the community to be
involved from day one. However to achieve the goal, we need governance around 
introducing "substantial" changes to the platform. The `scipian/rfcs` repository
is how we organize that process.

The "RFC" (Request for Comments) process is intended to provide a consistent and
controlled path for new features to enter the platform. This will allow all
stakeholders to be confident about the direction the platform is evolving in.

Many changes however, including bug fixes and documentation improvements can be
implemented and reviewed via the normal GitHub pull request workflow. For more
information, please reference the [CONTRIBUTING][contributing] document.

[contributing]: https://github.com/scipian/community/blob/master/CONTRIBUTING.md


Table of Contents
-----------------

- [Thanks][thanks]
- [When You Need to Follow This Process][when]
- [Before Creating an RFC][before]
- [Process][process]
- [Life Cycle][life-cycle]
- [Reviewing][reviewing]
- [Implementing][implementing]
- [Holding][holding]
- [Governance][governance]
- [License][license]
- [Contributions][contributions]

[thanks]: /README.md#thanks
[when]: /README.md#when-you-need-to-follow-this-process
[before]: /README.md#before-creating-an-rfc
[process]: /README.md#process
[life-cycle]: /README.md#life-cycle
[reviewing]: /README.md#reviewing
[implementing]: /README.md#implementing
[holding]: /README.md#holding
[governance]: /README.md#governance
[license]: /README.md#license
[contributions]: /README.md#contributions

Thanks
------

First, before we begin, this process is heavily inspired by the 
[Rust Community][rust-governance]. You are a great example of how a community 
can operate and thrive. Thank you!

[rust-governance]: https://www.rust-lang.org/governance

When You Need to Follow This Process
------------------------------------

You need to follow this process if you intend to make `substantial` changes to
the platform or the RFC process itself. The definition of a `substantial` change
is evolving based on community norms and varies depending on what part of the
ecosystem you are proposing to change.

Here are some examples of when an RFC is required:

- Any semantic change to the platform that is not a bugfix.
- Removing features, including those that are feature-gated.
- Creating roadmaps that encompass where the platform is going.

Here are some examples of when an RFC is not required:

- Rephrasing, reorganizing, refactoring, or otherwise "changing shape does not
  change meaning".
- Additions that strictly improve the code base like performance/speedup, better
  error handling, and etc.
- Additions only likely to be noticed by other developers of scipian, invisible
  to users of scipian.

_DISCLAIMER:_ If you submit a pull request to implement a new feature without 
going through the RFC process, it may be closed with a polite request to submit 
an RFC first.

Before Creating an RFC
----------------------

Please do not try to rush the process, there are many reasons it is in place and
one major reason is having a well thought out feature that is documented. This
will allow implementing the feature much smoother, because you will know what 
you are building before any work is done.

Rushing the process will definitely hurt it's chances of acceptance. For example
RFCs that are hastily proposed, low quality, previously rejected, or those that 
don't fit into the near-term roadmap, may be quickly rejected which can be 
demotivating for the unprepared contributor. Laying some groundwork ahead of 
the RFC can make the process smoother.

There is no single best way to prepare for submitting an RFC, but talking it
over with the community in the different channels to determine if the RFC may be
desirable is a great way. From there, having a consistent impact on the project
requires concerted effort towards consensus-building.

Process
-------

To get a major feature added to Scipian, you must first get the RFC merged into
the RFC repository as a markdown file. At that point, the RFC becomes "active"
and may be implemented with the goal of eventual inclusion into Scipian.

1. Fork the RFC repo.
1. Copy the 0000-template.md to text/0000-my-feature.md. (Where my-feature is
   descriptive. Do not assign an RFC number yet.)
1. Fill in the RFC and put care into the details: RFCs that do not present 
   convincing motivation, demonstrate understanding of the impact of the 
   design, or are disingenuous about the drawbacks or alternatives tend to be 
   poorly received.
1. Submit a pull request. As a pull request the RFC will receive design 
   feedback from the larger community, and the author should be prepared to 
   revise it in response.
1. Each pull request will be triaged by the maintainers.
1. Build concensus and integrate feedback. RFCs that have broad support are much
   more likely to make progress than those that don't receive any comments. Feel
   free to reach out to the RFC assignee in particular to get help identifying
   stakeholders and obstacles.
1. All conversations should stay within the comment thread of the pull request
   itself. Offline discussion will be summarized on the pull request comment
   thread.
1. RFCs rarely go through this process unchanged, especially as alternatives 
   and drawbacks are shown. You can make edits, big and small, to the RFC to 
   clarify or change the design, but make changes as new commits to the pull 
   request, and leave a comment on the pull request explaining your changes. 
   Specifically, do not squash or rebase commits after they are visible on the 
   pull request.
1. At some point, a maintainer will propose a "motion for final comment period" 
   (FCP), along with a disposition for the RFC (merge, close, or hold).
    - This step is taken when enough of the tradeoffs have been discussed that 
      the subteam is in a position to make a decision. That does not require 
      consensus amongst all participants in the RFC thread (which is usually
      impossible). However, the argument supporting the disposition on the RFC
      needs to have already been clearly articulated, and there should not be
      a strong consensus against that position outside of the maintainers.
      Maintainers use their best judgment in taking this step, and the FCP 
      itself ensures there is ample time and notification for stakeholders to 
      push back if it is made prematurely.
    - For RFCs with lengthy discussion, the motion to FCP is usually preceded by 
      a summary comment trying to lay out the current state of the discussion 
      and major tradeoffs/points of disagreement.
    - Before actually entering FCP, all members of the maintainers group must 
      sign off; this is often the point at which many members first review the 
      RFC in full depth.
1. Once an FCP is called, it will last ten calendar days, so it is open for at
   least five business days. We will do our best to advertise widely in our
   community channels. This way all stakeholders have a chance to lodge any 
   final objections before a decision is reached.
1. In most cases, the FCP period is quiet, and the RFC is either merged or
   closed. However, sometimes substantial new arguments or ideas are raised. 
   When this happens, the RFC is canceled and the it goes back into development 
   mode.

Life Cycle
----------

Once an RFC reaches "active" status, an issue will be created in the
`scipian/community` repository and the label `type/epic` will be applied. Using 
the RFC as reference, the epic can then be broken down into it's stories. Since
we have multiple repositories in the Scipian organization, the stories should be
created in the corresponding repository the story belongs to. When the work has 
been broken down, then the author may implement it and follow the pull request 
model to the appropriate Scipian repositories. Please refer to
[CONTRIBUTING][contributing] document for further instructions.

Please keep in mind that once an "RFC" becomes "active", it does not mean that
it's a rubber stamp and that the work will be merged. However, it does mean that
in principle all the major stakeholders have agreed to the feature and are
amendable to merging it.

Nor does being "active" imply anything about what priority is assigned to it's
implementation. Nor does it imply anything about whether a Scipian developer has
been assigned the task of implementing the feature. While it is not _necessary_
that the author of the RFC also write the implementation, it is by far the most
effective way to see an RFC through to completion. Authors should also not
expect that other project developers will take on responsibility of implementing
their accepted feature.

Modifications to "active" RFCs can be done in follow-up pull requests. We 
strive to write each RFC in a manner that it will reflect the final design of 
the feature, but the nature of the process means that we cannot expect every 
merged RFC to actually reflect what the end result will be at the time of the 
next major release.

In general, once accepted, RFCs should not be substantially changed. Only very 
minor changes should be submitted as amendments. More substantial changes 
should be new RFCs, with a note added to the original RFC. Exactly what counts 
as a "very minor change" is up to the maintainers to decide.

Reviewing
---------

While the RFC pull request is up, the maintainers may schedule meetings with 
the author and/or relevant stakeholders to discuss the issues in greater 
detail. Following the RFC process, a summary from the meetings will be posted 
back to the RFC pull request.

Maintainers makes final decisions about RFCs after the benefits and drawbacks 
are well understood. These decisions can be made at any time, but the 
maintainers will regularly issue decisions. When a decision is made, the RFC 
pull request will either be merged or closed. In either case, if the reasoning 
is not clear from the discussion in thread, the maintainers will add a comment 
describing the rationale for the decision.

Implementing
------------

Some accepted RFCs represent vital features that need to be implemented right 
away. Other accepted RFCs can represent features that can wait until some 
arbitrary developer feels like doing the work. Every accepted RFC has an 
associated issue tracking its implementation in the Scipian Community 
repository with the `type/epic` label applied to it; thus that associated issue 
can be assigned a priority via the triage process that the maintainers use for 
all issues in the Scipian organization.

The author of an RFC is not obligated to implement it. Of course, the RFC 
author (like any other developer) is welcome to post an implementation for 
review after the RFC has been accepted.

If you are interested in working on the implementation for an "active" RFC, but 
cannot determine if someone else is already working on it, feel free to ask 
(e.g. by leaving a comment on the associated issue).

Holding
-------

Some RFC pull requests are tagged with the `inactive/on-hold` label when they 
are closed (as part of the rejection process). An RFC closed with 
`inactive/on-hold` is marked as such because we want neither to think about 
evaluating the proposal nor about implementing the described feature until some 
time in the future, and we believe that we can afford to wait until then to do 
so. Historically, "on-hold" was used to hold features until after 1.0. Held pull
requests may be re-opened when the time is right. We don't have any formal
process for that, you should ask the maintainers.

Usually an RFC pull request marked as `inactive/on-hold` has already passed an 
informal first round of evaluation, namely the round of "do we think we would 
ever possibly consider making this change, as outlined in the RFC pull request, 
or some semi-obvious variation of it." (When the answer to the latter question 
is "no", then the appropriate response is to close the RFC, not hold it.)

Governance
----------

This process is intended to be as lightweight as reasonable for the present 
circumstances. Per this process, we are trying to let the process be driven by 
consensus and community norms, not impose more structure than necessary.

License
-------

This repository is currently licensed under the Apache License, Version 2.0. 
Please refer to the [LICENSE][repository-license] or the 
[Apache website][apache]. The GitHub website 
["Choose a License"][choose-license] is a great resource too.

[repository-license]: /LICENSE
[apache]: http://www.apache.org/licenses/LICENSE-2.0
[choose-license]: https://choosealicense.com/

Contributions
-------------

Any contribution intentionally submitted for inclusion in the work by you, 
shall be licensed under Apache 2.0, without any additional terms or conditions.
