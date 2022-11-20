## How do I use it?

1. Install Hugo (on a Mac: `brew install hugo`)
1. [Download your Twitter archive](https://twitter.com/settings/download_your_data) (Settings > Your account > Download an archive of your data).
1. Place the unzipped files in the 'input' folder.
1. Run `python3 parser.py`. This will generate your twitter archive in the `output/content` folder.
1. Edit `output/config.toml`. Mosty just change the `baseURL` to the site you plan to use for your twitter archive.
1. `cd output`, then run `hugo`

Your twitter archive will be generated as a set of static HTML files in the `output/public` folder; you can upload these to any web host. [Example output](https://twitter.joeycastillo.com).

**WARNING: This script includes your Twitter Circle tweets in the public archive.** They aren't noted in any special way. This is a legacy behavior from the upstream that I didn't have time to fix. Also unlike the upstream script, this one does not parse accounts you follow, folllowers or DMs. This is just for the public timeline (and of course circle tweets as mentioned above).

If you are having problems, [ping me on Mastodon](https://mastodon.social/@joeycastillo); I forked this and threw the changes together in 48 hours for my own archive, so it wouldn't stun me if an issue comes up.

# Upstream Readme

The Twitter archive gives you a bunch of data and an HTML file (`Your archive.html`). Open that file to take a look! It lets you view your tweets in a nice interface. It has some flaws but maybe that's all you need. If so then stop here, you don't need our script.

Flaws of the Twitter archive:
- It shows you tweets you posted with images, but if you click on one of the images to expand it then it takes you to the Twitter website. If you are offline or have deleted your account or twitter.com is down then that won't work.
- The tweets are stored in a complex JSON structure so you can't just copy them into your blog for example.
- The images they give you are smaller than the ones you uploaded. I don't know why they would do this to us.
- The links are all obfuscated in a short form using t.co, which hides their origin and redirects traffic to Twitter, giving them analytics. Also they will stop working if t.co goes down.

Our script does the following:
- Converts the tweets to [markdown](https://en.wikipedia.org/wiki/Markdown) and also HTML, with embedded images, videos and links.
- Replaces t.co URLs with their original versions.
- Copies used images to an output folder, to allow them to be moved to a new home.
- Afterwards, it asks if you want to try downloading the original size images.


## Related tools:

If our script doesn't do what you want then maybe a different tool will help:
- https://github.com/selfawaresoup/twitter-tools
- https://github.com/roobottom/twitter-archive-to-markdown-files
- https://gist.github.com/divyajyotiuk/9fb29c046e1dfcc8d5683684d7068efe#file-get_twitter_bookmarks_v3-py
- https://archive.alt-text.org/
- https://observablehq.com/@enjalot/twitter-archive-tweets
- https://github.com/woluxwolu/twint
- https://github.com/jarulsamy/Twitter-Archive
- https://sk22.github.io/twitter-archive-browser/
- https://pypi.org/project/pleroma-bot/
- https://github.com/mshea/Parse-Twitter-Archive
- https://github.com/dangoldin/twitter-archive-analysis
- https://fedi.doom.solutions/tumelune/
