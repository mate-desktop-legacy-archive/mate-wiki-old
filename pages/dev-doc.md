### MATE Development

## Versioning and Releases

  * Even numbered releases represent the current stable release. For example, 1.6.0, 1.6.1, etc.

  * Odd numbered releases represent the current unstable, testing release. For example, 1.7.0, 1.7.1, etc.

  * Once a stable release has been made, only bug fixes are made to that release. All new development goes into unstable testing releases. Once all our goals have been achieved and we deem the testing release to be stable, we bump the version and release it as a stable release.

  * Only one stable release is supported at a time. Once a new stable release is made, it immediately obsoletes the previous stable release.

## Overview of Development Cycle

  1. Stable release made

  2. For a period of time all development resources get devoted to bug triaging

  3. Development begins on the next release and our bug triaging team continues squashing bugs in the current release

  4. The next release is deemed stable. One last QA effort takes place involving all developers testing installation on a clean system as well as upgrading from a previous release.

  5. New stable release made

## [Roadmap](roadmap.md)

MATE defines the goals for the next release on its roadmap. New items should
never be added to this roadmap without the permission of project leadership.
MATE does not have fixed development cycles or timelines for releases. A
release is done when it’s done. We believe that rushed development leads to
sloppy code, bugs, and security vulnerabilities.

At some point, we freeze the features for the next release so developers can
focus on the remaining tasks.

Roadmap goals are determine by:

  * What user-made feature requests do we think would be a good fit

  * What changes need to be made for quality/maintenance purposes

  * Developer project ideas

## Git

  * The master branch is our development branch. It represents the most up-to-date code, but is not considered stable.

  * The current stable release has it’s own branch (example: 1.6). All bug fixes that need to be made to the current release get made there. These bug fixes also need to be merged to master if they apply there as well.

  * All bug fixes should be done in a separate branch and then merged to the current stable release and the development release (assuming the bug applies). They should be named issue-#. For example, if a branch fixes caja issue 5, then the branch name should be issue-5. 

  * All non-bug development should be done in a branch named dev-feature-name (example: dev-window-snapping. These branches get merged with the master branch upon completion.

  * Unless a fix is trivial–spelling mistake, for instance– or the commit is a version bump for a new release, developers should never commit directly to master

  * For prospective developers who are not in the github developers team, pull requests can be made. Please make sure that you base your pull request against the correct branch.

## Communicating

Development discussions take place in two locations:

  * #mate-dev irc.freenode.net

  * The MATE github repos

We strongly recommend joining #mate-dev to coordinate with other developers.
This helps expedite the development process and coordinate development
resources. Please note that #mate-dev is for development discussion only; off-
topic and support related discussions should take place in #mate.

## QA

Quality Assurance is achieved through the following methods:

  * Monthly code reviews of commits made by developers

  * Always perform code reviews before merging pull requests from non-developers

  * Unstable next release packages are made available for testing

  * Prior to a new release, all developers do a clean install of the next release on the distribution(s) of their choice. They also must perform an upgrade from the current release

## Style Guidelines

MATE is not particularly draconian about how you format your code, but we do
ask that you put an effort into code readability as well as internal
documentation (comments). Code that is a nightmare to read will not be
accepted. If a particular snippet of code is critical, confusing, etc. please
document what that code does and why the decision was made.

## Github Issues

We use github as our bug tracker. We use labels to define bugs as “confirmed”,
“unconfirmed”, and “feature requests”. If a newly opened issue is a bug, then
it should immediately be set as unconfirmed. Once a developer has been able to
confirm the bug or there are numerous users reporting the same issue, then the
issue can be confirmed.

Please do not be terse in your responses to issues. Even if the user opened an
issue for some inane reasons, please explain to them why the issue is being
closed.

## Mate Documentation Team

The MATE Documentation Team is beginning to form. A link to team guidelines
will be here: [ Mate Documentation Team Guide](dev-doc-doc-team-guide)
