| script_karma|Rating_242/78,_Downloaded_by_4548_ | Comments,_bugs,_improvements|Vim_wiki|
created by
Hari_Krishna_Dara
 
script type
utility
 
description
PLEASE READ THE INSTALL SECTION COMPLETELY.

This is a fairly complete integration with the perforce version control system for the most commanly used operations,
including many administrative commands. It includes a great menu that is modelled very close to the p4win (the perforce
GUI client) and is quite extensive.

------------------------------------------------------------------------------------------------------------------------
---------------------------
Lately, I am not finding enough time to add features to this, so if anybody is interested to help me add new features or
even take over the responsibility, you are very much welcome.
------------------------------------------------------------------------------------------------------------------------
--------------------------

Install the files as described in the installation section below and read and type &quot;:h perforce.txt&quot; for help
on using the plugin.

If you find any problems please report them to me. If you happen to add new features or fix any problems, I would
appreciate if you send me in the diff. This will speed up the future enhancements (there is a lot more that can be done)
and also benefit all the script users.

Search_key_words: perforce scm source control interface p4 p4d p4win multvals genutils Hari Krishna Dara
 
install details
- Extract the zip file into your runtime directory (~/.vim or %HOME%/vimfiles).
- Download the latest versions of the below scripts and place them in your runtime plugin directory (see end for
instructions specific to older version):
    genutils.vim: vimscript#197
- Start Vim and regenerate help tags on your runtime doc directory. Ex:
    :helpt ~/.vim/doc
    :helpt ~\vimfiles\doc
- Type the following command and read the installation section to complete the installation:
    :help perforce-installation

