# Awesome Swatch Internet Time (.beats) [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A curated list of awesome Swatch Internet Time frameworks, libraries, software and resources.

* TODO more programming languages
* TODO add all the operating systems

Github:
* [topic swatch-internet-time](https://github.com/topics/swatch-internet-time)
* [topic internet-time](https://github.com/topics/internet-time)

Rust:
* [on Github](https://github.com/search?l=Rust&q=internet+time+beat&type=Repositories)
* [beats crate](https://crates.io/crates/beats)

Method of calculation:
* ```now = time in UTC+1``` where Biel is located
* ```beat_time = (now.get_hour() + (now.get_minute() / 60) + now.get_second() / 3600) * 1000 / 24;```
* ```beat_time = now.get_millis_since_midnight() / 86400```
* ... more?

## Applications

Discord:
* [on Github](https://github.com/search?q=internet+time+beat+discord&type=Repositories)

Discussions:
* [Discussion on c2wiki](https://wiki.c2.com/?InternetTime)
  * [The Myth of Internet Time by Andrew Odlyzko](http://www.dtc.umn.edu/~odlyzko/doc/internet.time.myth.txt)
* [Fifth World wiki](https://fifthworld.fandom.com/wiki/Swatch_Internet_Time) -- [what is a Fifth World country](https://fifthworld.fandom.com/)

News articles:
* [ZDnet from 2000](https://www.zdnet.com/article/do-you-have-the-internet-time/), also with sales data (2M devices in first 2 years, time converter downloaded over 5 million times in first 2 years)
* [How stuff works](https://electronics.howstuffworks.com/gadgets/clocks-watches/internet-time.htm)
* [Baltimore Sun article from 1999](http://articles.baltimoresun.com/1999-04-08/news/9904080326_1_swatch-internet-time-keeping-time)
* [Vice 2015](https://www.vice.com/en/article/gyy4bm/remember-when-swatch-invented-a-new-time-system-for-the-internet)
* [academic dict](https://en-academic.com/dic.nsf/enwiki/210738)

Advantage:
* Worldwide synchronized clocks.

Disadvantage:
* Cannot easily deduce if somebody is awake at that time or not. Then again,
  * they don't have to accept the meeting invitation for that time. OTOH, avoid meetings anyway.
  * There is often times an online status function in internet communications platforms and telephone systems these days have a DND function when not available for calls.
* There is UTC.

Limitations:
* The Earth will always go around the sun.

Related:
* [New Earth Time](https://newearthtime.net/) based on 360 degrees per day. So un-decimal.
* Using UTC as basis for Internet Time instead of UTC+1 ("BMT").
* UTC iself.
