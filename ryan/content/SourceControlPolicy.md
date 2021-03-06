DETER sources are managed under git with the authoritative copy on [github.](https://github.com/deter-project/testbed) This document describes the structure of the repository and the policy for committing changes to the branches of that repository.

# The Branches

There are several distinguished branches of the DETER repository.  These include:

 Master::
  The most recent official stable DETER sources.  _(A link to the most recent release branch??? What is the semantics of this branch now??? -- tvf)'' \\ ''( I think lower-case *master* is a git artifact -- kls)_

======================== \\ _Keith proposes additionally_

 Production::
  This represents what is actually running on boss.isi.deterlab.net

_/Keith_\\
========================

 Development::
  Current development sources.  These include vetted research extensions and runnable DETER sources. This branch has been reviewed by the operations group and run in the full ISI DETERLab environment for at least 1 week.

 Release Branches::
  A released version, known to be a valid starting point for collaborators.  Release versions are only updated to fix urgent bugs or security problems, reviewed by the operations group. These are labelled by version number.  The current Release is 0.93.

 Nonce Branches::
  Developers may also create nonce branches to carry out development tasks, performance evaluations, or other common tasks.  The criteria for commits to these branches are fluid, and the branches themselves are not guaranteed to be stable in any way.

======================
      Rework of the above  ... GORAN
======================

        MASTER[[BR]]

	The most recent official stable DETER sources. (A link to the most recent release branch??? What is the semantics of this branch now??? -- tvf)
	This should be obsoleted by Release branches. It should be renamed to release 0.93.

	DEVELOPMENT[[BR]]

	This is the main trunk containing current development sources. 
	It is integration and collection branch. No support will be provided for snapshots of this branch. Anybody installing deter software or doing development is expected to take snapshots of the latest Release branch.
	Development trunk will be at all times under OPS group control.
	No change can be committed into this branch prior to OPS group approval, completed documentation and prior testing. 

*RELEASE*[[BR]]

	A released version, known to be a valid starting point for collaborators. 
	Release versions are only updated to fix urgent bugs or security problems reviewed by the operations group. 
	These are labelled by version number. The current Release is 0.93 a.k.a. MASTER.[[BR]]

	A new Release Branch will be created as snapshot of a stable (tested) DEV trunk whenever OPS group decide to release new project(s), or periodically a number of bug fixes.
        This newly released branch will be then tested, updates may be applied to fix any problems. When finalized, changes will be merged back into DEV, and the new release will be announced.
	Problems within these branches will be fixed as minor revisions of the branch in question.[[BR]]

        Release branches may periodically merged back into the Dev trunk, to pickup fixes done to that branch.
        The release branches will also be under OPS group control.
        We should support only one or two versions back from latest release. TBD.[[BR]]

        Procedure for creating new release should be:
               1. take a snapshot of the dev branch, create new release branch
               2. Test and fix the new branch until satisfied
               3. Document, then push changes, if any back to dev, 
               4. declare victory

*PRIVAT*[[BR]]  _(Are you objecting to Ted's term **Nonce**?  And did you possibly mean **Private** instead of **Privat** -- kls)_

	Developers may also create nonce branches to carry out development tasks, performance evaluations, or other common tasks. 
	These branches are not supported by the OPS group.
	The only play ground for developers and partners (to carry out development tasks, performance evaluations, bug fixing or other) is inside these branches. [[BR]]

	They are created and deleted as required with an assigned owner.
	Only the owner (or member of the owner's team) of such branch can commit to it.[[BR]]

	Committing changes from ISI owned branches back to the Dev Trunk can only be done by prior OPS group approval, after all paper work detailing changes and testing performed is completed.
	Committing changes from NON-ISI owned branches back to the Dev Trunk can only be done ISI team, upon request ,after detailed review and after OPS group approval.[[BR]]

	Procedure to prepare these branches for check-in should be
               1. pull all changes from DEV branch
               2. retest and fix 
               3. Do the documentation, then create request to check-in into dev 
               4. If ISI branch push the changes to dev, if not then OPS group will handle ...

*Keeping track of fixes and features in various branches[[BR]]*

	A better release control will have to be created to track what was fixed in each of the branches.
	As a bare minimum fixes would need to be tracked against release versions along with what and how they were tested.[[BR]]

        Again, we should only support few branches and obsolete older ones.  _(Does Goran intend *releases* instead of *branches*?  Should we be discouraging Nonce branches?  -- kls)_

*Definition of "accepted" change or satisfactory testing_''_*[[BR]]

	This is the criteria to declare a successful fix, new release readiness or project completion. Required to be satisfied before checking into DEV branch can be allowed.
	Need to define a default, minimum or required test hardware and/or procedure. 
        A separate mini deter hardware setup will be installed at ISI to provide for testing.
        How would partners do that ?
	Suggestions?

*Tagging:[[BR]]*

	Every major and/or minor release will be tagged in the DEV branch. [[BR]]

        The major/minor number will be a part of each version of the released software.
	
==### END============

==========================
 _Keith's rationale_

There MUST be a repository that corresponds closely to what we are
running in production.   Bitter experience from our past shows
that when we run things for more than a short while without
entering them into a repository, changes are lost, or files
not included.

The amount of time something should be tested in production before
entering into that repository depends on the nature of the change
or addition.

Whether or not a new feature or change should even be run or tested
in production also depends on the nature of the change; how big
it is, how thoroughly it has been tested outside of production.

I think it is terribly unwise to transcribe into quasi-force-of-law
fixed terms, and consequently the phrase \\
"run in the full ISI DETERLab environment for at least 1 week" \\ and \\
"This testing regimen implies that the code in development may
lag the code running in DETERLab itself."
makes my blood run cold.

The ops team meets once a week; we can review at each meeting what we think should be pushed from
**Production** to **Development**.  The ops team consists of experienced professionals; if a member
of the team discovers a highly critical fix needs to be issued to both **Development** and possible
release branches, he or she should have the freedom to do so providing that notification is made to
the other members of the team.


_/Keith's rationale_\\
========================

TO BE REVIEWED:

# Rationale

The criterion that code in the *development_' branch must run in the full ISI environment for a week is based on the premise that the development code is both the most technically advanced and has been seasoned in a harsh environment.  This is not a guarantee that the code is suitable for collaborators to use directly.  Code in the '_development* branch is mature and seasoned, but may not be fully documented or may implement research features that collaborators do not want.

The operations group vets code in nonce branches through code review and testing in various test environments before installing it on the main DETERLab.  All code must go through a review, though sometimes a fairly informal one, before being placed on the production testbed for its one week trial.  After the one week trial has been completed successfully without incident, the changes are committed from the nonce branch to the *development* branch.

Collaborators are welcome to ask that their changes from a nonce branch undergo similar review and test.  Collaborator changes that pass the 1 week trial can be included in *development* at the discretion of the operations group.

This testing regimen implies that the code in *development* may lag the code running in DETERLab itself.  The intent is that DETERLab staff can always restore a safe, though advanced, environment from source control at any time.

Collaborators are welcome to track *development* if the are willing to tolerate the volatility of a research laboratory.  More conservative collaborators will track a released version.  The operations group will announce updates to released versions, as well as providing 3 month notice of ceasing support for a released version.  These announcements are news items on the DETERLab.