For versions prior to 4.0, you need to download multvals.vim (vimscript#171) in addition to genutils, but make sure you
download only the non-autoload versions of both genutils and multvals plugins (see their download page for details, and
a trick to have both coexists).
 
 ______________________________________________________________
|rate_this_script|oLife_Changing_oHelpful_oUnfulfilling _[rate|
script versions (upload_new_version)
Click on the package to download.
package      script  date  Vim     user    release notes
             version       version
perforce-    4.1     2006- 7.0     Hari    There were a few issues with the 4.0 version, and this version tries to
4.1.zip              09-03         Krishna resolve them, and adds a few features.
                                   Dara
                                           - Fixed broken handling of <SHOW DIFF> in describe windows. But it is
                                             better than before, as you can now describe multiple changelists and
                                             show diffs selectively.
                                           - For newer perforce servers, <Enter> on a pending change (in
                                             changelist) showed the file list twice. Removed special handling for
                                             this, which means for older perforce servers, you will see no file
                                             list.
                                           - Force a file status update on auto checkout.
                                           - File status handling has in general been improved.
                                           - Now executing command on multiple files that result in changing the
                                             file statuses (such as add, edit, revert etc.) will correctly result
                                             in their file statuses getting reset.
                                           - While create a new changelist or submitting a change, the Files:
                                             section is examined and the file statuses for all of them will be
                                             reset. This also works for most of the cases of modifying a changelist
                                             to remove/add files.
                                           - This will also solve a long standing issue that reload during submit
                                             doesn't update its file status.
                                           - All windows are getting navigatation commands mapped (like in help
                                             window)
                                           - Workaround for one of the E788 errors (originating from the plugin)
                                             during the auto-checkout. This part of the code has been cleaned up
                                             and simplified. During the auto-checkout, if there are other users
                                             editing the same file, it now results in the plugin echoing the output
                                             as a |WarningMsg|. If you missed to read the output (because you
                                             pressed <Enter> in advance), you can see it again using the
                                             |PFLastMessage| command. The other E788 originating from Vim code
                                             can't be fixed/workedaround, it has to be fixed by Bram.
                                           - Fixed broken submit from changelist.
                                           - When you create changelists, you can now safely undo to make any
                                             further changes, and save them. This also works for submissions (to
                                             edit description only), though you may have to remove the Files
                                             section before saving the change description.
perforce-    4.0     2006- 7.0     Hari    Uploading again, the previous attempt had a a file missing in the zip.
4.0.zip              09-01         Krishna
                                   Dara    - Using Vim7 features, so it is no longer backwards compatible with
                                             older Vim releases. All the logic using multvals has been changed to
                                             take advantage of the Vim7 Lists, so it should be a lot more cleaner
                                             and flexible.
                                           - No longer depends on multvals plugin.
                                           - It is now autoloaded on demand, which means it will help your vim
                                             session load faster. Read the impact on the installation due to this
                                             change, |perforce-installation|.
                                           - A new Cancel option for checkout prompt, see
                                             |perforce-automatic-checkout|. The default for checkout prompt is now
                                             &quot;Cancel&quot;.
                                           - The perforce/perforcemenu.vim needs to be loaded from your vimrc if
                                             you want menu to be enabled. See |perforce-installation|.
                                           - The plugin no longer removes the global user setting variables but you
                                             still need to call |:PFInitialize| for effect of some settings to
                                             propogate further. This should have no user visible impact (except in
                                             rare cases).  This will only make it easier to deal with settings. You
                                             can still use |:PFSettings| command conveniently for its prompting or
                                             completion features.
                                           - Setting a preset to the g:p4DefaultPreset directly now works fine.
                                           - Most settings can now be overridden at the buffer/window/tab level.
                                           - Bug: PFRefreshActivePane doesn't work well on the diff windows (especially
                                             when the ++c option is used).
perforce-    3.2     2006- 6.0     Hari    Release 3.2 for vim7 compatibility. There are a few enhancements too. This is
3.2.zip              05-08         Krishna probably the last version that will work in Vim 6.3/6.4.
                                   Dara    - Fixed PVDiff to work with two filenames. The problem was only with
                                             PVDiff command, as &quot;PF vdiff&quot; worked fine.
                                           - PFDiffOff command is a lot more flexible now, see |PFDiffOff|.
                                           - New command PPasswd for changing passwords.
                                           - Don't confirm revert if -a or -n option is passed.
                                           - Avoid accidentally loosing existing buffers while opening new ones
                                             from diff and other windows.
                                           - Recognize additional p4 commands as valid.
                                           - You can now pass multiple codeline modifiers, see
                                             |perforce-alternative-codeline-modifier|.
                                           - Misc. tuneups for peforce diff hyperlinking feature.
                                           - Misc. bugfixes in the menu.
perforce-    3.1     2004- 6.0     Hari    - This version introduces the concept of overriding settints at the
3.1.zip              10-28         Krishna   buffer/window level (an extension of the existing support for
                                   Dara      b:p4Options). Makes it easier to work with multiple clients from a single
                                             vim instance. Currently only the p4Client/p4Port/p4User/clientRoot can be
                                             set at buffer/window level.
                                           - Now view mappings are maintained separately for each client. This allows
                                             us to easily work with multiple clients at once. Also see
                                             |perforce-buffer-local-options|.
                                           - For diff hyperlinking, avoid refreshing the depot file if it already
                                             visible.
                                           - Now supports <pfitem> tag to mean the current list item. See |:<pfite>|
                                           - New :PExec command to make it easier to execute exeternal perforce
                                             commands directly, when plugin can't do what you want. See |PExec|.
                                           - PFDiffLink and PFDiffVLink commands couldn't handle &quot;diff -r&quot;
                                           output.
                                           - If the current directory is not same as the directory of file being
                                             resolved PFShowConflicts didn't work.
                                           - PItemOpen in describe window now opens the local file, as PItemDescribe
                                             can be used to open the depot file.
                                           - Misc. bug fixes:
                                               - Negative revisions are not working any more. E.g., PP #-1
                                               - PW is not using the custom completion, so revision specifier (#1)
                                                 still needs to be escaped.
                                               - While rerunning a command that opens up a new buffer (such as PD),
                                                 unexpected warning messages about matching an existing buffer.
                                                 Instead, it should silently refresh the output.
                                               - Diff hyperlinking, prints the depot file everytime, this causes
                                                 unnecessary delays.
                                               - PFRefreshActivePane would fail if there are filename special
                                                 characters in the command.
perforce-    3.0     2004- 6.0     Hari    Now requires Vim 6.3 and the latest versions of genutils and multvals
3.0.zip              08-11         Krishna plugins.
                                   Dara
                                           Too many changes to be listed here, read the |perforce-version-changes|
                                           section for details.

                                           Takes advantage of some of the new Vim 6.3 features.

                                           I recommend reading |perforce-troubleshooting|, |perforce-known-issues|,
                                           |perforce-tips| sections. Many of the other sections also have been updated,
                                           which are cross referenced from the version changes section.

                                           Please report issues using the new PFBugReport command.
perforce-    2.0     2003- 6.0     Hari    There are too many changes to mention here. Most notable ones being, the new
2.0.zip              10-30         Krishna online help for the plugin and the perforce ruler feature from Tom's perforce
                                   Dara    plugin which is now integrated into this with some improvements. Regenerate
                                           help tags after extracting the zip. I highly recommend reading through at
                                           least the installation, changes, troubleshooting and tips sections of the
                                           help. I also recommend at least glancing through the rest of the help to have
                                           an idea of what the plugin is capable of doing. I appreciate feedback.

                                           Download the new versions of multvals.vim and genutils.vim.
perforce-    1.3     2002- 6.0     Hari    - You need genutils.vim version (1.0.24)
1.3.zip              04-12         Krishna - Now the PSubmit and PDiff2 commands are enhanced. PSubmit can now take
                                   Dara    arguments that are directly passed to POpened to generate the list of files
                                           to submit. So it is possible to say &quot;PSubmit % #&quot; to open the
                                           template with only the current and alternate files or &quot;PSubmit //depot/
                                           branch/...&quot; to open the template with all the opened files under the
                                           given branch.
                                           - You can now pass in filters at the end of the commands. Just make sure you
                                           have a white space before the pipe. Ex:

                                             PChanges -s pending | grep hari

                                           - I added ^X^P command line mapping which works like the &quot;E&quot;
                                           command but provides more flexibility. I also added ^X^I command line mapping
                                           for list windows (such as PF changes), which inserts the current item name on
                                           to the command line. Try them, they are very useful.
                                           - New commands for clients, labels windows to create a new item from the
                                           current item as a template (type P).
                                           - In the filelist windows, you can now press p to print the current file and
                                           S to sync to the current file.
                                           - Another major change is improved command line parsing.
                                           - Also the syntax highlighting has been improved to cover more cases.
perforce-    1.2.2   2002- 6.0     Hari    Earlier, I have uploaded a wrong file as a zip file, I apologize for the
1.2.2.zip            04-02         Krishna mistake. I have deleted the old upload and am trying again.
                                   Dara
                                           This is just a minor patch release. Added useful WQ command which is same as
                                           the W command but will also quit the window if there is no error. Speeds up
                                           making changes to labels, jobs etc. You might still want to use W for
                                           submits, as you can copy the output into your integration plans or something
                                           like that. Also I made a typo in my previous release notes about the variable
                                           name for passing default diff options. The correct name is g:
                                           p4DefaultDiffOptions. Please use the latest version of genutils.vim which
                                           fixes a typo resulting in an error message while quitting help windows.
perforce-    1.2.0   2002- 6.0     Hari    - Perforce help window is now much better. It reuses the same window for all
1.2.0.zip            03-26         Krishna the help commands and maximizes too like the vim built-in window. It even
                                   Dara    restores the windows when you quit the help. Also navigating in the help
                                           window is much better as the cursor positions are remembered.
                                           - New command: PJobspec
                                           - g:p4DefaultChangesSize to pass in default diff options to all the diff
                                           operations. Set it to '-dc' to get diff with context.
                                           - Renamed g:p4DefaultChangesSize to g:p4DefaultListSize. This is now used
                                           even for jobs command.
                                           - g:p4MaxLinesInDialog to limit the number of lines that should be shown in
                                           the dialogs. Commands that normally show dialogs (such as PE) open a new
                                           window if this limit is exceeded. This avoids showing too many lines in the
                                           dialogs (such as PF edit ...)
                                           - Fixed labelsync command.
                                           - Fixed the delete in the list view. Now pressing D in the labels, changes
                                           etc. works.
                                           - <SHOW DIFFS> option on the describe window. Pressing <Enter> on this line
                                           expands it to show diff.
                                           - Some basic formatting options in the edit windows.
                                           - You need the 1.0.19 version of genutils.vim
perforce-    1.1.17  2002- 6.0     Hari    Fixed it to work on Unix, thanks to Kevin McCarthy for reporting the problem
1.1.17.zip           03-20         Krishna and a solution. I also added a basic syntax highlighting for the perforce
                                   Dara    windows (not complete yet). Extract the perforce.zip in your runtime
                                           directory.
perforce.vim 1.1.15  2002- 6.0     Hari    Minor patch release. Fixed PLabels command. Now O in PChanges correctly edits
                     03-19         Krishna the current change instead of showing the opened list. The opened list can be
                                   Dara    viewed by using the o (small case) command. Updated the usage header in the
                                           file.
perforce.vim 1.1.14  2002- 6.0     Hari    More featured, more robust, with more predictable results. Lots of bugs have
                     03-17         Krishna been fixed. Now, a command executed through PF or its shortcut are identical,
                                   Dara    so no more surprises (PF change and PChange are same). Thanks for the
                                           suggestion, Man. The code is also much more cleaner now. I have also improved
                                           the help header in the file, so read the first few lines for a good overview
                                           of the script's capabilities.
perforce.vim 1.1.8   2002- 6.0     Hari    Initial upload
                     03-08         Krishna
                                   Dara
