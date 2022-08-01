# Richards-Rich-Playlist
A place for data and tools used to create a playlist from the links dropped in a Twitter post by Richard D Bartlett @rdbartlett

## Source of data
Thread with many comments with Youtube and Spotify links, but some just being text:
https://twitter.com/RichDecibels/status/1553673739795054592

## ListenBrainz Playlist
https://listenbrainz.org/playlist/95431805-bdd3-4904-bffe-3506c1a09006/
Why ListenBrainz and not just another Youtube plalist? Because: https://listenbrainz.org/about 

## Raw output of links
 <INSERT LINK>



# PROCESS
- Registered for a free account with apify.com
- Used the vdrmota/twitter-scraper hat/tip to @vdrmota
-- his repo of the tool: https://github.com/vdrmota/actor-twitter-scraper

- Ran the tool (aka Actor) within apify
-- 1st run: output was 50 data points of which many are text comments or t.co shortened links
-- 2nd run: different parameters for script, produced same results as 1st run
-- 3rd run: more strict parameters set.... RUNNING NOW



