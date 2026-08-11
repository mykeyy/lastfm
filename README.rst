=================
Last.fm API Skill
=================

.. image:: logo.svg
   :width: 120px
   :alt: Last.fm logo

.. image:: https://skills.sh/b/mykeyy/lastfm
   :target: https://skills.sh/mykeyy/lastfm
   :alt: skills.sh installs

A compact Agent Skill for the Last.fm Music Discovery API.

The repository keeps ``SKILL.md`` small and routes agents to focused reference files for authentication, scrobbling, errors, or a single API namespace. An agent working on ``album.getInfo`` should not need to load track scrobbling rules or the whole Last.fm documentation set.

This is an unofficial community project. It is not affiliated with, sponsored by, or endorsed by Last.fm.

Why this exists
===============

Last.fm's API documentation is useful, but loading a large documentation dump into an agent wastes context. This skill uses progressive disclosure instead. The entry file tells the agent which reference to open, and the detailed material stays out of context until it is needed.

The method list and core behavior are based on the official Last.fm API documentation. When the local reference and the current official documentation disagree, the official documentation should be treated as the source of truth.

Repository layout
=================

``SKILL.md``
   Small routing layer for the skill. It explains which reference file to read for a task.

``references/overview.md``
   API root, request format, JSON responses, encoding, usage guidance, and current namespaces.

``references/authentication.md``
   Web, desktop, and mobile authentication, session lifetime, and ``api_sig`` signing.

``references/scrobbling.md``
   Scrobble timing, now playing, batching, ``chosenByUser``, filtering, and retry behavior.

``references/errors.md``
   Last.fm error codes and practical handling notes.

``references/fm_api_*.txt``
   Method details split by namespace: album, artist, auth, chart, geo, library, tag, track, and user.

Install
=======

skills.sh
---------

The current skills CLI can install the repository directly:

.. code-block:: sh

   npx skills add mykeyy/lastfm

To inspect what the CLI discovers before installing:

.. code-block:: sh

   npx skills add mykeyy/lastfm --list

Manual install
--------------

Claude Code:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git ~/.claude/skills/lastfm-api

OpenCode:

.. code-block:: sh

   git clone https://github.com/mykeyy/lastfm.git ~/.config/opencode/skills/lastfm-api

Usage
=====

Once installed, ask the agent about the part of Last.fm you are working with. For example:

* ``What parameters does track.scrobble require?``
* ``Show me the web authentication flow.``
* ``How should I retry failed scrobbles?``
* ``Which user method returns recent tracks?``
* ``Build a JSON request for album.getInfo.``

The skill should open only the reference files needed for the question.

Official documentation
======================

* Last.fm API: https://www.last.fm/api
* API introduction: https://www.last.fm/api/intro
* Authentication specification: https://www.last.fm/api/authspec
* Scrobbling 2.0: https://www.last.fm/api/scrobbling
* Error codes: https://www.last.fm/api/errorcodes

License
=======

MIT
