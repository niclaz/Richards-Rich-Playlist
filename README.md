# Richards-Rich-Playlist
A place for data and tools used to create a playlist from the links dropped in a Twitter post by Richard D Bartlett @rdbartlett


## Source of data
Thread with many comments with Youtube and Spotify links, but some just being text:

https://twitter.com/RichDecibels/status/1553673739795054592


## ListenBrainz Playlist
https://listenbrainz.org/playlist/95431805-bdd3-4904-bffe-3506c1a09006/

Why ListenBrainz and not just another Youtube plalist? [Because of these reasons](https://listenbrainz.org/about)


## Raw output of links

[list of youtube links](https://github.com/niclaz/Richards-Rich-Playlist/blob/main/youtube-links-parsed)

[non youtube links and text from thread](https://github.com/niclaz/Richards-Rich-Playlist/blob/main/other-links-and-text)



## Process 1: cloud-based webcrawling [COMPLETED]
 - Registered for a free account with apify.com 
 - Ran the vdrmota tool (aka Actor) within apify
  * 1st run: output was 50 data points of which many are text comments or t.co shortened links
  * 2nd run: different parameters for script, produced same results as 1st run
  * 3rd run: more strict parameters set.... got a similar result as previous runs, about 45-50 data points and all t.co shortened links
  
 - Switching tool, trying to use: zuzka/twitter-url-scraperRuns within Apify... got similar results to above
  * 1st run: re-attempting the zuzka tool with a different scraping protocols to see if results change.... got 169 data points this time.
  * 2nd run: 
  * END of Process - used to cross compare with Process 2 and get more text (non-url link) contributions.


## Process 2: Electric Boogaloo [COMPLETED]
 - Whilst running the apify scappers above I also tried to export a raw HTML file from Twitter to grab the links out of it
 - Nitter, a privacy preserving frontend of Twitter came in useful as it does not do link shortening
 - Output produced is being parsed and will be added to repo as it's own file: 


# Gratitude

Thanking / hat-tip to these devs and services used in this process:
- [@rdbartlett](https://github.com/rdbartlett) for letting me play with his data and make the playlist
- [@vdrmota](https://github.com/vdrmota) for the twitter-scraper 'Actor' within [Apify](https://apify.com/vdrmota])
- [@zpelechova](https://github.com/zpelechova) for the twitter-url-scraper 'Actor' within [Apify](https://apify.com/zuzka)
- [@alecsharpie](https://github.com/alecsharpie) for this Twitter url expander hack: requests.get(https://t.co<adfsd>).url
