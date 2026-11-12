I saved my prediction before the experiment, then corrected it with oslab debrief lab2. I was right about ___, but wrong about ___. I learned that a relative path starts from the folder I am in, so the same path can work in one folder and fail in another.# Lab 2 Report: Linux Navigation and File Management

Student ID: e20230389

## What I did
- Built `TechCorp/Audit/` (with `archive/`), `TechCorp/HR/` and `TechCorp/Engineering/`.
- Moved `audit notes.txt` into `reports/` with a relative path, and `budget 2026.txt` with absolute paths.
- Copied both reports into `TechCorp/Audit/`, and copied the first one into `archive/` as `first-original.txt`.
- Proved the copies are identical with `cmp` (no output means identical).

## Relative vs absolute paths
- A relative path starts from the folder I am in (`pwd`). An absolute path starts from `/`.
- For step 3 I used relative paths, because they are short when I am already in the lab folder. Absolute paths are better when the starting folder may change.

## My path error
- Error: `cat: 'reports/audit notes.txt': No such file or directory`
- Cause: I was in `TechCorp/HR`, and there is no `reports` folder there. A relative path starts from the current folder.
- Fix: `../../reports/audit notes.txt` (two levels up to `lab2`, then into `reports`).

## Names with spaces
My file names contain a space, so I wrote `"$file1"` in double quotes. Without quotes, the shell splits the name into two words and `ls` looks for two files that do not exist.

## Prediction and debrief
I saved my prediction before the experiment, then gave the right answer to each question with oslab debrief lab2, so my wrong guesses were corrected. I learned that a relative path starts from the folder I am in (check with pwd), while an absolute path starts from /, and that a file name with a space needs quotes.

## Evidence
- `evidence/paths.txt`: my commands, my decision, and my Error and Fix lines
- `evidence/tree.txt`: the final list of files
- `evidence/checkpoint.txt`: the checkpoint output
