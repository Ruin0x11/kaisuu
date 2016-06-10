# Dekki

Create tab-separated Japanese word lists ordered by frequency for importing into Anki from text files.

## Requirements

* mecab
* mecab-ipadic

## Installation

Install the above requirements, then do:

```
gem install dekki
```

## Usage

```
dekki [-ik] [-c LINES] [-o FILE] INPUT
```

You can input one or more files or read from stdin.

By default, the cards are printed on stdout. You can pipe them to a file or use the `-o` flag to specify a file to write to. Note that with the `-o` flag, the file is overwritten.

To create a single wordlist per file, use the `-i` flag. This will write one word list file per file passed in, each with the original file's name in the word list's name.

By default, cards that are missing the kana or meaning fields are ignored. This can happen if the dictionary fails to find an entry for a separated word. To keep these cards anyway, use the `-k` flag.

The `-c` flag controls how many lines of context before and after the sentence the word is found in are kept.

The order of the fields in the output is as follows:

* Kanji
* Kana
* Meaning
* Before (sentences before sentence word was in)
* Context (first sentence word was found in)
* After (sentences after sentence word was in)
* Frequency (times word was seen)
* Position (line number word was first seen on)
* Source (first file word was found in)

Once you have the wordlist, import the file into Anki. Make sure that the 'Allow HTML in fields' box is checked.

Many cards will have to be suspended, if they were parsed incorrectly. Just press `!` while reviewing to suspend the current note.

## Notes

Rough around the edges, since there are many false positives. Use at your own risk.
