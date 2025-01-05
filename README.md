# Awesome Swatch Internet Time (.Beats) [![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)

A curated list of awesome Swatch Internet Time libraries, software and resources.

Contributions like pull requests, issues and discussion are welcome :-)

## Contents

* [Official, Basic Info](#official-basic-info)
* [Web Clocks and Converters](#web-clocks-and-converters)
* [Community](#community)
* [Physical Clocks and Watches](#physical-clocks-and-watches)
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
* It seems that Charly Alberti invented the idea as *I-Time* for "Internet Time", sent it to Swatch as a business proposal and they made "Swatch Internet Time" out of it a few months later. ([Newspaper article](https://hackaday.io/project/193777-the-curious-case-of-swatch-internet-time), [Charly Alberti commenting on it in comments section](https://hackaday.com/2023/11/27/swatch-internet-time-watch-doesnt-miss-a-beat/), [Miami New Times article](https://www.miaminewtimes.com/music/silicon-bitchin-6356576)). The website for it was [www.i-time.com](https://web.archive.org/web/20001109155300/http://www.i-time.com:80/) and was online from 1998 to 2001.


## Web Clocks and Converters

* [internet-ti.me](https://internet-ti.me/)
  * meeting aid via URL for non-beat users: [https://internet-ti.me/@610](https://internet-ti.me/@610) -- directly shows time in local time and world time zones, generates metadata for embedding into social media
  * [also has a converter](https://internet-ti.me/converter)
  * [source code](https://github.com/ticky/internet-ti.me) - By Jessica Stokes.
* [beats.wiki](https://beats.wiki/)
  * clock re-calculates precisely, ie. at correct sub-second interval
  * updates the HTML title, so you get time in browser tab title
  * has a meeting aid via URL: [https://beats.wiki/2021-08-06@31.94](https://beats.wiki/2021-08-06@31.94)
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


## Physical Clocks and Watches

The Original Swatch Net Time Watches:

* Swatch does not sell them any more.
* search for *Swatch Originals .Beat Net Time SQN101*

Physical clocks:

* [Round self-made clock by Roni Bandini, reported on Hackaday, with comments from Charly Alberti](https://hackaday.com/2023/11/27/swatch-internet-time-watch-doesnt-miss-a-beat/) ([source code](https://github.com/ronibandini/XiaoRoundInternetHour), [project details, with newspaper article about Charly Alberti's iTime](https://hackaday.io/project/193777-the-curious-case-of-swatch-internet-time))


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

* Android:  [by cbateman](https://play.google.com/store/apps/details?id=xyz.cbateman.beattimewidget) as a handy widget for the home screen
* Android:  [by mirk0dex](https://f-droid.org/packages/eu.mirkodi.swatchbeatclock/) as a regular app it seems
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
* Suggestion to use *conky* desktop widgets ([link](https://www.answeroverflow.com/m/1311596991620317195)) but not sure if there is a ready-made clock showing .beats
* The [Modern Clock](https://www.reddit.com/r/kde/comments/ugjcxo/new_clock_widget_for_kde_modern_clock/) widget seems popular, and it looks very promising to modify the source code:
  * [adding "UTC" time in addition to "Local" should be possible](https://github.com/Prayag2/kde_modernclock/blob/5c86f0f23d2646be7e9872fc5e769bdce259af92/package/contents/ui/main.qml#L41)
  * [then add calculation and display in main.qml here](https://github.com/Prayag2/kde_modernclock/blob/5c86f0f23d2646be7e9872fc5e769bdce259af92/package/contents/ui/main.qml#L58)
  * TODO add copy-paste version for easy use


## Applications

* [Slack Bot und slash command](https://github.com/daph/beatbot-rs) - Written in Rust.
* Discord on [on GitHub](https://github.com/search?q=internet+time+beat+discord&type=Repositories) using a Bot
  * [another Discord Bot](https://github.com/Xe/withinbot)
* [emacs](https://www.emacswiki.org/emacs/InternetTime)
* TODO Thunderbird
* TODO Outlook
* Google Sheets:
  * Set the timezone of the Sheet to UTC = "GMT +0 (no daylight savings time" in File - Properties. (As of 2024-12, there is no function to get ```NOW()``` time in a specific time zone; all times are based on the time zone set in the sheet properties.)
  * In A1, add ```=NOW()```
  * Somewhere else, enter ```=MOD( ( HOUR(A1) * 3600 + MINUTE(A1) * 60 + SECOND(A1)  + 3600) / 86.4, 1000)```
  * If your language or region setting uses comma as decimal separator, the formula is ```=MOD( ( HOUR(A1) * 3600 + MINUTE(A1) * 60 + SECOND(A1)  + 3600) / 86,4; 1000)```
  * This formula automatically adds +1 one for the UTC+1 basis of Swatch Internet Time.


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

Interval of calculation:
* The correct interval is every full beat or every 0.1 or 0.01 beats, depending on the displayed accuracy. This is slightly faster than 1 second update intervals, but not always possible to realize.
* Calculating the precise beat time, but updating the display every second or every minute. This is often the easy method when doing modifications of existing clock apps or system clock displays. When re-calculating every second, the beat value display will have numeric gaps and jump over a digit in the 0.01 precision = 2nd sub-decimal digit about every 8 to 9 seconds.


## Discussions

* [Discussion on c2wiki](https://wiki.c2.com/?InternetTime)
  * [The Myth of Internet Time by Andrew Odlyzko](http://www.dtc.umn.edu/~odlyzko/doc/internet.time.myth.txt)
* [Fifth World wiki](https://fifthworld.fandom.com/wiki/Swatch_Internet_Time) - [what is a Fifth World country](https://fifthworld.fandom.com/)
* [on TimeAndDate](https://www.timeanddate.com/time/internettime.html)
* [by Sandra](https://portal.mozz.us/gemini/idiomdrottning.org/beat-time) - original at gemini://idiomdrottning.org/beat-time
* [Agora Road Forum](https://forum.agoraroad.com/index.php?threads/motion-for-agora-road-to-adopt-internet-beat-time.6950) - with some implementations and links to various implementations

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
* [beatTAI](https://github.com/B4UDW3RK5/beatTAI) - instead of UTC+1 ("BMT"), uses [International Atomic Time (TAI)](https://en.wikipedia.org/wiki/International_Atomic_Time) which is UTC but monotonic, meaning without any added leap seconds. Format is ":xxx.xx" so just ":" instead of "@", which should combine nicely with ISO 8601 date format like so, "YYYY-MM-DD:xxx.xx". Has implementations in some programming languages and method of calculation for easy reference. Even though the TAI atomic time is the basis of UTC and available at the level of NTP, it is not as easily available in programming languages, compared to UTC.
