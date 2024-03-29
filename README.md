# Awesome Swatch Internet Time (.Beats) [![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)

A curated list of awesome Swatch Internet Time libraries, software and resources.

Contributions like pull requests and discussion are welcome :-)

## Contents

* [Official, Basic Info](#official-basic-info)
* [Web Clocks and Converters](#web-clocks-and-converters)
* [Community](#community)
* [Original Swatch Net Time Watches](#original-swatch-net-time-watches)
* [Smart Watches](#smart-watches)
* [Mobile](#mobile)
* [Operating Systems](#operating-systems)
* [Applications](#applications)
* [Programming Languages, Libraries](#programming-languages-libraries)
* [Method of Calculation](#method-of-calculation)
* [Discussions](#discussions)
* [News Articles](#news-articles)
* [Related](#related)


## Official, Basic Info

* [Swatch Internet Time webpage](https://www.swatch.com/de-at/internet-time.html) - it has a [funny video](https://www.youtube.com/watch?v=4ROTh6gZz3Y) about an important gotcha with Internet Time: Because it is the same time everywhere does not mean that they are in the same place of their day/night cycle.
* [Wikipedia](https://en.wikipedia.org/wiki/Swatch_Internet_Time)


## Web Clocks and Converters

* [internet-ti.me](https://internet-ti.me/)
  * great tool for non-beat users: [https://internet-ti.me/@610](https://internet-ti.me/@610) -- directly shows time in local time and world time zones, generates metadata for embedding into social media
  * [also has a converter](https://internet-ti.me/converter)
  * [source code](https://github.com/ticky/internet-ti.me) - By Jessica Stokes.
* [swatchclock.com](http://www.swatchclock.com/)
  * [source code](https://github.com/Clidus/swatch)
* [gwil.co](http://gwil.co/internet-time/)
  * with links to some implementations
* [CSGNetwork converter and display](http://www.csgnetwork.com/csgbmtcvt.html)


## Community

* [on Reddit](https://www.reddit.com/r/SwatchInternetTime/)
* [GitHub Discussion here on the repo](https://github.com/ERnsTL/awesome-internettime/discussions)
* [Github projects with tag "swatch-internet-time"](https://github.com/topics/swatch-internet-time)
* [Github projects with tag "internet-time"](https://github.com/topics/internet-time)


## Original Swatch Net Time Watches

* Swatch does not sell them any more.
* search for *Swatch Originals .Beat Net Time SQN101*


## Smart Watches

* Apple Watch:  [internet-beat by Jessica Stokes](https://apps.apple.com/us/app/internet-beat/id304080578)
  * https://at-watch.jessicastokes.net/ -> https://apps.apple.com/app/at-watch/id1440309007
* Android und Galaxy Watch: [by derfreimann](https://apkgk.com/com.derfreimann.watchfaces.internetTime)
    * with estimated total number of installs
* [GitHub search for watch face internet time beats](https://github.com/search?q=watch+face+internet+time+beats)
* Pebble watch:  [watch faces on GitHub](https://github.com/search?q=pebble+internet+time+beats)
  * getpebble.com redirects to fitbit.com, so it seems Pebble has been bought by Fitbit
* [in-VR clock](https://github.com/ticky/internet-ti.me-VR) - Written in JavaScript.


## Mobile

* Android:  [by cbateman](https://play.google.com/store/apps/details?id=xyz.cbateman.beattimewidget)
* iPhone:  [beat-internet-time](https://apps.apple.com/at/app/beat-internet-time/id1570173118)
* iOS and Apple Watch:  [NetTime by Simon Rice](https://github.com/SimonRice/NetTime)


## Operating Systems

* MacOS: [dotbeat](https://swiftobc.com/repo/amiantos-dotbeat-swift-datetime) and [dotbeat developer repository](https://github.com/amiantos/dotbeat)
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
    If you want to add UTC display as well:
    ```
    var now = new Date();
    var utc = new Date(now.getTime() + now.getTimezoneOffset() * 60000);
    setText(
        Utils.convertFromPattern(this._formatter.format(PATTERN, now)) + 
        "  @" + this.formatBeatTime() + 
        "  Z" + Utils.convertFromPattern(this._formatter.format('kk:mm', utc))
    );
    ```
    If you want the ISO 8601 calendar week as well:
    ```
    var now = new Date();
    var utc = new Date(now.getTime() + now.getTimezoneOffset() * 60000);
    setText(
        Utils.convertFromPattern(this._formatter.format(PATTERN, now)) + 
        "  @" + this.formatBeatTime() + 
        "  Z" + Utils.convertFromPattern(this._formatter.format('kk:mm', utc)) + 
        "  W" + now.getWeekNumber()
    );
    ```
    ...and add function for ISO8601 calendar week at the top from [the source](https://stackoverflow.com/questions/6117814/get-week-of-year-in-javascript-like-in-php)
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
  * Restart GNOME shell by pressing Alt+F2 and enter "r" for restart (all windows remain open as they were).

KDE:
* TODO


## Applications

* [Slack Bot und slash command](https://github.com/daph/beatbot-rs) - Written in Rust.
* Discord on [on GitHub](https://github.com/search?q=internet+time+beat+discord&type=Repositories) using a Bot
  * [another Discord Bot](https://github.com/Xe/withinbot)
* [emacs](https://www.emacswiki.org/emacs/InternetTime)
* TODO Thunderbird
* TODO Outlook


## Programming Languages, Libraries

Project listings:
* [GitHub topic swatch-internet-time](https://github.com/topics/swatch-internet-time)
* [GitHub topic internet-time](https://github.com/topics/internet-time)
* Gitlab and Sourcehut provided 0 results

Rust:
* [on GitHub](https://github.com/search?l=Rust&q=internet+time+beat&type=Repositories)
* [beats crate](https://crates.io/crates/beats)
* [gil_beats by Gil Desmarais](https://github.com/gildesmarais/gil_beats)
  * algorithm is unefficient
* [daph/beats](https://github.com/daph/beats)

Go:
* [beats by Peter Hellberg](https://github.com/peterhellberg/beats)

C:
* [beats by j0hax](https://github.com/j0hax/beats) - Also with links to other C implementations.
* TODO coreutils formatter %@ ? date tool? glibc? -- [date(1) uses ```fprintftime()```](http://www.maizure.org/projects/decoded-gnu-coreutils/date.html) and this again uses ```strftime()``` from glibc.

Shell script:

The script is so trivial, I show it here directly:

```sh
 $ printf "@$(( ( ( ( $(date "+%s") + 3600 ) % 86400 ) * 10 ) / 864 ))\n"
```

JavaScript:
* [beats by azappa](https://github.com/azappa/beats)

TypeScript and React:
* [dot-beat-time](https://github.com/sgwilym/dot-beat-time)
* [React module](https://github.com/sgwilym/use-internet-time)
* [internet-time by JaviToro](https://github.com/JaviToro/internet-time)

Python:
* [code snippet](https://github.com/153/toys/blob/master/beat-time.py)
* [SwatchTime by Henry Malinowski](https://github.com/henry-malinowski/SwatchTime)
* [AmigaOS 1.x Workbench clock in PyGame](https://github.com/mdoege/AmigaClock)
* [toys by 153](https://github.com/153/toys)

PHP:
* [in standard library](https://www.php.net/manual/en/function.date.php) - using the [DateTime format "B"](https://www.php.net/manual/en/datetime.format.php)

C#:
* [on Stack Overflow](https://stackoverflow.com/questions/10479991/convert-datetime-to-swatch-internet-time-beat-time)

Elixir:
* [beat_time by ZuraGuerra](https://github.com/ZuraGuerra/beat_time)

Typescript:
* [dot-beat-time](https://github.com/sgwilym/dot-beat-time)
* [use-beat-time](https://github.com/sgwilym/use-internet-time) - For React apps.

Java:
* [Swatch-Internet-Time](https://github.com/AlexanderJonsson/Swatch-Internet-Time)

Kotlin and Android:
* [beat time library for Android](https://github.com/raheemadamboev/server-time-android)

Perl:
* [DateTime::Complete](https://metacpan.org/pod/Bundle::DateTime::Complete) - With module *IBeat*.
* [DateTime::Format::Builder::Parsers::Quick](https://metacpan.org/pod/DateTime::Format::Builder::Parser::Quick) - For parsing.


## Method of Calculation

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
* Any more?


## Discussions

* [Discussion on c2wiki](https://wiki.c2.com/?InternetTime)
  * [The Myth of Internet Time by Andrew Odlyzko](http://www.dtc.umn.edu/~odlyzko/doc/internet.time.myth.txt)
* [Fifth World wiki](https://fifthworld.fandom.com/wiki/Swatch_Internet_Time) - [what is a Fifth World country](https://fifthworld.fandom.com/)
* [on TimeAndDate](https://www.timeanddate.com/time/internettime.html)
* [by Sandra](https://portal.mozz.us/gemini/idiomdrottning.org/beat-time) - original at gemini://idiomdrottning.org/beat-time

Advantage:
* Worldwide synchronized clocks.

Disadvantage:
* Cannot easily deduce if somebody is awake at that time or not. Then again,
  * they don't have to accept the meeting invitation for that time. OTOH, avoid meetings anyway.
  * There is often times an online status function in internet communications platforms and telephone systems these days have a DND function when not available for calls.
* There is UTC.

Limitations:
* The Earth will always go around the sun. Meaning, it will never be physically day or night everywhere at the sime time. There will always be two choices: 
  1. Favoring the local day/night and roughly following the biological cycle but having to calculate for worldwide coordination or
  2. favoring easy worldwide coordination without calculations, as in the case of Internet Time, but requiring to take care of the availability of others, which in today's networked systems is easy to do.


## News Articles

* [ZDnet from 2000](https://www.zdnet.com/article/do-you-have-the-internet-time/) - Also with sales data (2M devices in first 2 years, time converter downloaded over 5 million times in first 2 years).
* [How stuff works](https://electronics.howstuffworks.com/gadgets/clocks-watches/internet-time.htm)
* [Baltimore Sun article from 1999](http://articles.baltimoresun.com/1999-04-08/news/9904080326_1_swatch-internet-time-keeping-time)
* [Vice 2015](https://www.vice.com/en/article/gyy4bm/remember-when-swatch-invented-a-new-time-system-for-the-internet)
* [academic dict](https://en-academic.com/dic.nsf/enwiki/210738)
* [CNN 1999](http://edition.cnn.com/TECH/computing/9902/26/t_t/internet.time/)


## Related

* [Github projects with tag "decimal-time"](https://github.com/topics/decimal-time)
* [Github projects with tag "metric-time"](https://github.com/topics/metric-time)
* [New Earth Time](https://newearthtime.net/) - Based on 360 degrees per day. So un-decimal.
* Using UTC as basis for Internet Time instead of UTC+1 ("BMT").
* UTC iself.
