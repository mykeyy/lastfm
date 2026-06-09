=================
Last.fm API Skill
=================

.. image:: https://www.last.fm/static/images/logo_open_graph_large.png
   :width: 300px
   :alt: Last.fm Logo

.. image:: https://skills.sh/b/mykeyy/lastfm
   :target: https://skills.sh/mykeyy/lastfm
   :alt: skills.sh badge

This is an Agent Skill for the Last.fm Music Discovery API. It gives your AI tools a complete, compressed lookup guide for everything they need to interact with Last.fm: authentication, scrobbling, and API methods.

.. note::
   This is an unofficial, community-maintained project. It is not affiliated with, sponsored by, or endorsed by Last.fm.

Instead of raw HTML docs that waste context windows, the references in this repository are compressed to save space while retaining details. Your agent will read the compressed files to get the information it needs, reducing token usage and speeding up responses.

What is inside
==============

* **SKILL.md**: The entry point for the skill, containing the method index and basic API parameters.
* **references/**: The folder containing compressed text documentation for each namespace.

+-------------------------------+-----------------------------------------------------------------+
| File                          | Contents                                                        |
+===============================+=================================================================+
| references/fm_a_main.txt      | Authentication flows, scrobbling criteria, signature signing    |
+-------------------------------+-----------------------------------------------------------------+
| references/fm_api_track.txt   | Track methods, including track.scrobble and updateNowPlaying    |
+-------------------------------+-----------------------------------------------------------------+
| references/fm_api_*.txt       | Namespace-specific method specifications (album, artist, user)  |
+-------------------------------+-----------------------------------------------------------------+

Installation
============

Claude Code
-----------

Clone this repository directly into Claude Code's skills directory:

.. code-block:: sh

   mkdir -p ~/.claude/skills
   git clone https://github.com/Mykeyy/lastfm.git ~/.claude/skills/lastfm-api

OpenCode
--------

Clone this repository directly into OpenCode's skills directory:

.. code-block:: sh

   mkdir -p ~/.config/opencode/skills
   git clone https://github.com/Mykeyy/lastfm.git ~/.config/opencode/skills/lastfm-api

skills.sh
---------

If you use a client compatible with the skills.sh registry:

.. code-block:: sh

   skills install Mykeyy/lastfm

Usage
=====

Once you load the skill into your AI environment, you can ask questions directly:

* "How do we sign API requests?"
* "What parameters does track.scrobble require?"
* "When do I need to set chosenByUser to 0?"
* "Is HTTPS required for all calls?"

License
=======

MIT
