<a id="readme-top"></a>
# About The Project
SimpleFS shows how a real file system works on the inside. It creates a small disk image file and lets you add files into it. It uses a superblock, bitmaps, inodes, and a root directory, just like real file systems do, but in a much simpler way. Made for the CSE321 (Operating Systems) Lab Project at BRAC University.
<p align="right">(<a href="#readme-top">back to top</a>)</p>

# Built With
* ![C](https://img.shields.io/badge/C-C11-A8B9CC?style=for-the-badge&logo=c&logoColor=white)
* ![GCC](https://img.shields.io/badge/GCC-Compiler-A42E2B?style=for-the-badge&logo=gnu&logoColor=white)
<p align="right">(<a href="#readme-top">back to top</a>)</p>

# Project Overview
## Key Features
- Creates a 256 KB disk image (64 blocks, 4 KB each)
- Sets up the superblock, inode bitmap, data bitmap, and inode table
- Creates a root directory with `.` and `..`
- Adds normal files into the image
- Finds free inodes and blocks using first-fit
- Checks for errors (bad image, file too big, duplicate name, no free space)
## Disk Layout
| Block | What it holds  |
|-------|----------------|
| 0     | Superblock     |
| 1     | Inode bitmap   |
| 2     | Data bitmap    |
| 3     | Inode table    |
| 4–63  | Data blocks    |
## Project Files
- `simplefs.h`: shared structs and constants
- `simplefs_builder.c`: makes a new empty disk image
- `simplefs_adder.c`: adds a file into the image
- `test1.txt`, `test2.txt`, `test3.txt`: sample files for testing
## Limits
- Only one folder (the root directory)
- Max 32 inodes
- Max file size: 12 KB (3 blocks)
- Max file name: 58 characters
- No delete, rename, subfolders, or permissions
<p align="right">(<a href="#readme-top">back to top</a>)</p>

# How To Run
**1. Compile**
```bash
gcc -Wall -Wextra -std=c11 simplefs_builder.c -o simplefs_builder
gcc -Wall -Wextra -std=c11 simplefs_adder.c -o simplefs_adder
```
**2. Create a disk image**
```bash
./simplefs_builder --image disk.img
```
**3. Add a file**
```bash
./simplefs_adder --input disk.img --file test1.txt
```







