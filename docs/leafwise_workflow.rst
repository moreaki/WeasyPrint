Leafwise Workflow
=================

This repository serves two related purposes:

* ``moreaki/WeasyPrint`` stays close to upstream WeasyPrint and is the place
  where patches, fixes, experiments, and pull-request branches are prepared.
* ``convertic-software/leafwise`` is the commercial product repository. It is
  seeded from the ``leafwise`` branch in this repository.


Repository Roles
----------------

Use the repositories with the following intent:

* ``Kozea/WeasyPrint`` is the upstream open-source project.
* ``moreaki/WeasyPrint`` is the integration bridge fork used to:

  - sync with upstream,
  - prepare fix branches,
  - submit pull requests upstream,
  - collect product-relevant changes on the ``leafwise`` branch.

* ``convertic-software/leafwise`` is the product repository used to build the
  commercial offering on top of the integrated ``leafwise`` code line.


Branch Roles
------------

Within ``moreaki/WeasyPrint``:

* ``main`` should stay close to upstream and remain easy to rebase, merge, or
  compare against upstream development.
* topic branches such as ``fix-*``, ``svg-*``, ``initial-letter-*``, and
  similar branches are used for isolated fixes or features that can be proposed
  upstream.
* ``leafwise`` is the integration branch that combines the selected topic
  branches intended to become part of the product baseline.

Within ``convertic-software/leafwise``:

* ``main`` is expected to track the product codebase derived from
  ``moreaki/WeasyPrint:leafwise``.
* product-specific feature branches can be created there when work is not meant
  to go upstream.


Recommended Flow
----------------

For work that may go upstream:

1. Start from ``main`` in ``moreaki/WeasyPrint``.
2. Create a focused topic branch for the fix or feature.
3. Open a pull request against upstream when the branch is ready.
4. Merge the branch into ``leafwise`` when you want it included in the product
   baseline.

For product-only work:

1. Start from ``main`` in ``convertic-software/leafwise``.
2. Create product branches there.
3. Merge back into the product repository after review.
4. Port changes back to ``moreaki/WeasyPrint`` only when a change is suitable
   for upstreaming or useful to keep the bridge fork aligned.

For upstream syncs:

1. Update ``main`` in ``moreaki/WeasyPrint`` from upstream.
2. Reconcile any topic branches that still matter.
3. Refresh ``leafwise`` by merging or rebasing the required branches onto the
   updated base.
4. Move ``convertic-software/leafwise`` forward from the refreshed
   ``moreaki/WeasyPrint:leafwise`` state.


Licensing Notes
---------------

WeasyPrint is distributed under the BSD 3-Clause license. That allows
commercial use, redistribution, and modification, including in a proprietary
product, provided that the required copyright notices, license text, and
disclaimer are preserved in redistributions, and that the original authors are
not presented as endorsing the product.

When shipping the product, also review any third-party assets or dependencies
bundled with the repository, as they may require their own notices or
attribution.
