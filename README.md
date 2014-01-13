#gmail-mbox-to-imap


gmail-mbox-to-imap is an adaptation of IMAP upload in order to transform Gmail tags into folders.

IMAP upload: http://imap-upload.sourceforge.net/, by OZAWA Masayuki

##Installation

    git clone https://github.com/ldidry/gmail-mbox-to-imap.git
    cd gmail-mbox-to-imap

##Usage

You will need to grab your Gmail's messages in mbox format. Go to <https://google.com/takeout>, create an archive containing your mails, download it and unzip it.

Then:

    ./gmail-mbox-to-imap.py --host=mail.example.com --ssl --user=user@example.com --password=your-password migration-from-gmail.mbox

More options with:

    ./gmail-mbox-to-imap.py --help

##Issues

###Language

Google translates its labels in your native language. For example, in french, Inbox is called "Boîte de Réception". Plus, in the `X-Gmail-Labels`, the encoding seems to be not well interpreted, so I use regexes to translate "Boîte de Réception" to "INBOX", the absence of the "Non lus" label adds a "\Seen" flag to the, and some other fixes.

So, if you're not french, edit the script around the line 166 and change regexes to match your language.

If someone knows Python well and want to create some sort of localization function that use the good regex for a chosen language : welcome aboard !

###Strange behavior

When trying the script, it seems to let a lot of mails unseen while they were already seen. I don't know why. Again, if you know Python, welcome aboard !

##License

gmail-mbox-to-imap is released under the terms of the MIT license. See License.txt for details.
