# Richards-Rich-Playlist
A place for data and tools used to create a playlist from the links dropped in a Twitter post by Richard D Bartlett @rdbartlett

At first I attempting to use Python / Selenium solutions found on Github, but my machine did not have the setup or resources to engage in this crawling, so what follows is a write up of a **no code method of etracting links or specific data from long Twitter threads** - Hope you find it useful and if so fork this and create a write-up.


## Source of data
Thread with many comments with Youtube and Spotify links, but some just being text:

https://twitter.com/RichDecibels/status/1553673739795054592


## ListenBrainz Playlist
https://listenbrainz.org/playlist/95431805-bdd3-4904-bffe-3506c1a09006/

Why ListenBrainz and not just another Youtube plalist? [Because of these reasons](https://listenbrainz.org/about)


## Youtube playlists made by Richard

https://www.youtube.com/watch?v=ZychufQciUY&list=TLGGE-G7ad6M_MowMTA4MjAyMg
https://www.youtube.com/watch?v=IN2iuLK1I3s&list=TLGGXGY-0TlzETYwMTA4MjAyMg
https://www.youtube.com/watch?v=5b3XkCi3jsQ&list=TLGG896wvmgjjUQwMTA4MjAyMg
https://www.youtube.com/watch?v=eJuclG1q2fQ&list=TLGGLPiVNCJH_8gwMTA4MjAyMg


## Raw output of links

[list of youtube links](https://github.com/niclaz/Richards-Rich-Playlist/blob/main/youtube-links-parsed)

[non youtube links and text from thread](https://github.com/niclaz/Richards-Rich-Playlist/blob/main/other-links-and-text)



## Process 1: cloud-based webcrawling [SUCCESSFUL]
 - Registered for a free account with apify.com 
 - Ran the vdrmota tool (aka Actor) within apify
  * 1st run: output was 50 data points of which many are text comments or t.co shortened links
  * 2nd run: different parameters for script, produced same results as 1st run
  * 3rd run: more strict parameters set.... got a similar result as previous runs, about 45-50 data points and all t.co shortened links
  
 - Switching tool, trying to use: zuzka/twitter-url-scraperRuns within Apify... got similar results to above
  * 1st run: re-attempting the zuzka tool with a different protocols (POST) to see if results change.... got 169 data points this time.
  * END of Process - used results of webcrawler to cross compare with Process 2 and get more text (non-url link) contributions.


## Process 2: Electric Boogaloo [COMPLETED]
 - Whilst running the apify webscappers above I also tried to find a way to export a raw HTML file from Twitter to grab the video links out of it
 - Since Youtube shortens the links and has a 'convoluted' source code I opted to try alternative front-ends for Twitter
 - Enter [Nitter](https://github.com/zedeus/nitter), a privacy preserving frontend of Twitter came in useful as it does not do the Twitter link shortening and does not need a login to access
 - Within the preferences of Nitter (in this case the instance at https://nitter.ca) I activated the 'experimental' feature infinite scrolling to produce one page of results for the whole thread and reduced the amount of data on the page (i.e. activating 'hide tweet stats').
 - Then it was only a question of saving the webpage's source code (in this case within Firefox menu, 'save page as' and selecting the the 'web page, HTML only' option)
 - Output produced was parsed using Bash / terminal to only retain html lines that that had "Youtube/Spotify/Soundcloud" within - you could use Python for this as well
 - Some manual cleanup of the < > brackets of HTML from this output and voila. Although in this method no 'text submissions' (song recommendations without a url link) may have been lost in the process... *shrug*
 - Parsed output was compared with the Process 1 output and added to this repo as it's [own file](https://github.com/niclaz/Richards-Rich-Playlist/blob/main/youtube-links-parsed) 


# Gratitude

Thanking / hat-tip to these devs and services used in this process:
- [@rdbartlett](https://github.com/rdbartlett) for letting me play with his data and make the playlist
- [@vdrmota](https://github.com/vdrmota) for the twitter-scraper 'Actor' within [Apify](https://apify.com/vdrmota])
- [@zpelechova](https://github.com/zpelechova) for the twitter-url-scraper 'Actor' within [Apify](https://apify.com/zuzka)
- [@alecsharpie](https://github.com/alecsharpie) for this Twitter url expander hack: requests.get(https://t.co<adfsd>).url
- [@Zedeus](https://github.com/zedeus) for creating such an epic tool as Nitter and people running their own instance of it.
