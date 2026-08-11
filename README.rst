=================
Last.fm API Skill
=================

.. image:: logo.svg
   :width: 120px
   :alt: Last.fm logo

.. image:: https://skills.sh/b/mykeyy/lastfm
   :target: https://skills.sh/mykeyy/lastfm
   :alt: skills.sh installs

.. image:: https://img.shields.io/github/stars/mykeyy/lastfm?style=flat
   :target: https://github.com/mykeyy/lastfm/stargazers
   :alt: GitHub stars

.. image:: https://img.shields.io/github/license/mykeyy/lastfm
   :target: LICENSE
   :alt: MIT license

An Agent Skill for the Last.fm API, with focused references for authentication, scrobbling, errors, albums, artists, tracks, users, charts, tags, and the rest of the public method namespaces.

The skill is built around progressive disclosure. ``SKILL.md`` stays small. When an agent needs ``album.getInfo``, it reads the album reference. When it needs scrobbling, it reads the track and scrobbling references. Unrelated documentation stays out of context.

This is an unofficial community project. It is not affiliated with, sponsored by, or endorsed by Last.fm.

Install
=======

skills.sh
---------

.. code-block:: sh

   npx skills add mykeyy/lastfm

See what the CLI discovers before installing:

.. code-block:: sh

   npx skills add mykeyy/lastfm --list

The repository also has a page on https://skills.sh/mykeyy/lastfm.

Manual install
--------------

Claude Code:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git ~/.claude/skills/lastfm-api

OpenCode:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git ~/.config/opencode/skills/lastfm-api

Any client that supports the Agent Skills format can use the same repository.

What it covers
==============

* Last.fm API request format and JSON responses
* Web, desktop, and mobile authentication
* ``api_sig`` request signing and session keys
* ``track.updateNowPlaying`` and ``track.scrobble``
* Retry rules, ignored scrobbles, and Last.fm error codes
* Album, artist, auth, chart, geo, library, tag, track, and user methods

Repository layout
=================

``SKILL.md``
   The routing layer. It tells the agent which reference to read for the current task.

``references/overview.md``
   API root, request format, encoding, usage guidance, and namespace overview.

``references/authentication.md``
   Web, desktop, and mobile authentication plus request signing.

``references/scrobbling.md``
   Scrobble timing, now playing, batching, ``chosenByUser``, filtering, and retries.

``references/errors.md``
   API error codes and practical handling notes.

``references/fm_api_*.txt``
   Detailed method references split by API namespace.

``skills.sh.json``
   Metadata used to organize the repository page on skills.sh.

Examples
========

After installing the skill, try requests such as:

* ``What parameters does track.scrobble require?``
* ``Show me the Last.fm web authentication flow.``
* ``How should I retry failed scrobbles?``
* ``Which user method returns recent tracks?``
* ``Build a JSON request for album.getInfo.``

For request examples you can copy into a terminal, see ``examples/quickstart.md``.

Documentation sources
=====================

The core references are checked against the official Last.fm documentation:

* Last.fm API: https://www.last.fm/api
* API introduction: https://www.last.fm/api/intro
* Authentication specification: https://www.last.fm/api/authspec
* Scrobbling 2.0: https://www.last.fm/api/scrobbling
* Error codes: https://www.last.fm/api/errorcodes

If a local snapshot disagrees with the current Last.fm documentation, use the official documentation as the source of truth.

Support the project
===================

If you use the skill and want other developers to find it, star the repository. Actual installs through the ``skills`` CLI are what contribute to the skills.sh install count.

License
=======

MIT
