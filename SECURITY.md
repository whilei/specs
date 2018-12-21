# Security

__Goals:__

- redundant, distributed, and interdependent authorization structures
- transparent systems of checks and balances
- compartmentalized security domains
- accountible authorship and procurement

__Heuristics:__

- favor democracy over oligarchy, and oligarchy over monarchy, when possible
  + usually democracy is impossible
- favor well-described identities whenever possible
  + enable individual identities more than group identities
  + interconnected identities more than isolated identites
    + eg. PGP Web of Trust-heavy signatures over unattached "Solo-signers"
- build _systems for_ not _stores of_
  + eg. systems of authorization, instead of authorities (juries over judges)
  + eg. tools for verification, instead of verifiers (CI instead of manual compilation)
- [Principle of Least Privilege]( https://en.wikipedia.org/wiki/Principle_of_least_privilege )

## Repository

### Source

- Must include a list of Authorized Contributors.
- Must include a way to verify the authorship and validity of at least merge commits, as described in the [Git section](#Git).

### Git

- All __merge commits__ must be signed with the PGP key belonging to an Authorized Contributor.
- ?? Each valid __merge commit PGP signing key__ must be verified by at least one other Authorized Contributor. ??
  - eg. The Authorized Contributors must establish a minimal "PGP web of trust" among themselves.
- __Merge commits__ may optionally be signed with [OpenTimeStamps](https://opentimestamps.org/)
- All __tags__ must be signed by an Authorized Contributor.
- Modifications to __the list of Authorized Contributors__ must require approving reviews by more than 50% of the set of Authorized Contributors minus the author.
- Branching strategies should use `master` as the sole canonical and distribution-ready branch.

### Github

> - [ ] TODO: integrate these ideas better with the [Organization specs](#Organization).

- Must require at least 1 approving review in order to merge to `master`.
- Do not trust Github whenever possible; use tools that minimize reliance on Github Infrastructure+GUIs, permissions, or benevolent employees

### CI

- Should ensure valid commits using the verification requirements and systems described in the [Source](#Source) and [Git](#Git) sections.
- Should prefer deterministic build systems.

### Distribution

- Must include PGP-signed SHA256 hashes (signed by an authorized contributor) of each distributed artifact.
- Would be nice to provide a tool to enable independent verification that those signatures were indeed made by an authorized contributor.

## Organization

### Github

- Must be [_Owned_](https://help.github.com/articles/access-permissions-on-github/) by more than one person.
- All organization Owners, and organization Members with _Repository Write_ privileges or greater, must use app-based [2FA for Github login](https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/).
- Use [nested teams](https://blog.github.com/2017-06-13-nested-teams-add-depth-to-your-team-structure/) when reasonable to encourage least-privilege principles for repository permissions.
- Members with Repository Write permissions are not necessarily also Authorized Contributors.

#### References

- https://help.github.com/articles/access-permissions-on-github/
- https://help.github.com/articles/repository-permission-levels-for-an-organization/
- https://help.github.com/articles/about-teams/
- https://help.github.com/articles/managing-team-access-to-an-organization-repository/
- https://blog.github.com/2017-06-13-nested-teams-add-depth-to-your-team-structure/
- https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/

## Appendix

### References

- https://en.wikipedia.org/wiki/Principle_of_least_privilege 
- https://opentimestamps.org/
- https://stackoverflow.com/questions/1962094/what-is-the-sign-off-feature-in-git-for
- Torvalds on a "good commit message": https://github.com/torvalds/subsurface-for-dirk/blame/a48494d2fbed58c751e9b7e8fbff88582f9b2d02/README#L88. Note that enumeration on this _do not_ belong in this document. They should go in a document about _STYLE_.
- Chris Beams on _How to Write a Git Commit Message_: https://chris.beams.io/posts/git-commit/. This is also more about style, not security.
- https://help.github.com/articles/about-teams/
- https://help.github.com/articles/managing-team-access-to-an-organization-repository/
- https://blog.github.com/2017-06-13-nested-teams-add-depth-to-your-team-structure/
- https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/
- https://medium.com/@lopp/who-controls-bitcoin-core-c55c0af91b8a

