# log / doc / design

> `design.md` is `log`'s design document.

<!-- vim-markdown-toc GFM -->

* [Features](#features)
  * [User Interface](#user-interface)
  * [Command Line](#command-line)
    * [Options](#options)
* [Example Export Outputs](#example-export-outputs)
  * [Markdown](#markdown)
  * [JSON](#json)

<!-- vim-markdown-toc -->

## Features

### User Interface

**`log`** initializes `log`, opening its UI. The displays this month's entries
in human-readable format, with visible entry IDs and current context, and opens
a persistent prompt at the bottom of the UI for executing subsequent commands:
* **Adding entries -** Write an entry with `#tags` and a `#/context/a/b/c` to
be added to the log.
date(s). `rm 06`, for example, would remove all entries in June, while `rm 2023` would remove all entries in 2023, and `rm 2023-06-29` would remove all entries on June 29, 2023.
* **`a [AUTHOR_NAME]` -** Sets the log's author to the given `[AUTHOR_NAME]`.
* **`e [ENTRY_ID]` -** Opens prompt for editing an existing entry, given the
`[ENTRY_ID]`.
* **`h` -** Opens `log`'s manual.
* **`j` -** Exports the log to JSON.
* **`l [LOG_NAME]` -** Opens a log with the given `[LOG_NAME]`.
* **`q` -** quits `log`.
* **`rm`:**
  * **`rm [ENTRY_ID(s)]` -** Removes all entries with the given `[ENTRY_ID(s)]`.
  * **`rm [DATE(s)]` -** Flexibly removes all entries made in the given
* **`v` -** Displays `log`'s version.
* **`x` -** Exports the log to Markdown.

### Command Line

**Adding entries -** `log [ENTRY]` will add a new log `ENTRY` to the current
log.

#### Options

`log` can be executed with the following options:

* **`-a [AUTHOR_NAME]` -** Sets the log's author to the given `[AUTHOR_NAME]`.
* **`-c` -** Displays the current log.
* **`-e [ENTRY_ID]` -** Opens prompt for editing an existing entry, given the
`[ENTRY_ID]`.
* **`-h` -** Opens `log`'s manual.
* **`-i` -** Displays information about the current log:
  * log title
  * log author
  * log path
  * entry count
  * date of first entry
  * contexts used
  * tags used
* **`-j` -** Exports the log to [JSON](#json).
* **`-l [LOG_NAME]` -** Switches `log` to handle a log
with the given `[LOG_NAME]`.
* **`-rm`:**
  * **`-rm [ENTRY_ID(s)]` -** Removes all entries with the given `[ENTRY_ID(s)]`.
  * **`-rm [DATE(s)]` -** Flexibly removes all entries made in the given
* **`-v` -** Displays `log`'s version.
* **`-x` -** Exports the log to [Markdown](#markdown).

## Example Export Outputs

### Markdown

```
---
title: My Journal
author: J. Doe
---

# My Journal

## 2023

### 06

#### 2023-06-29

* **`home / living_room / 11:24:13` -** Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. `#cooking` `#salad` `#soup`
* **`home / 11:25:02` -** Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. `#python`

#### 2023-06-30

* **`11:27:55` -** Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.

#### 2023-06-31

* **`11:28:39` -** Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. `#guinea_pigs`

### 07

#### 2023-07-01

* **`11:29:53` -** Nibh sit amet commodo nulla facilisi nullam vehicula. `#job_search`
```

### JSON

```json
{
  "title": "My Journal",
  "entries": [
    {
      "entry": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. `#cooking` `#salad` `#soup`",
      "tags": ["cooking", "salad"],
      "time": "11:24:18",
      "date": "2023-06-09"
    },
    {
    }
  ],
  "tags": [
    "cooking",
    "salad"
  ],
  "contexts": [
    "home",
    "home/garden",
    "work",
    "work/meeting",
    "work/side_hustle",
    "school"
  ]
}
```
