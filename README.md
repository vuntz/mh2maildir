`mh2maildir` is a perl script to convert a mailbox in the MH format to the Maildir format. The name of this script shows how imaginative I can be ;-)

A few months ago (it was still 2004), I changed my e-mail habits. I used to use Sylpheed to download all my mails using POP3, and then I realized it was much more convenient to always have my mails available on an IMAP server. I didn't want to use the infamous [mbox](http://en.wikipedia.org/wiki/Mbox) format, and I quickly found that the [Maildir](http://cr.yp.to/proto/maildir.html) format was the best format to fit my needs. And there I was, wanting to convert my mailbox in the MH format to the Maildir format.

After searching a bit on Internet, I found two scripts handling this task. But both had limitations:

  * [mh2maildir](http://www.informatik-vollmer.de/software/mh2maildir.html), by Jürgen Vollmer. This script uses procmail and is thus quite slow. Moreover, it does not handle really well the directory names (eg, when there's a space or a dot in the name), and the mail status is not saved (read, not read, etc.).
  * [mh2Maildir](http://rslomkow.org/Pretender/scripts/), by Robin Slomkowski. This script does not handle subdirectories and marks all mails as read.

Since I was not satisfied by the solutions I found, I chose to write my own script. This script would use the metadata from Sylpheed, which would make it easy to keep the mails status. I took Robin Slomkowski's script as a basis, and improved it. Here are the features I added:

  * recursively convert directories
  * keep the directory names
  * if available, use metadata from Sylpheed to determine if a mail is read or not read, marked as important, deleted, or if it has been replied to
  * fallback on the mail headers to determine if a mail is read or not read, deleted, or if it has been replied to
  * dates of the mails are kept and used for the filenames
  * probably some other minor features...

Of course, before you use this script, it is highly recommended that you backup your mails and you stop the reception of new mails. The theory says no mails of the mailbox in the MH format should be deleted. But that's only theory...

Here's the basic example, where mails will be put in `$HOME/Maildir`:

```
mh2maildir /path/to/MH/dir
```

Here's another example:

```
mh2maildir /path/to/MH/dir /path/to/new/Maildir
```

There is no known bug. But since I'm in no way perfect, there should be some bugs ;-) All contributions to improve the script is of course welcome.

This script is released under the GPL 2.0 license.
