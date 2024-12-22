# firefox-stable
Bash script for linux to have the stable release from Mozilla Foundation

## Purpose
Any reason you can think of for having the oficial and overall working firefox release for linux, instead of the snap or any other that can have issues.

## Installation
Download the script and place it for your preferred cron usage. Placing it in <code>/etc/cron.weekly</code> is a good option.

You can run the script manually whenever you want and/or let cron run it. In any case, the script needs root privileges because it needs write permissions in <code>/usr/local/</code>.
The script creates a wrapper in <code>/usr/local/bin/firefox</code> so it takes precedence in your system. Also, downloads the latest stable release from Mozilla website and places it in <code>/usr/local/firefox-${VERSION}</code>, with a symlink <code>/usr/local/firefox</code> pointing to the release, so the wrapper doesn't fail.

The default is the es-ES release, but if you run the script with any other lang code as first parameter, that lang code will be used instead.

## Switching from other firefox release
First of all, you have to identify your working profile, because firefox, from time to time, in some releases, creates a new profile and uses it as default, regardless anything else. So, before having the wrapper as default, you have to run <code>firefox -p</code> to see your existing profiles. Maybe you have to try and error until you find your working profile. Once you identify it, you can rename to a proper name so you don't forget it in the future. Also, find the location of the working profile. Since the Mozilla release expects the profiles in <code>~/.mozilla/firefox</code> and if your working profile is in a different path, the wrapper may not find it. In that case, you can copy or move the entire profile directory to the standard location.

Once your old working profile is enabled, mark the options for setting it as default and launching without asking. This should work until the next time a new release creates a new profile for you and sets it as default, in whose case you will have to run again <code>firefox -p</code> and choose your profile as default.

It's up to you to remove any other profiles you consider unnecessary.
