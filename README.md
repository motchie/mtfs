mtfs
====

Movable Type as a File System.

### What is mtfs?

mtfs is [FUSE](http://fuse.sourceforge.net/) implementation of [Movable Type](http://www.movabletype.org/).

It represents MT's objects as files and directoris.

I.E. You can edit MT's template with your favorite text editor, and no needs to use admin screen. 

### Current Status

Current Status of this software is alpha or just a sample.


### Requirements

- Magnanimous mind.
- Linux (Tested with: CentOS 6.5)
- Root privilege user
- [Movable Type](http://movabletype.org/start/) installed. (Tested with: MTOS 5.2.9 ja)
- [Fuse::Simple] (http://search.cpan.org/~noseynick/Fuse-Simple-1.00/) installed.

### Test run

1. Copy mtfs to /path/to/mt/tools
2. `cd /path/to/mt`
3. `sudo perl ./tools/mtfs`
4. Launch another terminal.
5. `sudo ls -lha /mnt/`
6. You'll see a 'templates' directory.
7. `sudo ls -lha /mnt/templates`
8. You'll see many files which filenames are template identifier of your MT.
9. View some files. For example: /mnt/templates/rsd
10. You'll see file contents exactly same as you'll see on MT's admin screen.
11. Press Ctrl+C in terminal which runs mtfs.
12. `sudo umount /mnt` in rest terminal.
