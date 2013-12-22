mtfs
====

Movable Type as a File System.

### What is mtfs?

mtfs is [FUSE](http://fuse.sourceforge.net/) implementation of [Movable Type](http://www.movabletype.org/).

It represents MT's objects as files and directories.

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

```
[motchie@localhost]~% sudo ls -lha /mnt
total 5.0K
drwxr-xr-x   1 root root    1 Dec 22 05:31 .
dr-xr-xr-x. 22 root root 4.0K Dec 21 23:39 ..
drwxr-xr-x   1 root root    1 Dec 22 05:31 templates
```

7. `sudo ls -lha /mnt/templates`
8. You'll see many files which filenames are template identifier of your MT.

```
[motchie@localhost]~% sudo ls -lha /mnt/templates
total 25K
drwxr-xr-x 1 root root    1 Dec 22 05:31 .
drwxr-xr-x 1 root root    1 Dec 22 05:31 ..
-rw-r--r-- 1 root root  200 Dec 22 05:31 2column_layout_sidebar
-rw-r--r-- 1 root root  138 Dec 22 05:31 3column_layout_primary_sidebar
-rw-r--r-- 1 root root   62 Dec 22 05:31 3column_layout_secondary_sidebar
-rw-r--r-- 1 root root  624 Dec 22 05:31 banner_footer
-rw-r--r-- 1 root root  681 Dec 22 05:31 banner_header
-rw-r--r-- 1 root root  376 Dec 22 05:31 blogs
-rw-r--r-- 1 root root 1.1K Dec 22 05:31 comment_detail
-rw-r--r-- 1 root root  290 Dec 22 05:31 comment_listing
-rw-r--r-- 1 root root 6.9K Dec 22 05:31 comment_preview
-rw-r--r-- 1 root root 2.2K Dec 22 05:31 comment_response
-rw-r--r-- 1 root root  322 Dec 22 05:31 comment_throttle
-rw-r--r-- 1 root root  415 Dec 22 05:31 commenter_confirm
-rw-r--r-- 1 root root  304 Dec 22 05:31 commenter_notify
-rw-r--r-- 1 root root 5.2K Dec 22 05:31 comments
-rw-r--r-- 1 root root  334 Dec 22 05:31 creative_commons
-rw-r--r-- 1 root root 1.2K Dec 22 05:31 dynamic_error
-rw-r--r-- 1 root root 2.2K Dec 22 05:31 entry_summary
-rw-r--r-- 1 root root 2.2K Dec 22 05:31 feed_recent
-rw-r--r-- 1 root root   73 Dec 22 05:31 footer-email
-rw-r--r-- 1 root root  528 Dec 22 05:31 html_head
-rw-r--r-- 1 root root  45K Dec 22 05:31 javascript
-rw-r--r-- 1 root root  144 Dec 22 05:31 lockout-ip
-rw-r--r-- 1 root root  214 Dec 22 05:31 lockout-user
-rw-r--r-- 1 root root 1.3K Dec 22 05:31 main_index
-rw-r--r-- 1 root root  324 Dec 22 05:31 main_index_widgets_group
-rw-r--r-- 1 root root 1.4K Dec 22 05:31 new-comment
-rw-r--r-- 1 root root 1.9K Dec 22 05:31 new-ping
-rw-r--r-- 1 root root 1.1K Dec 22 05:31 notify-entry
-rw-r--r-- 1 root root  278 Dec 22 05:31 openid
-rw-r--r-- 1 root root 2.4K Dec 22 05:31 page
-rw-r--r-- 1 root root  953 Dec 22 05:31 pages_list
-rw-r--r-- 1 root root  476 Dec 22 05:31 popup_image
-rw-r--r-- 1 root root  274 Dec 22 05:31 powered_by
-rw-r--r-- 1 root root  662 Dec 22 05:31 recent_assets
-rw-r--r-- 1 root root  700 Dec 22 05:31 recent_comments
-rw-r--r-- 1 root root  557 Dec 22 05:31 recent_entries
-rw-r--r-- 1 root root  148 Dec 22 05:31 recover-password
-rw-r--r-- 1 root root  782 Dec 22 05:31 rsd
-rw-r--r-- 1 root root 1.5K Dec 22 05:31 search
-rw-r--r-- 1 root root 6.6K Dec 22 05:31 search_results
-rw-r--r-- 1 root root  894 Dec 22 05:31 sidebar
-rw-r--r-- 1 root root 1.7K Dec 22 05:31 signin
-rw-r--r-- 1 root root  122 Dec 22 05:31 styles
-rw-r--r-- 1 root root  960 Dec 22 05:31 syndication
-rw-r--r-- 1 root root  496 Dec 22 05:31 tag_cloud
-rw-r--r-- 1 root root 1.1K Dec 22 05:31 technorati_search
-rw-r--r-- 1 root root 1.4K Dec 22 05:31 trackbacks
-rw-r--r-- 1 root root  442 Dec 22 05:31 verify-subscribe
[motchie@localhost]~%
```

9. View some files. For example: /mnt/templates/rsd
10. You'll see file contents exactly same as you'll see on MT's admin screen.


```
[motchie@localhost]~% sudo more /mnt/templates/rsd
<$mt:HTTPContentType type="application/rsd+xml"$><?xml version="1.0"?>
<rsd version="1.0" xmlns="http://archipelago.phrasewise.com/rsd">
<service>
<engineName><$mt:ProductName version="1"$></engineName>
<engineLink>http://www.sixapart.com/movabletype/</engineLink>
<homePageLink><$mt:BlogURL$></homePageLink>
<apis>
<api name="MetaWeblog" preferred="true" apiLink="<$mt:CGIPath$><$mt:XMLRPCScript
$>" blogID="<$mt:BlogID$>" />
<api name="MovableType" preferred="false" apiLink="<$mt:CGIPath$><$mt:XMLRPCScri
pt$>" blogID="<$mt:BlogID$>" />
<api name="Blogger" preferred="false" apiLink="<$mt:CGIPath$><$mt:XMLRPCScript$>
" blogID="<$mt:BlogID$>" />
<api name="Atom" preferred="false" apiLink="<$mt:CGIPath$><$mt:AtomScript$>/webl
og" blogID="<$mt:BlogID$>" />
</apis>
</service>
</rsd>
```

11. Press Ctrl+C in terminal which runs mtfs.
12. `sudo umount /mnt` in rest terminal.
