# ColdHex

A dark && flat && blue, QtCurve based theme for KDE featuring some GTK icon fixes, a custom white on black Sifr icon style for LibreOffice and some Firefox and KMail UI customizations.

![ColdHex Plasma screenshot](https://raw.githubusercontent.com/denydias/coldhex/master/screenshots/1-plasma.png)

ColdHex is heavily based on the following amazing third parties work:

* **Theme:** [Hex](http://garthecho.deviantart.com/art/Hex-439924084), by gartecho
* **Tray icons:** [Krayscale](http://kde-look.org/content/show.php/?content=133300), by kubicle
* **GTK icon fixes:** [kAwOken](http://alecive.deviantart.com/art/kAwOken-244166779), by alecive

This is how it looks with native Qt/KDE apps (Dolphin and Gwenview):

![ColdHex KDE applications screenshot](https://raw.githubusercontent.com/denydias/coldhex/master/screenshots/2-plasma_apps.png)

## Installation

Follow the steps bellow to install ColdHex. The installation procedure is based on Slackware64 -current multilib. Take for granted that destination paths are different for each Linux distribution. You have to figure out them for yourself.

### Main theme

1. Before continue, you must install [QtCurve-KDE4](http://slackbuilds.org/repository/14.1/desktop/QtCurve-KDE4/) and [QtCurve-Gtk2](http://slackbuilds.org/repository/14.1/desktop/QtCurve-Gtk2/);

2. Clone ColdHex repository:

    ```ShellSession
    $ git clone https://github.com/denydias/coldhex.git
    ```

3. Symlink (or copy) the following directories:

    ```ShellSession
    ln -s /path/to/coldhex/desktoptheme/ColdHex /home/jdoe/.kde/share/apps/desktoptheme/
    ln -s /path/to/coldhex/color-schemes/ColdHex.colors /home/jdoe/.kde/share/apps/color-schemes/
    ```

4. Open System Settings > Appearance > Style, choose 'QtCurve' in 'Widget style';

5. Click 'Configure...' button at right of 'Widget style', in the QtCurve configuration, 'Import...', select `/path/to/coldhex/ColdHex.qtcurve`, choose 'ColdHex' in 'Presets', 'Ok', 'Apply';

6. Select 'Color', choose 'ColdHex', 'Option' tab, disable 'Apply colors to non-KDE4 applications', 'Apply';

7. **Optional but strongly recommended:** install and select [kAwOkenWhite](http://alecive.deviantart.com/art/kAwOken-244166779) in 'Icons' configuration;

8. Select 'Fonts' and choose 'Droid Sans', size 8 for all but 'Small' (size 7,5) and 'Window Title' (size 9), enable 'anti-aliasing', 'Apply';

9. Select 'GTK Configuration' (you may have to install [this optional module](http://slackbuilds.org/repository/14.1/desktop/kde-gtk-config/)), choose 'QtCurve' for 'GTK2', 'oxygen-gtk' for 'GTK3', 'Droid Sans 8' for 'Font', 'Icons Only', disable both 'Show Icons', select 'Monochrome' for both 'Icon Themes', 'Apply';

10. Open System Settings > Workspace Appearance > Window Decorations, choose ´QtCurve', 'Apply';

11. Select 'Workspace Theme', choose 'ColdHex', 'Apply'.

Things will look a bit weird now. That's because you need to logout/login back (or reboot if you like) so KDE properly refresh everything. If you want to keep going with the optional parts bellow, continue reading and reload session at the end.

## GTK Icon Fixes

When you select QtCurve for GTK2 Theme, KDE GTK+ integration is going to refuse to show your selected icon theme for GTK+ application on your taskbar and system tray. This is particularly annoying for continuously open applications such as Firefox and Dropbox. To fix that open a terminal and run:

```ShellSession
cd /path/to/coldhex/tools/gtk_icons/
./gtk_icon_fix
```

At the end it'll ask for you root password to clean up icon caches. You are free to just not give it and git 'CTRL-C' if you Linux distro just run that at boot. You have to figure out if that's your case for yourself.

If you see errors such as `file not found` or `operation not permited`, then you might want to edit `gtk_icon_fix` script and change the following variables to your system needs:

```ShellSession
DROPBOX_DST=$HOME/.dropbox-dist/dropbox-lnx.x86_64-2.10.30/images/hicolor/16x16
FIREFOX_DST=/usr/share/icons/hicolor
```

**REMEMBER:** If you upgrade your system and the icons revert back to the original ones, run `gtk_icon_fix` again to fix them again.

## LibreOffice

ColdHex also provides an easy to apply workaround for LibreOffice white on black behavior. This is how it looks:

![ColdHex LibreOffice screenshot](https://raw.githubusercontent.com/denydias/coldhex/master/screenshots/3-gtk_libreoffice.png)

To apply it, run this the following in your terminal:

```ShellSession
cd /path/to/coldhex/tools/libreoffice/
./sifr_mogrify
```

Then follow onscreen rules.

## Firefox

You could get nice gray URLs in your Firefox's Location Bar dropdown.

![ColdHex Firefox screenshot](https://raw.githubusercontent.com/denydias/coldhex/master/screenshots/4-gtk_firefox.png)

Just edit (or create) your `.mozilla/firefox/anything.default/chrome/userChrome.css` to add:

```CSS
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

.ac-url-text {color:#787775 !important;}
```

Pay attention that the above is tested only in Firefox 32+. If you are in Slackware, make sure you have **NOT** compiled `QtCurve-Gtk2` package with the option `USERCHROME=no` in place.

## KMail

If your new messages color in Kmail just refuses to follow KDE system wide settings and appear as a difficult to read blue instead of a lighter one, go to KMail configuration, appearance, enable 'Use custom colors', set `#508ED8` to 'Unread message' color, 'Ok'.

That should have done it. Now you can logout/login to enjoy your new ColdHexed KDE.

## Licenses

My code for CodHex is licensed under [GNU GENERAL PUBLIC LICENSE Version 3](http://www.gnu.org/licenses/gpl-3.0.txt).

[Hex](http://garthecho.deviantart.com/art/Hex-439924084), by gartecho, [Krayscale](http://kde-look.org/content/show.php/?content=133300), by kubicle, and [kAwOken](http://alecive.deviantart.com/art/kAwOken-244166779), by alecive, have their own license terms.

LibreOffice is licensed under [Mozilla Public License v2.0](http://www.libreoffice.org/download/license/) by
The Document Foundation.
