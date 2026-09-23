CSE 321: Operating Systems
SimpleFS Lab Term Project
Group 11
Section: 6

STUDENT IDS:
22201665 (Azizul Kabir Zayed)
22201786 (Mohmmad Al Amin)
21201336 (Ajwad Ahnaf)

PROJECT FILES
simplefs.h
simplefs_builder.c
simplefs_adder.c
README.txt

COMPILATION
gcc -Wall -Wextra -std=c11 simplefs_builder.c -o simplefs_builder
gcc -Wall -Wextra -std=c11 simplefs_adder.c -o simplefs_adder

EXECUTION

Create a new SimpleFS image:
./simplefs_builder --image disk.img

Add a regular file:
./simplefs_adder --input disk.img --file test1.txt

IMPLEMENTATION DESCRIPTION

simplefs_builder initializes a 256 KiB SimpleFS image consisting of
64 blocks of 4096 bytes each. It initializes the superblock, inode
bitmap, data bitmap, inode table root inode, and the "." and ".."
entries of the root directory.

simplefs_adder opens an existing SimpleFS image, verifies the
superblock magic number, validates the input file, performs first-fit
inode and data-block allocation, copies file contents into data
blocks, creates the file inode, updates allocation bitmaps, creates a
root-directory entry, and updates the root inode size.

SimpleFS supports a single root directory, 32 total inodes, three
direct data-block pointers per inode, files up to 12288 bytes, and
file names up to 58 characters.

MEMBER CONTRIBUTIONS

22201665:
simplefs.h

22201786:
simplefs_builder.c

21201336:
simplefs_adder.c

KNOWN LIMITATIONS

SimpleFS intentionally does not implement subdirectories, indirect
blocks, deletion, renaming, permissions, links, journaling, mounting,
caching, or multi-level directory traversal, as specified by the
project requirements.

No additional known problems at the time of submission.
