# Awesome Swatch Internet Time (.beats) [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A curated list of awesome Swatch Internet Time libraries, software and resources.


## Official, Basic Info

* [Swatch Internet Time webpage](https://www.swatch.com/de-at/internet-time.html) with a [weird video](https://www.youtube.com/watch?v=4ROTh6gZz3Y)
* [Wikipedia](https://en.wikipedia.org/wiki/Swatch_Internet_Time)


## Web Clocks and Converters

* [internet-ti.me](https://internet-ti.me/)
  * great tool for non-beat users: [https://internet-ti.me/@610](https://internet-ti.me/@610) -- directly shows time in local time and world time zones
  * [also has a converter](https://internet-ti.me/converter)
  * [source code](https://github.com/ticky/internet-ti.me) by Jessica Stokes
* [swatchclock.com](http://www.swatchclock.com/)
  * [source code](https://github.com/Clidus/swatch)
* [gwil.co](http://gwil.co/internet-time/)
  * with links to some implementations
* [CSGNetwork converter and display](http://www.csgnetwork.com/csgbmtcvt.html)


## Community

* [on Reddit](https://www.reddit.com/r/SwatchInternetTime/)
* [Github Discussion here on the repo](https://github.com/ERnsTL/awesome-internettime/discussions)


## Original Swatch Net Time watches

* Swatch does not sell them any more.
* search for *Swatch Originals .Beat Net Time SQN101*


## Smart Watches

* Apple Watch:  [internet-beat by Jessica Stokes](https://apps.apple.com/us/app/internet-beat/id304080578)
  * https://at-watch.jessicastokes.net/ -> https://apps.apple.com/app/at-watch/id1440309007
* Android und Galaxy Watch: [by derfreimann](https://apkgk.com/com.derfreimann.watchfaces.internetTime)
    * with estimated total number of installs
* [Github search for watch face internet time beats](https://github.com/search?q=watch+face+internet+time+beats)
* Pebble watch:  [watch faces on Github](https://github.com/search?q=pebble+internet+time+beats)
  * getpebble.com -> fitbit.com seems to have been bought up
* [in-VR clock](https://github.com/ticky/internet-ti.me-VR)


## Mobile

* Android:  [by cbateman](https://play.google.com/store/apps/details?id=xyz.cbateman.beattimewidget&hl=de&gl=US)
* iPhone:  [beat-internet-time](https://apps.apple.com/at/app/beat-internet-time/id1570173118)
* iOS and Apple Watch:  [NetTime by Simon Rice](https://github.com/SimonRice/NetTime)


## Operating Systems

* MacOS: [dotbeat](https://swiftobc.com/repo/amiantos-dotbeat-swift-datetime)
* Windows: [Beat-Time](https://github.com/optoisolated/Beat-Time)

GNOME:
* [clock Override](https://extensions.gnome.org/extension/1206/clock-override/)
  * would be best solution since it can do @ time already
  * but it is necessary to fix it for Gnome v40+, author is not happy with performance on v40+ but it is possible
* [date menu formatter](https://extensions.gnome.org/extension/4655/date-menu-formatter/)
  * works for Gnome v40+ but has no @time
  * Modification for @time with help of code snippet [from this function in clock-override extension](https://github.com/stuartlangridge/gnome-shell-clock-override/blob/c6578c3d1993cb6cba599d1191e45655a7ef76b0/formatter.js#L94), bit of a hack:
    ```
    editor ~/.local/share/gnome-shell/extensions/date-menu-formatter@marcinjakubowski.github.com/extension.js
    ```
  * Add import and timezone at top (note that date-menu-formatter uses an other date system for the other date formats, todo):
    ```
    const GLib = imports.gi.GLib;
    let bmttz = GLib.TimeZone.new('+01');
    ```
  * Add beat time display in ```update()```:
    ```
    setText(Utils.convertFromPattern(this._formatter.format(PATTERN, new Date())) + "  @" + this.formatBeatTime());
    ```
  * Add function below:
    ```
    formatBeatTime() {
        var bmtnow = GLib.DateTime.new_now(bmttz);
        var beat_time = 0 | ( bmtnow.get_second() + ((bmtnow.get_minute() * 60) + (bmtnow.get_hour() * 3600)) ) / 86.4;
        return ('000' + beat_time).slice(-3);
    }
    ```
  * Test change without rebooting:
    ```
    dbus-run-session -- gnome-shell --nested --wayland
    ```

KDE:
* TODO


## Applications

* [Slack Bot und slash command](https://github.com/daph/beatbot-rs) written in Rust
* Discord on [on Github](https://github.com/search?q=internet+time+beat+discord&type=Repositories) using a Bot
* [emacs](https://www.emacswiki.org/emacs/InternetTime)
* TODO Thunderbird
* TODO Outlook
* ...more?


## Programming Languages, Libraries

Project listings:
* [Github topic swatch-internet-time](https://github.com/topics/swatch-internet-time)
* [Github topic internet-time](https://github.com/topics/internet-time)
* Gitlab and Sourcehut provided 0 results

Rust:
* [on Github](https://github.com/search?l=Rust&q=internet+time+beat&type=Repositories)
* [beats crate](https://crates.io/crates/beats)
* [gil_beats by Gil Desmarais](https://github.com/gildesmarais/gil_beats)
  * algorithm is unefficient

Go:
* [beats by Peter Hellberg](https://github.com/peterhellberg/beats)

C:
* [beats by j0hax](https://github.com/j0hax/beats) - also with links to other C implementations
* TODO coreutils formatter %@ ? date tool? glibc?

JavaScript:
* [beats by azappa](https://github.com/azappa/beats)
* [Internet Time for your in-VR wristwatch](https://github.com/ticky/internet-ti.me-VR)

Python:
* [code snippet](https://github.com/153/toys/blob/master/beat-time.py)
* [SwatchTime by Henry Malinowski](https://github.com/henry-malinowski/SwatchTime)
* [AmigaOS 1.x Workbench clock in PyGame](https://github.com/mdoege/AmigaClock)

PHP:
* [in standard library](https://www.php.net/manual/en/function.date.php) using the [DateTime format "B"](https://www.php.net/manual/en/datetime.format.php)

C#:
* [on Stackoverflow](https://stackoverflow.com/questions/10479991/convert-datetime-to-swatch-internet-time-beat-time)

Elixir:
* [beat_time by ZuraGuerra](https://github.com/ZuraGuerra/beat_time)

Typescript:
* [dot-beat-time](https://github.com/sgwilym/dot-beat-time)
* [use-beat-time](https://github.com/sgwilym/use-internet-time) for React apps

Kotlin and Android:
* [beat time library for Android](https://github.com/raheemadamboev/server-time-android)

Perl:
* [DateTime::Complete](https://metacpan.org/pod/Bundle::DateTime::Complete) with module *IBeat*
* [DateTime::Format::Builder::Parsers::Quick](https://metacpan.org/pod/DateTime::Format::Builder::Parser::Quick) for parsing


## Method of calculation

* Get time ```now``` either in UTC or UTC+1 where Biel is located. Re-use the timezone object since it will not change. Getting UTC is usually easy, then simply add ```+1``` to the hour part in the calculations below.
* Method using seconds as basis using multiplication. On x86, multiplication is faster than division and floating point division is faster than integer division.
  ```
  beats = ( now.get_second() + ((now.get_minute() * 60) + ((now.get_hour() + 0) * 3600)) ) / 86.4
  ```
* Method using hour as basis using division:
  ```
  beats = (now.get_hour() + (now.get_minute() / 60) + now.get_second() / 3600) * 1000 / 24
  ```
* Method using some form of "time since midnight" in UTC+1. For example, if this is efficient to acquire:
  ```
  unixutc = time(NULL);
  # unix time is always UTC, so add 1 hour
  unixbmt = unixutc + 3600;
  # get seconds since midnight
  secsincemidnight = unixbmt % 86400;
  beats = secsincemidnight / 86.4;
  ```
* ... more?


## Discussions

* [Discussion on c2wiki](https://wiki.c2.com/?InternetTime)
  * [The Myth of Internet Time by Andrew Odlyzko](http://www.dtc.umn.edu/~odlyzko/doc/internet.time.myth.txt)
* [Fifth World wiki](https://fifthworld.fandom.com/wiki/Swatch_Internet_Time) -- [what is a Fifth World country](https://fifthworld.fandom.com/)
* [on TimeAndDate](https://www.timeanddate.com/time/internettime.html)

Advantage:
* Worldwide synchronized clocks.

Disadvantage:
* Cannot easily deduce if somebody is awake at that time or not. Then again,
  * they don't have to accept the meeting invitation for that time. OTOH, avoid meetings anyway.
  * There is often times an online status function in internet communications platforms and telephone systems these days have a DND function when not available for calls.
* There is UTC.

Limitations:
* The Earth will always go around the sun.


## News Articles

* [ZDnet from 2000](https://www.zdnet.com/article/do-you-have-the-internet-time/), also with sales data (2M devices in first 2 years, time converter downloaded over 5 million times in first 2 years)
* [How stuff works](https://electronics.howstuffworks.com/gadgets/clocks-watches/internet-time.htm)
* [Baltimore Sun article from 1999](http://articles.baltimoresun.com/1999-04-08/news/9904080326_1_swatch-internet-time-keeping-time)
* [Vice 2015](https://www.vice.com/en/article/gyy4bm/remember-when-swatch-invented-a-new-time-system-for-the-internet)
* [academic dict](https://en-academic.com/dic.nsf/enwiki/210738)
* [CNN 1999](http://edition.cnn.com/TECH/computing/9902/26/t_t/internet.time/)


## Related

* [New Earth Time](https://newearthtime.net/) based on 360 degrees per day. So un-decimal.
* Using UTC as basis for Internet Time instead of UTC+1 ("BMT").
* UTC iself.
