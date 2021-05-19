# The Process

I will describe the process motivating myself to get Metrodroid to work with my CharlieCards.

## Motivation

As [public speaking is overvalued](https://nitter.nixnet.services/nodebotanist/status/972559715380203521#m)<sup>[1](#myfootnote1)</sup> to the point of detriment (and publishing to a somewhat nebulously defined publishing master that most likely does not have _your_ best interests in mind, to some extent), I want to commit myself to the sheer exercise of crystal clear communication as much as possible.

## Variable Precedents Set by MIT and the Proprietary Goody Two Shoes MBTA

MIT is... all over the place when it comes to hacking (as in tinkering and being curious, as defined by "The Hacker Manifesto" by [Loyd Blankenship](https://en.wikipedia.org/wiki/Loyd_Blankenship)).  The MBTA is also naïve for believing in security via obscurity in its CharlieCards and tries to be a proprietary well-behaving goody two shoes, which at best does nothing good for society and at worst actively harms society collectively.  Three cases come to mind (from best to worst):

1.  The first is [_MBTA vs. Anderson_](https://en.wikipedia.org/wiki/Massachusetts_Bay_Transportation_Authority_v._Anderson).  The events regarding this legal case happened between 2007-2008, back when the introduction of the CharlieCard on the MBTA was brand new.  Essentially (without being strictly 100% correct with terminology), four MIT students created a final project on the insecurities of the new CharlieCard and planned on presenting their findings to DEF CON.  However, the MBTA wanted to suppress the proliferation of this information via legal means (i.e., suing) with a temporary restraining order under the Computer Fraud and Abuse Act.  Ironically, a bunch of things happened to manifest the usual Streisand effect, which ended up spreading the findings of the students even faster than if there was no controversy to begin with.  Ultimately, the courts did not grant the MBTA an extension to the restraining order and it is legally safe to research the security of CharlieCards and other similar endeavors for academic purposes... for now.
2.  The second is [Andrew "bunnie" Huang](https://en.wikipedia.org/wiki/Andrew_Huang_(hacker)#Reverse_engineering) for performing the hardware hacking on the original Xbox.  Basically, MIT did not have Huang's back when Microsoft came for Huang - however, Huang's department did.  This happened around 2003.  (Ok, not chronologically in order, though this sort of leads into the last point.)  The year is now 2021, and let us compare the two sides.  On one hand, the Xbox has only gotten worse with DRM and irreparability; Microsoft will not publicly admit it needs hardware tinkerers, such as Ben Heck, to make Xbox controllers more accessible to maximize market reach.  On the other hand, Huang as moved on to [(remotely!) co-write a paper with Edward Snowden](https://www.tjoe.org/pub/direct-radio-introspection/release/2) in 2016 on how to modify iPhone 6 hardware with hardware switches so that it cannot be "remotely hacked" and created a promising hardware production project called [Betrusted](https://betrusted.io/) to produce [Precursor](https://www.crowdsupply.com/sutajio-kosagi/precursor), based on guidelines set by the Introspection Engine in 2016.  Apparently the bottom line is that [no smartphone manufacturer cares about real security for its users](https://nitter.nixnet.services/Snowden/status/1308453045672517633#m)<sup>[2](#myfootnote2)</sup>.  (As you can see, Huang evidently values the flexibility of remote work way before COVID-19 pandemic happened.)
3.  The third and last is [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz).  I feel I do not need to introduce or explain what happened to Swartz, especially if you have made it this far.  If you really need to, then I would highly recommend the biographical documentary on Swartz called _The Internet's Own Boy_, which is completely free to watch and available to watch on YouTube!  (No need to find it through a library, streaming service, or... uh, other economical avenue of finding movies and TV shows.)  Unsurprisingly, Huang supported Swartz after Swartz's death by releasing the Xbox hacking book for free through Free Starch Press (which publishes many hacking-related books).  I think my online life would be considerably worse if I did not not have RSS (which Swartz helped to create when he was 13-14 years old!) through Newsboat and the Creative Commons, to say the least.

### A Pause to Reflect

As you can see from the extremely non-comprehensive selection of cases above, there is not telling whether or not MIT, who some consider the best "technical" college in the US, will respond when it comes to a user's right to exercise the curious hacker's mindset.  Granted, there are crucial subtleties attached to all three cases mentioned above that I did not explore, though that is out of scope here.

## Part 1: The Anecdotal Task at Hand: CharlieCards with Metrodroid in 2019

Additionally, there is no telling whether or not I would get into trouble for writing about making Metrodroid work with CharlieCards.

Potentially - there must be a (legal) reason why Metrodroid does not provide MIFARE keys.  I am not trying to do that.

The MIFARE keys for CharlieCards have already been discovered and pasted around here and there (for various transportation agencies, especially if the agency uses MIFARE cards with nonstandard yet universal keys) in rather disparate locations on the Internet.

Somebody who is much smarter than me and more motivated would have done something "bad" by now with this information if this was even remotely true.

Due to these points, I think I will be ok (I hope).

I have compiled all my mental notes here.  This method could also be potentially used on any other transportation agency using universal nonstandard MIFARE Classic cards.

### How This All Started

Basically, in fall of 2019, I had too much time to browse F-Droid with a smartphone withLineageOS for microG installed.  I may have downloaded Metrodroid during this period of my life, but I did nothing with the app because I could not figure out how to make Metrodroid work out of the box.

I then found [a hacking convention video](https://www.youtube.com/watch?v=gMR-sFufXiE) about MIFARE Classic cards.  When I first started, I was sort of convinced that I truly really needed to "hack" the CharlieCard to get it working with MetroCard.

However, this turned out to be false, once I got to work to get Metrodroid to recognize CharlieCards.

Going to [Metrodroid's GitHub page](https://github.com/metrodroid/metrodroid) lead me to [Metrodroid's Wiki](https://github.com/metrodroid/metrodroid/wiki).  I determined that the CharlieCard was a MIFARE Classic card.  This mean that this is the easiest type of card to get working on Metrodroid.  The odds were in my favor.

I tried reading the [Security Notes](https://github.com/metrodroid/metrodroid/wiki/Security-Notes), but that was not what I needed.

Under the ["Cracking Keys" page](https://github.com/metrodroid/metrodroid/wiki/Cracking-keys), I thought the ["Importing Keys into Metrodroid"](https://github.com/metrodroid/metrodroid/wiki/Cracking-keys#importing-keys-into-metrodroid) would be helpful.  However, this was a ruse I created for myself, since I am not creating new MIFARE card work all by myself.

The subsection that actually lead me in the correct direction was ["Cards that have the same keys on every card"](https://github.com/metrodroid/metrodroid/wiki/Cracking-keys#cards-that-have-the-same-keys-on-every-card), which was under "MIFARE Classic" > "Key usage by transit card".  This told me that CharlieCards had universal yet unique/nonstandard MIFARE Classic keys.

I needed to find these MIFARE Classic keys somehow.

I took a detour by watching [this video](https://www.youtube.com/watch?v=qumhrXobI9A), which demonstrated some sort of brute force technique with a HTC One M8.  (The phone could be the HTC One M7, but I am going to trust my instincts from the time when I recognized new phones better than I do now.)

Excited by reading about the app used in the video, I downloaded the [Mifare Classic Tool](https://github.com/ikarus23/MifareClassicTool) (which I will come back to and discuss later), but was disappointed when the version of the app from F-Droid could not actually brute force key searches.  I should have been more keen on the video's comments, since [a comment indicated that finding nontrivial keys via brute force was futile](https://www.youtube.com/watch?v=qumhrXobI9A&lc=UgjqYyv5KPVSaXgCoAEC.8B0jxZwZAGs8BAZQA-16tN) and would take way too long to perform via a smartphone.

I was going to give up, since I thought at the moment I would have to buy MIFARE Classic card scanning hardware.

However, I had simply failed to comprehend what was already present in the Metrodroid Wiki for CharlieCards.

If we go directly to [the CharlieCard page](https://github.com/metrodroid/metrodroid/wiki/CharlieCard), we can see that we need (up to) 16 sets of A/B key pairs, because there are 16 sectors on CharlieCards.  (This has something to do with MIFARE Classic cards using and storing hexadecimal values on an extremely low-level detail overview.)  This detail comes up later, though I should have paid closer to the last section of the page named "Keys", which states:

> All CharlieCards appear to use the same keys. All the keys that are used appear in some "well known key lists".

CharlieCards are listed under ["Reasonably well supported cards"](https://github.com/metrodroid/metrodroid/wiki/checklists), except for subscriptions - I have no idea what that means.  I believe one can register a CharlieCard and refill it with money via a credit or debit card on the MBTA's website, though I do not know if this is what "subscriptions" mean.  (There should be an open source mobile client to do this, though pragmatically that might be asking for too much, since developing and maintaining Metrodroid is difficult.)

I took another detour, thinking I might be able to pick up something from technical specifications for MIFARE Classic cards by going to the [webpage for MIFARE Classic cards](https://www.mifare.net/en/products/chip-card-ics/mifare-classic/).

Other than what is already known (i.e. [a 2015 security notice from NXP](https://www.mifare.net/en/products/chip-card-ics/mifare-classic/security-statement-on-crypto1-implementations/), the creator of MIFARE Classic cards, stating that MIFARE Classic keys should no longer be implemented in high security scenarios), I read through [a MIFARE Classic marketing leaflet](https://www.mifare.net/wp-content/uploads/2018/10/MIFARE-Classic-EV1-Leaflet-web-102018.pdf) and [an extremely obtuse technical specification](https://www.nxp.com/docs/en/data-sheet/MF1S70YYX_V1.pdf) that was clearly written for electrical engineers or computer engineers than a normal reader.

It is 2021, 7 years after this security notice came out.  I am inferring the MBTA is indicating to its riders that they do not need high levels of security.  Ok.  (Oh, do not even consider trying to use the newer, more "secure" MIFARE cards - that will only dig yourself into the "security via obscurity" pit of darkness.  The lead developer of Metrodroid, Michael Farrell, gave a talk about Metrodroid in 2018 called, ["Tap On to Reverse Engineering"](https://www.youtube.com/watch?v=qVvNdfKRw7M) - do not do Farrell dirty by ignoring what he says in his talk.)

Anyways, in the past, I simply "tried" using Metrodroid.  However, (disregarding the fact that the CharlieCard was not fully supported at the time but would work if the encryption keys were found,) I come across the otherwise expected error in Metrodroid of not being able to read the card due to the lack of keys.  Ok, I thought this would happen.  Looks like I will really need to find those encryption keys.  (Oh yes, this assume that I have already installed Metrodroid on my OnePlus One.  I vaguely recall Metrodroid claiming my phone could not support reading from Metrodroid, but this turned out to be false.)

Next, I download and launch the MIFARE Classic Tool (MCT), which says [MCT is not capable of brute force attacks](https://github.com/ikarus23/MifareClassicTool#general-information), confirming what was discussed in the YouTube comments of the video from earlier.  Almost by accident, I simply poke around this app to discover and deduce that this app has many well-known encryption keys preloaded in the app due to what happens next.  With NFC turned on, I simply scan a CharlieCard (any CharlieCard, since all use the same set of encryption keys).  Once MCT recognizes with a little temporary dialogue box at the bottom of the screen, I tap the "READ TAG" button in the app.  Then, I let MCT on the phone try all preloaded keys while reading the CharlieCard.

This takes a while (on the order of 10 minutes).  However, once I was done, I realized that I had a CharlieCard dump.  I saved the dump to the app internally (since that is what the first "save" option you see does, not externally save to the phone's storage system so that the file explorer can display the file) and then went to "EDIT/ANALYZE DUMP FILE" in MCT.  In this part of the app, you may now save the dump file with any filename you want by going to the three dots menu > "Export Dump" ? ".mct (MIFARE Classic Tool)".

Now, to make this part of forming a JSON file that Metrodroid will accept, I should have used a flash drive with USB-A ("normal" USB) and micro USB (or USB-C).  However, using the data cable that came with your phone and enabling "File Transfer" on your Android device should suffice.

I then brought the `.mct` file onto a computer.  (You could use a text editor on your Android device - however, unless you have a swanky Android setup already, such as the physical keyboard cover accessory for the Samsung Galaxy Tab S5e, trying to use a text editor will always be less convenient than using a proper laptop or desktop computer.)  Out of all of the file formats accepted by Metrodroid, I found [static JSON file type](https://github.com/metrodroid/metrodroid/wiki/Importing-MIFARE-Classic-keys#static-json) to be easiest (since it worked for me in the end).  I do not recall if I had trouble with the other two accepted file formats or what.

After cheesing my way with `gedit`, I finally saved the file and brought it back to my Android phone.  After selecting the keys I wanted to import into Metrodroid, I finally had the CharlieCard working on Metrodroid!

I had accomplished this with the OnePlus One (codenamed `bacon`, for those from the LineageOS part of the Android custom ROM world) and the OnePlus 3T (codenamed`oneplus3`) at the end of October 2019.  If I recall correctly, the OnePlus 3T was slightly faster while doing NFC reading processes.  However, I do not recall the OnePlus One taking _that_ much longer than the OnePlus 3T - perhaps 30 seconds to 1 minute longer.  This is certainly not a dealbreaker by any means - it is not like NFC experienced a quantum leap in performance from the 2014 to 2016, the years the OnePlus One and OnePLus 3T were released, respectively.

Feeling accomplished, I wrote some half-baked notes for myself on my old laptop.  Since then, I had only transfered the decrypted raw dump and CharlieCard key file to my current laptop.  At some point in 2020, I lost my original writeup (due to making an extremely arrogant mistake by removing the keyloop folder or something on my old Ubuntu laptop - note to self: you would rather do backups in a way that is so "stupid" it cannot fail, rather than risk loosing everything by trying to make backups in a way that is way "smarter" that no one asked for).

## Part 2: Return to Metrodroid in 2021

I had initially wanted to post what I discovered back in late 2019.  However, I did not want to log into GitHub many times, over and over again, and I did not yet know how to use SSH keys to use Git to push changes onto the repository I am working on (once set up) without logging into GitHub.

Fast forward to 2021.  I have started to upload my work onto GitHub so that I would not risk losing my only copies of my work sort of related to coding.  (As is said in library science, having only one copy of a valuable work is never a good situation - remember what happened to the Library of Alexandria?)

The COVID-19 pandemic has made the world worse with regards to privacy, security, and anonymity.  (I hope I do not have to explain this.)

Ironically, I have not used public transportation since the pandemic started.  (Fortunately, this has given enough time for the lovely folks working on Metrodroid to work out some systemic F-Droid build kink that prevented the F-Droid release of Metrodroid to fall behind the one released on the Google Play Store.)

However, this got me thinking about how some people would like to make as few trips to MBTA stations as possible - even before the pandemic started.  That was one of the reasons why I got involved with Metrodroid in the first place - I saw a practical use case it could offer me.

Friends keep telling me to not take public transportation again in a only partially joking manner - though there may be people out there who do not have the luxury or privilege of choice when it comes to transportation.

Moreover, there is a huge learning gap between discovering Metrodroid and getting a CharlieCard to work with Metrodroid.

So, in the spirit of reproducible results (both in science and reproducible builds in dev ops), I tried to follow my mental tracks with getting CharlieCard to work with Metrodroid again in 2021.

Surprisingly, my OnePlus One and OnePlus 3T had NFC that was wonky and failed to stay "on"/"activated" with LineageOS 18.1.  This is because Metrodroid kept asking for me to turn on the NFC on the OnePlus One and MCT never activated (even though the NFC was consistently activated), while the NFC status kept flickering on the OnePlus 3T and MCT stated that the CharlieCard could not be read (despite giving the correct information that the card was a MIFARE Classic 1K card).  (Though I will have to do a lot of sorting out the situation before I file an issue in MCT... yet [both devices are supposed to be compatible with MCT](https://github.com/ikarus23/MifareClassicTool/blob/master/COMPATIBLE_DEVICES.md) - not sure if this is a LOS issue with those two devices or strictly a MCT issue.)

Fortunately, I had the OnePlus 5T (codenamed `dumpling`) and NFC, MCT, and Metrodroid worked perfectly fine.

In MCT, the OnePlus 5T needs about 8 minutes to scan 1,081 preloaded keys in MCT.  MCT is able to find the 21 unique keys required to decrypt the CharlieCard and obtain a raw dump of the CharlieCard.  Once the 21 keys have been identified, MCT takes about 10-15 seconds to obtain the same raw dump of any CharlieCard.

This reminds me - you will want to export the dump and _not_ the keys from MCT, since Metrodroid cannot accept the file format that the keys are exported in MCT verbatim and the key export will not indicate which key should be used for either the A or B portion in each of the 16 sectors of the MIFARE Classic card.  The exported key file in MCT will indicate how many unique encryption keys there are, though.  Besides, taking into the account that there are A and B keys, the worst case scenario in which Metrodroid attempts to use a list of 21 unsorted keys (assuming Metrodroid can accept unsorted keys) in 32 A/B positions is 21 × 32 = 441 total position attempts.  That is much longer than specifying 32 exact positions of which of the 21 keys are supposed to be arranged to fully decrypt the A/B areas of 16 sectors in order and in one go (1 × 32 = 32).

Use Caffeine on LOS to keep the screen open to any saved dump on MCT next to your computer so that you know what text to delete and what text to keep to help yourself prep the static JSON for Metrodroid.

After editing the raw dump into a static JSON file, Metrodroid takes less than one second to fully unlock any CharlieCard.

(What is awesome is that now Metrodroid saves all available data each time you scan the card!)

Here is what currently works for CharlieCards in Metrodroid (May 2021):

* validity date range (though they do not correspond to correct dates I wrote down on accompanying sticky notes - also do not know if Metrodroid gets confused with "Keep Active" dates versus "Expiration Dates")
* (some) expiration dates (I guess - again, sometimes it is accurate and sometimes it is not)
* card balance
* dates and times of each time card was used (not sure if this includes tapping CharlieCards on kiosks), but every price amount is preset to $0.00 and feature "Unknown" labels and hexadecimal values of the form 0xNNN, where N is a hexadecimal digit
* what seems to be the last 10 trips, stored locally (I am sure the MBTA can bring up more trips and a complete data log for any CharlieCard, if law enforcement or TLA, such as the FBI, ever demanded information about a certain CharlieCard, since every card should be recorded according to the back room service)

Here is what does not work at all for CharlieCards in Metrodroid (May 2021):

* Names of locations/stops or bus routes taken for each transaction (I know this should somewhat work, because I remember seeing MBTA employees helping me with CharlieCards before and their administrative portal shows the name of every subway stop or bus you have taken - though I am not sure how far back that history goes on a CharlieCard kiosk, perhaps just 10)

### Verbose Explanation of How to Position CharlieCards with NFC Chips on Phones

Lastly, the experience of using the CharlieCard with Metrodroid or MCT will be greatly improved if you know the general NFC contact area on both the CharlieCard and on your Android phone, so that NFC scanning will not be disrupt the connection by accident.  Remember that your phone's effective NFC transit/receive area is neither as strong or as large as the CharlieCard scanners at MBTA stations, buses, or kiosks.

The NFC chip on the CharlieCard is located in the lower right corner, if the front of the card is upright and facing you - sort of like an NFC "hot spot" (or "hot corner").  (The rectangular indentation of the NFC chip in CharlieCards, due to manufacturer irregularities, is much easier to inspect on older CharlieCards obtained during the years of 2009-2012.  On a well-made CharlieCard today that is not made via an instant CharlieCard printer that prints out a card in front of you in one minute, it is either nearly impossible to see this indent with the naked eye or it has been eliminated altogether.)

The NFC receiver/transmitter is typically located behind the camera of Android smartphones, since this part of the smartphone is made of glass that allows NFC transmission to pass through on phones with aluminum unibodies.  This is true on the OnePlus One, OnePlus 3T ,and OnePlus 5T.  (Plastic is not really making a comeback in 2021, though glass phones are - for newer glass phones, the NFC chip may not be behind the camera anymore.  Instead, always make sure to look up on your favorite search engine where the NFC chip is located on your specific phone model.  Do **not** get me started on forced obsolescence trends in consumer smartphones vs. right to repair... though that is out of scope for this topic.)

For best results, place the CharlieCard on a flat surface, such as a table.  Next, place the phone on top of the CharlieCard so that the phone's camera is on top of the CharlieCard's hot spot (or hot corner).

This way ensures that the NFC connection from your phone to the CharlieCard is optimal and prevents any disconnection interruptions, which causes you to restart from square one in both MCT and in Metrodroid.

### Most Important Take-away Points

Based on my work here, this means if one had a laptop, a USB data cable, and an Android phone (which has properly functioning NFC) with Metrodroid and MIFARE Classic Tool installed; then one can get Metrodroid to work with the CharlieCard without ever requiring Internet access in about 15-20 minutes when starting from scratch.  (Personally, I would take at least 30-40 minutes from scratch.)

No searching for the MBTA CharlieCard MIFARE Classic keys on Pastebin or whatever.  (Actually, I used to have, but it seems I have either lost this bookmark or the Pastebin post has vanished for whatever reason.  I am surmising that if you knew the correct people in MIFARE card "hacking", then you can get the keys for CharlieCard easily - if it is not already posted publically online somewhere.)

Metrodroid is a good method to locally determine without network access if you have any money left on any CharlieCard - expired or inactive cards are automatically "locked out" and any kiosk refuses to display any information when you tap your CharlieCard on the kiosks.  So, ordinarily you must go to the CharlieCard Store in Downtown Crossing in order to determine whether or not there is any balance left on an inactive/expired CharlieCard.  (I have heard hearsay that it is possible to retrieve remaining balances on inactive/expired CharlieCards - however, I have never attempted this, so I cannot say whether or not that is true.)  That way (once the pandemic is over-ish), you can tell whether or not a CharlieCard you have lying around is worth taking it all the way to the CharlieCard Store to get your money's worth.

I hope this verbose mind dump will be remotely interesting to someone out there and/or at least helpful with describing the discovery process I had to go through to get Metrodroid app to scan CharlieCards.  At the very least, I hope this will help those out there who want to use Metrodroid app with a CharlieCard but would have normally given up if they saw and balked at the task of obtaining the CharlieCard encryption keys.

### Concluding Remarks

I will have to consult other IRL programming friends to make sure whether or not I would be ok if I posted the CharlieCard keys here on GitHub.  To err on the side of caution, I will not (at least until I have been cleared on this by people who are way smarter than me, especially on topics such as this) - however, the procedure I described above will always work, regardless of whether or not the keys are posted in a rather prominently public place on the Internet.

I had just never seen the method described anywhere on the (public) clearnet.

Additionally, once you have created a static JSON key file for CharlieCards, you only need to load the key file onto any Android phone and import the keys into Metrodroid to get the app to work with CharlieCards.  So, make sure to back up the MIFARE Classic keys for CharlieCards so you do not have to mess around with the MCT dump file again.

Lastly, this little "project" shows the power of "no tech" hacking.  I did not even need to buy Proxmark3 hardware or whatever is used for NFC card hacking to "crack" the CharlieCard.

However, this exercise was very time, energy, and focus consuming.  I have high regard to anyone who dabbles in actual brute force cracking of these MIFARE brand NFC cards.  This stuff is so hard!

At some point, I thought I could be a "hardware hacker", but I think I will chill out with such aspirations after this project.  Reading MIFARE Classic technical specifications was not fun and was most certainly almost a complete waste of paper and printing supplies.

### Hope for the Future

There are so many aspects of the MBTA we cannot control.  To name a few in a noncomprehensive list:

* "New" electronic LCD signs atthat give more time to horrible ads than bus time arrivals (which can be a dealbreaker when trying to catch a subway train after getting off a bus),
* quite a few e-ink screens that show MBTA bus arrivals but are located _nowhere_ near an actual bus stop where people would need such signs,
* rising MBTA fares with no increase of services in general (do not get me into the "debt" the MBTA has - there must be some sort of Massachusetts-centric Deus Group controlling the MBTA via puppet strings, as if this was _Mr. Robot_ - we know about the privatization of the MBTA),
* the availability of CharlieCards becoming exclusively available at centralized subway stations (when they used to be placed on top of every MBTA kiosk in every subway station for free before 2010),
* MBTA public hearings strategically placed in the weirdest places in Massachusetts in order to make access to these hearings as difficult as possible,
* the new Orange Line cars having "minor" derailings - even though these are supposed to be generally "brand new" subway cars,
* and many other points that could be put on here, but are most likely wasted as angry grumbling tweets and effectively lost in the black hole of Twitter/commercialized ad-centric social media sites.

Inspired by `trackthet.com` (which seems to be defunct now in May 2021) and acknowledging that the MBTA has public APIs that app developers can access - maybe that the way to determine what the MBTA stops at subway stations or bus routes can be extracted from in Metrodroid?

I do not know, though as governments and institutions begin to be more and more overtly and overbearing proprietary (and proprietary software can only become monotonically worse over time), open source

## Acknowledgements

* Johnny Long, who gave the ["No-Tech Hacking"](https://www.youtube.com/watch?v=N4kfsxF8Tio) in 2007 at DEF CON 15 - that's where I use the "no tech" hacking principle (though my hacking does involve some typing, it still requires no actual scripting work and can be followed mechanically)
* th3ph3d, who gave the [Cracking Mifare Classic the Easy (and Cheap) Way](https://www.youtube.com/watch?v=gMR-sFufXiE) talk at DC801 in 2018 and got me interested in and set me on my way to get CharlieCards to work on Metrodroid
* Metrodroid, the front and center app that made this "little" project even possible in the first place
* MIFARE Classic Tool, the behind the scenes MVP or invisible hero of this project that makes it possible to retrieve CharlieCards 100% offline (once installed on your Android phone, of course)
* @phcoder (Vladimir Serbinenko), for bringing CharlieCard support to the Metrodroid app
* F-Droid and LineageOS for microG - if F-Droid was never included in LOS for microG, then I would never have the chance to be exposed to Metrodroid and MCT
* Last, but not least: Privacy Tools IO, which mentions LOS for microG - if it were not for the [alternative Android OS section](https://www.privacytools.io/operating-systems/#aosp_os), then I would still be stuck on LOS with the Google Play Store draining the life out of my battery whenever GSF feels like crashing my battery percentage to 0% while making my phone insanely hot for no good reason (because, proprietary software)

## Disclaimer

I am not affiliated with anyone or getting promoted or paid to do any of this.  I am not related to Metrodroid, MIFARE Classic Tool, or the MBTA.

I am merely stringing together information that is already publicly available though disparately scattered across the internet.

(I am also just putting this information on GitHub because I would like very much to prevent myself from losing my data of small personal projects (that I barely wrote any documentation for) anymore.)

## Footnotes

<a name="myfootnote1">1</a>: You can find [this on the Wayback Machine](https://web.archive.org/web/20210516182407/https://nitter.nixnet.services/nodebotanist/status/972559715380203521), if that Nitter instance is rate limited.

<a name="myfootnote2">2</a>: Again, [this is on the Wayback Machine](https://web.archive.org/web/20210516193138/https://nitter.nixnet.services/Snowden/status/1308453045672517633), if that Nitter instance is rate limited.