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

A portable Agent Skill for the Last.fm API, with focused references for authentication, scrobbling, errors, albums, artists, tracks, users, charts, tags, and the rest of the public method namespaces.

The repository uses the open ``SKILL.md`` format instead of maintaining separate copies for individual coding agents. The same skill is designed to work with Claude Code, Codex, OpenCode, Google Antigravity, and other clients that support Agent Skills.

The skill is built around progressive disclosure. ``SKILL.md`` stays small. When an agent needs ``album.getInfo``, it reads the album reference. When it needs scrobbling, it reads the track and scrobbling references. Unrelated documentation stays out of context.

This is an unofficial community project. It is not affiliated with, sponsored by, or endorsed by Last.fm.

Install
=======

Recommended
-----------

Use the skills.sh CLI from the project where you want the skill available:

.. code-block:: sh

   npx skills add mykeyy/lastfm

See what the CLI discovers before installing:

.. code-block:: sh

   npx skills add mykeyy/lastfm --list

The repository page is https://skills.sh/mykeyy/lastfm.

Client compatibility
====================

Claude Code
-----------

The normal ``npx skills add`` command is the recommended install path. For a manual global install:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git ~/.claude/skills/lastfm-api

Start a new Claude Code session after installing so the skill can be discovered.

Codex
-----

Run the normal install command from your project root:

.. code-block:: sh

   npx skills add mykeyy/lastfm

Then start a new Codex session. The skill uses the Agent Skills open standard and does not require Codex-specific instructions or a separate copy of ``SKILL.md``.

OpenCode
--------

OpenCode supports Agent Skills directly and discovers compatible skill directories. The normal skills.sh install works, or you can install globally:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git ~/.config/opencode/skills/lastfm-api

For a project-local install, OpenCode also supports the portable ``.agents/skills`` location:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git .agents/skills/lastfm-api

Google Antigravity
------------------

Antigravity uses the same directory-based Agent Skills format. For a project-local install, place the skill under ``.agents/skills``:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git .agents/skills/lastfm-api

For a global Antigravity install, Google documents the global skills directory as ``~/.gemini/config/skills``:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git ~/.gemini/config/skills/lastfm-api

In Antigravity CLI, use ``/skills`` to confirm that ``lastfm-api`` is visible. If you installed it while Antigravity was already running, start a new session before troubleshooting discovery.

Other clients
-------------

skills.sh also lists support for clients including Cursor, Windsurf, GitHub Copilot, Gemini, Cline, AMP, and OpenClaw. Use the normal ``npx skills add mykeyy/lastfm`` command when the client is supported by the skills CLI.

There is intentionally only one source of truth in this repository. Client-specific copies are avoided so API fixes and security updates do not drift between agents.

What it covers
==============

* Last.fm API request format and JSON responses
* Web, desktop, and mobile authentication boundaries
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
   Web and desktop authorization, the legacy mobile authentication boundary, and request signing.

``references/scrobbling.md``
   Scrobble timing, now playing, batching, ``chosenByUser``, filtering, and retries.

``references/errors.md``
   API error codes and practical handling notes.

``references/{album,artist,auth,chart,geo,library,tag,track,user}.md``
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