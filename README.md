version 1.01 (Mar 03, 2016)

        + Added WRITE capability to Folder Images.Initially only Atari DOS 2/2.5 compatible. All DOS operations
        except Format Disk and Duplicate Disk are supported.Maximum file write size is limited to 124KB or 1010
        sectors (due to DOS not utilizing sectors numbers beyond 1023 when writing a new file). Larger files can
        however be read from a Folder Image because AspeQt recycles the sector numbers it is handing out to DOS
        once the number hits 1024, and DOS does not care about the sector numbers when reading /loading a file.
        Folder Images can also be made bootable with DOS option "Write DOS Files", this integrates well with,and
        complements the existing "Folder Boot Option" feature of AspeQt. Only 64 file entries can be accommodated
        within a folder image due to Atari DOS limitation. A special file called $boot.bin will be created in the
        folder if the folder is made bootable. The file however will not show up on a DOS directory listing and
        does not count as one of the 64file entries. Currently MyDOS is only supported in Atari Compatible mode,
        meaning MyDOS specific features like sub-directories will not work. The next release will hopefully add
        full MyDOS compatibility and next comes SpartaDOS/SDX file system compatibility. Currently SDX have good
        read compatibility and some write capability through the use of ATARIDOS.SYSdriver, but no extensive tests
        have been done yet, so if you want to try it expect some problems.

        + Added menu item to Tools menu to launch ALibPc (Atari Librarian for PC). ALibPc is a separate standalone
        module designed to organize, view and manage Atari 8 bit software libraries on a PC. It can also be used
        to archive Atari 8 bit disks/software by connecting an Atari disk drive to your PC by a means of 10502PC
        interface such as my SIO2PC/10502PC Dual-USB device.

        - Removed the Print button from the "User Manual" window due to a bug in Qt (v5.4.0)which caused the
        printed output to be out of alignment with missing pages. The button will be reimplemented after the
        bug is fixed. In the meantime see below for an alternative.

        + Added a "Save as PDF" button to the Documentation Window. This will produce a local PDF copy of the
        most recent ONLINE documentation in PDF format in the language translated to by BING (if applicable).
        The document will be saved to the user's Desktop folder.If your documentation is displayed from the local
        html copy rather than ONLINE, it will then produce a PDF copy of the local documentation.You can then
        print a hard copy of the PDF file from your favourite PDF viewer. (Note: PDF printing is not affected by
        the above Qt printing bug)

        + Added capability to associate image file types thru apps UI .ATR,.PRO,.XFD,.XEX and .CAS with AspeQt.
        Double clicking on such a file will launch Aspeqt and the file will be automatically mounted to disk slot
        D1:. You can also create a short cut on your desktop or on another folder and specify an image file name
        with it's full path as a command line argument to achieve the same effect. In this case if the file
        specified can not be found AspeQt will display a warning message and continue loading as if no argument
        was passed.

        + Added "Use Ramdisk" option to "Boot Folder Options" dialog. When a folder is made bootable, a ramdisk
        won't be setup by default unless this option is checked.

        + Added a keyboard shortcuts help screen, and an option to hide the Log Window

        * Version numbering scheme was changed from x.x.x format to x.xx format.

        * Starting with v1.01 this branch of AspeQt will now be identified as "AspeQt vx.xx - A8W Edition"
        as there are now other forks and branches available from various other sources. Make sure you use the
        A8W Edition of AspeQt with SIO2PC devices purchased from me to guarantee future compatibility and
        technical support.

        * Minimizing the main window of AspeQt to the task bar did not work as expected. Fixed the problems
        and added a context menu to the taskbar icon which is activated by a right-click. You can now perform
        various actions when AspeQt main window is minimized to task bar.

        * Previously experimental handshake mode (NONE) is now added as a permanent handshake method. In this
        mode AspeQt can be used with SIO2PCdevices based on Serial-to-USB chips that don't provide a handshake
        signal (i.e. DSR, CTS or RI). It will also allow the use of wireless (i.e. Bluetooth) SIO2PC solutions.
        In this latter case Atari will need to use a custom OS like HIAS Hi-Speed OS, modified to handle longer
        SIO timeouts. Real drives can be mixed with AspeQt virtual drives when handshake NONE is used, however
        there is a very slight chance that AspeQt may interpret some random data as command frames, and possibly
        corrupt/damage real disk data. The likelihood of this happening is less than 1 in trillion but it exists
        nonetheless. So if you're using handshake NONE, and concerned about the possibility of data corruption,
        do not use real drives and make sure "auto commit" is turned OFF on your AspeQt drive slots so that in
        case any data corruption occurs it could be easily be reversed by ejecting the disk image. Personally
        I have so far never experienced any problems, but your mileage may vary, so you are now warned.

        * Log Display Window is completely reworked to fix a few bugs which caused unexpected behaviour in log
        window displayFilter by drive number logic has also been cleaned up.

        * Previous change to the Format time out value (from $03 to $E0) caused Atari to experience long waits
        on virtual drives if the disk on the drive is read-only or write-protected and the format was denied.
        Re-implemented disk format logic to fix the problem.

        * Fixed some problems with disk geometry information, more specifically VTOC values were not accurate for
        a freshly formatted DOS disk

        * Changed "Use Larger font" setting to a more flexible "Use Custom font size" setting. The font size is
        now user selectable within a reasonable size range.The log window text is now also resized along with
        drive slot descriptions

        * Cassette playback window is redesigned, fixed the progress bar which never worked before.

        * Various other GUI related changes and changes to streamline the code.
