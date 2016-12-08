---
layout: post
title: while (false !== readdir())
---

Had fun today with readdir(), this function expects to be passed a valid handle that was created with opendir().  The php documentation states: "Returns the entry name on success or FALSE on failure". The trouble is that opendir might have returned false because it was given an invalid directory and if you pass readdir() that false it returns NULL.

So today I came across a case of a recursive while loop conditioned on readdir() not being false, since another bug had passed opendir() an invalid directory.  That created a cool loop that filled the server logs with PHP Warnings from readdir().

Based on a bug report (https://bugs.php.net/bug.php?id=54673) that links to http://www.php.net/manual/en/functions.internal.php by convention functions passed invalid parameters will return NULL.

Filed under "Learned something new today"
