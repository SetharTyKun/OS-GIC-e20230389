# Lab 3 Report: Wildcards, Hard Links and Symbolic Links

- **Student Name:** VUON SETHAR TYKUN
- **Student ID:** e20230389
- **My values:** name = garden, tag = draft, v1 = 192, v2 = 218

## Core 1: Wildcards

- `notes/*.txt` selected garden12.txt, garden1.txt and garden2.txt. It skipped the hidden file `.garden.txt` and `garden.log`.
- `notes/"$name"?.txt` selected only garden1.txt and garden2.txt, because `?` matches exactly one character, so garden12.txt is not included.
- `'notes/*.txt'` in quotes printed the literal text `<notes/*.txt>`, because quotes switch off the expansion. The shell expands patterns before the command runs.

Evidence: `evidence/wildcards.txt`

## Core 2: Rename, break, and reuse the old name

| Step | Hard link (garden-hard.txt) | Symbolic link (garden-soft.txt) |
|---|---|---|
| Before rename | version 192, same inode as garden.txt (19269423) | version 192, own inode (19269437), stores `garden.txt` |
| After renaming to garden-draft.txt | still version 192 | `No such file or directory` (dangling) |
| After a new garden.txt was created | still version 192 | works again, but reads version 218 (the new file) |

- The hard link points to the inode, so renaming the file does not affect it.
- The symbolic link only stores the name `garden.txt`. After the rename, no file had that name, so it dangled. When a new file took the name, the link read it.
- The new garden.txt has a different inode (19269439), so it is a separate file from the original.
- **What surprised me:** the symbolic link started working again by itself, but it read the wrong file (version 218 instead of 192).

Evidence: `evidence/links.txt`, `evidence/replacement.txt`

## Core 3: Repair

I deleted the broken symbolic link with `rm --` and made it again with `ln -s`, storing a relative target to `garden-draft.txt`. A relative target is read from the folder that holds the link. After the repair, `cat garden-soft.txt` printed version 192 again. I did not touch the hard link and did not rename the report back.

The reason for my relative target is in the `Decision:` line at the end of `evidence/links.txt`.

## Live checkpoint

I built the cp-river case (a hard link and a chain of two symbolic links), renamed the data file, and repaired the first link so the chain read the data again. The output is saved in `evidence/checkpoint.txt`.

## Prediction and debrief

My prediction was right on all three questions (no, 192, 218). In the debrief I first typed 218 for the hard link by mistake, then corrected it to 192 after checking my evidence, because the hard link points to the original inode and not to the name.

## Evidence files

- `evidence/wildcards.txt`: my three wildcard expansions
- `evidence/links.txt`: before, after the rename, after the repair, and my Decision line
- `evidence/replacement.txt`: the new file that took the old name
- `evidence/checkpoint.txt`: the saved output of the checkpoint
