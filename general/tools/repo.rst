.. role:: raw-html-m2r(raw)
   :format: html


repo
====

"Repo is a tool built on top of Git. Repo helps manage many Git repositories,
does the uploads to revision control systems, and automates parts of the
development workflow. Repo is not meant to replace Git, only to make it easier
to work with Git. The repo command is an executable Python script that you can
put anywhere in your path." `- Source <(https://gerrit.googlesource.com/git-repo)>`_

Download
--------

.. code-block:: console

   git clone https://gerrit.googlesource.com/git-repo

repo Manifest Format
--------------------

"A repo manifest describes the structure of a repo client; that is the
directories that are visible and where they should be obtained from with git.

The basic structure of a manifest is a bare Git repository holding a single
default.xml XML file in the top level directory.

Manifests are inherently version controlled, since they are kept within a Git
repository. Updates to manifests are automatically obtained by clients during
repo sync." `- Source <(https://gerrit.googlesource.com/git-repo/+/HEAD/docs/manifest-format.md)>`_

----

Footnotes & Appendix
--------------------

----

`Ka-Ro electronics GmbH <https://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
