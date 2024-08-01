# CharlieCard on Metrodroid

Here are my scattered notes on how I got the [Metrodroid](https://www.metrodroid.org/metrodroid/)
app to work on my Android phones.

I've personally confirmed the following phones work on GrapheneOS:
* [Pixel 4a](https://en.wikipedia.org/wiki/Pixel_4a)
* [Pixel 5a](https://en.wikipedia.org/wiki/Pixel_5a)
* [Pixel 6a](https://en.wikipedia.org/wiki/Pixel_6a)

## Notes

According to this 2023 hardwear&period;io '"Un-fare Advantage” - Hacking The
MBTA CharlieCard From 2008 To Present' [talk](https://www.youtube.com/watch?v=me6FyrDRlD4)
by Bobby Rauch, the MIFARE Classic keys for CharlieCards are included on the
lists of well-known keys on [Flipper Zero](https://en.wikipedia.org/wiki/Flipper_Zero)
devices with the latest firmware.

As mentioned on the Security Notes [page](https://github.com/metrodroid/metrodroid/wiki/Security-Notes)
of the Metrodroid wiki, the MBTA really should allow ways for its customers to
view the current balance of CharlieCards in an offline manner along with fixing
fundamental issues with its ticketing system, instead of relying on on a system
design entirely dependent on
[security through obscurity](https://en.wikipedia.org/wiki/Security_through_obscurity).

## License

(Probably GPLv3, though I may change to some form of Creative Commons if I need to)

