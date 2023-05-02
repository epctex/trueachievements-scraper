# Actor - TrueAchievements Scraper

## TrueAchievements scraper

Since TrueAchievements doesn't provide a good and free API, this actor should help you to retrieve data from it.

The TrueAchievements data scraper supports the following features:

-   Search any keywords - You can search any keyword you would like to have and get the results of game, articles and all comments!

-   Scrape article list pages - Get all articles, comments and all the content.

-   Scrape series detail - Retrieve all games of any series.

-   Scrape games of a publisher - Scrape all the games from specific publisher(s).

-   Scrape XBOX game pass list - Get all the list of games on XBOX game pass.

-   Scrape game list - Scrape full XBOX games list from TrueAchievements.

-   Scrape genres - If you want to get games on a certain category or anything related the genres, just type the url.

-   Scrape game detail - Images, sizes, achievements, developers, genres, publishers and many more information can be retrieved for each game that you'd like to get.

-   Scrape article detail - All content of any article and its comments are ready for you.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/trueachievements-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on TrueAchievements that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on TrueAchievements.

- `startUrls`: (Optional) (Array) List of TrueAchievements URLs. You should only provide news list, search, any listing URL, game detail, article detail, genre detail, publisher detail URLs.

- `includeComments`: (Optional) (Boolean) This will add all the comments that TrueAchievements provides inside the article object. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of comments.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all detail requests. If actor doesn't block very often it'll scrape 100 data points in 2 minutes with ~0.06-0.09 compute units.

### TrueAchievements Scraper Input example

```json
{
  "startUrls":[
    "https://www.trueachievements.com/news?search=game",
    "https://www.trueachievements.com/n52218/way-to-the-woods-game-pass",
    "https://www.trueachievements.com/game/Monster-Energy-Supercross-4",
    "https://www.trueachievements.com/xbox-series",
    "https://www.trueachievements.com/series/Call-of-Duty?distinct=true&dlcsetting=AllDLC",
    "https://www.trueachievements.com/publisher/Electronic-Arts/games",
    "https://www.trueachievements.com/xbox-game-pass/games",
    "https://www.trueachievements.com/games.aspx",
    "https://www.trueachievements.com/genre/Simulation-Racing",
    "https://www.trueachievements.com/searchresults.aspx?search=game"
  ],
  "search":"last",
  "maxItems":20,
  "endPage": 1,
  "includeComments":false,
  "proxy":{
    "useApifyProxy":true
  }
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## TrueAchievements Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this TrueAchievements actor.

## Scraped TrueAchievements Properties

The structure of each item in TrueAchievements looks like this:

### Article Detail

```json
{
	"type": "article",
	"title": "Action-adventure game Way to the Woods comes to Game Pass in March",
	"description": "Another 2023 Xbox Game Pass addition has been confirmed: atmospheric action-adventure game Way to the Woods joins the service early next year.",
	"url": "https://www.trueachievements.com/n52218/way-to-the-woods-game-pass",
	"htmlContent": "<h2 class=\"intro\">Another 2023 Xbox Game Pass addition has been confirmed: atmospheric action-adventure game Way to the Woods joins the service early next year.</h2>As confirmed during Wholesome Snack: The Game Awards Edition, <a href=\"https://www.trueachievements.com/game/Way-to-the-Woods/achievements\">Way to the Woods</a> will come to Xbox Game Pass in March 2023! Check out the trailer below.<br><div class=\"lazyYT\" style=\"padding-bottom:56.25%;\" data-youtube-id=\"wOHBv9MrtAs\" data-ratio=\"16:9\" data-parameters=\"start=581\" data-width=\"700px\"></div><h3>Way to the Woods joins Xbox Game Pass in early 2023</h3>Way to the Woods revolves around a deer and her fawn making their way through what looks to be an abandoned world as they search for home. In our <a href=\"https://www.trueachievements.com/n45333/way-to-the-woods-xbox-game-pass\"> Way to the Woods interview</a>, we spoke to creator Anthony Tan about all aspects of the game; including how its art style takes inspiration from Studio Ghibli films like Spirited Away and Princess Mononoke. <br><br>Way to the Woods looks to be hauntingly beautiful, and it'll be interesting to learn more about its story and world as March 2023 draws nearer. What do you think of Way to the Woods? Happy it's one of the <a href=\"https://www.trueachievements.com/n50708/xbox-game-pass-coming-soon-2022-2023\"> games coming to Game Pass</a>? Let us know in the comments!<script>head.ready(function() { getTimeAgo(); })</script>",
	"textContent": "Another 2023 Xbox Game Pass addition has been confirmed: atmospheric action-adventure game Way to the Woods joins the service early next year.As confirmed during Wholesome Snack: The Game Awards Edition, Way to the Woods will come to Xbox Game Pass in March 2023! Check out the trailer below.Way to the Woods joins Xbox Game Pass in early 2023Way to the Woods revolves around a deer and her fawn making their way through what looks to be an abandoned world as they search for home. In our  Way to the Woods interview, we spoke to creator Anthony Tan about all aspects of the game; including how its art style takes inspiration from Studio Ghibli films like Spirited Away and Princess Mononoke. Way to the Woods looks to be hauntingly beautiful, and it'll be interesting to learn more about its story and world as March 2023 draws nearer. What do you think of Way to the Woods? Happy it's one of the  games coming to Game Pass? Let us know in the comments!head.ready(function() { getTimeAgo(); })",
	"author": {
		"name": "Heidi Nicholas",
		"url": "https://www.trueachievements.com/author/Heidi+Nicholas",
		"bio": "Heidi graduated with an MA in English Literature, and now enjoys writing news, reviews, and features across TrueAchievements and TrueTrophies. When she’s not writing, Heidi is usually either looking for her next RPG, or trying to convince the rest of the team to hear about yet another delightfully wholesome game she has found."
	},
	"comments": [
		{
			"commenter": {
				"name": "Frankie DrumsNY",
				"url": "https://www.trueachievements.com/gamer/Frankie+DrumsNY",
				"avatar": "https://www.trueachievements.com/imagestore/0005050400/5050435.jpg"
			},
			"date": "08 December 22 at 23:29",
			"content": "Hoping they don't pull any punches on this and they go for the hard MA rating. Dismemberment, gratuitous nudity,  cursing & slurs, etc. Might as well go all in."
		},
		{
			"commenter": {
				"name": "thatNoseyParker",
				"url": "https://www.trueachievements.com/gamer/thatNoseyParker",
				"avatar": "https://www.trueachievements.com/imagestore/0003532800/3532856.jpg"
			},
			"date": "09 December 22 at 01:26",
			"content": "Finally! I remember getting excited for this years ago, genuine concern is was silently abandoned"
		},
		{
			"commenter": {
				"name": "MCR182",
				"url": "https://www.trueachievements.com/gamer/MCR182",
				"avatar": "https://www.trueachievements.com/imagestore/0005229200/5229206.jpg"
			},
			"date": "09 December 22 at 01:31",
			"content": "I've been waiting since I saw the first trailer at E3 years ago looks beautiful"
		},
		{
			"commenter": {
				"name": "VjOnItGood81",
				"url": "https://www.trueachievements.com/gamer/VjOnItGood81",
				"avatar": "https://www.trueachievements.com/imagestore/0005716500/5716547.jpg"
			},
			"date": "09 December 22 at 04:29",
			"content": "I'm looking forward to this."
		},
		{
			"commenter": {
				"name": "SnarkLord1980",
				"url": "https://www.trueachievements.com/gamer/SnarkLord1980",
				"avatar": "https://www.trueachievements.com/imagestore/0004842700/4842796.jpg"
			},
			"date": "09 December 22 at 05:46",
			"content": "Sweet. I love new Game Pass announcements."
		}
	]
}
```

### Game Detail

```json
{
	"type": "game",
	"title": "Monster Energy Supercross - The Official Videogame 4",
	"url": "https://www.trueachievements.com/game/Monster-Energy-Supercross-4",
	"publishers": [
		{
			"name": "Milestone",
			"url": "https://www.trueachievements.com/publisher/Milestone"
		}
	],
	"developers": [
		{
			"name": "Milestone",
			"url": "https://www.trueachievements.com/developer/Milestone"
		}
	],
	"release": "11 March 2021",
	"platform": "Xbox Series X|S",
	"genres": [
		"Simulation Racing",
		"Sports",
		"Motocross"
	],
	"features": [
		"Optimized for Series X|S",
		"HDR"
	],
	"notes": [],
	"medium": "Physical and Digital",
	"size": "16.92GB",
	"completionEstimate": "N/A",
	"link": "https://milestone.it/games/monster-energy-supercross-4/",
	"screenshots": [
		"https://ip.trueachievements.com/remote/www.trueachievements.com/customimages/121262.jpg?width=900",
		"https://ip.trueachievements.com/remote/store-images.s-microsoft.com/image/apps.42544.14569410385401135.4de05eee-3e44-4aba-922b-26e29bd33651.99e4f626-4c1c-46df-849a-d8f845f1a570?width=900",
		"https://ip.trueachievements.com/remote/store-images.s-microsoft.com/image/apps.13823.14569410385401135.4de05eee-3e44-4aba-922b-26e29bd33651.b1b464d9-74ae-4807-9b63-89153761abac?width=900",
		"https://ip.trueachievements.com/remote/store-images.s-microsoft.com/image/apps.57903.14569410385401135.4de05eee-3e44-4aba-922b-26e29bd33651.a6998723-5b48-450d-8631-0108d6c1842f?width=900",
		"https://ip.trueachievements.com/remote/store-images.s-microsoft.com/image/apps.17763.14569410385401135.4de05eee-3e44-4aba-922b-26e29bd33651.adb80f60-b2fc-4707-a52a-629858f6add9?width=900",
		"https://ip.trueachievements.com/remote/store-images.s-microsoft.com/image/apps.35976.14569410385401135.4de05eee-3e44-4aba-922b-26e29bd33651.5074e426-8ea7-4b6b-adf4-c7ff9d5ef2bb?width=900",
		"https://ip.trueachievements.com/remote/store-images.s-microsoft.com/image/apps.37807.14569410385401135.4de05eee-3e44-4aba-922b-26e29bd33651.62644b4b-bf13-4a16-a3af-aabcd293f558?width=900",
		"https://ip.trueachievements.com/remote/store-images.s-microsoft.com/image/apps.16341.14569410385401135.4de05eee-3e44-4aba-922b-26e29bd33651.4f4abc54-0f7b-458e-8032-ca6c4a3f0b15?width=900"
	],
	"news": [
		{
			"title": "Golf With Your Friends headlines this weekend's Free Play Days games",
			"url": "https://www.trueachievements.com/n47135/free-play-days-games",
			"image": "https://www.trueachievements.com/customimages/thumbs/103627.jpg"
		}
	],
	"achievements": [
		{
			"title": "Sharing is the key",
			"url": "https://www.trueachievements.com/a319407/sharing-is-the-key-achievement",
			"description": "Complete a Main Event in a Custom Track created by another player",
			"numberOfTrackedGamers": 193,
			"percantage": 11,
			"taRatio": 2.95
		},
		{
			"title": "Now you're one of us!",
			"url": "https://www.trueachievements.com/a319408/now-youre-one-of-us-achievement",
			"description": "Accept the contract of a Team you asked to join",
			"numberOfTrackedGamers": 93,
			"percantage": 6,
			"taRatio": 4.25
		},
		{
			"title": "Who wants to be a Millionaire?",
			"url": "https://www.trueachievements.com/a319409/who-wants-to-be-a-millionaire-achievement",
			"description": "Earn a total of 1,000,000 SX Credits",
			"numberOfTrackedGamers": 228,
			"percantage": 14,
			"taRatio": 2.71
		},
		{
			"title": "The fastest",
			"url": "https://www.trueachievements.com/a319410/the-fastest-achievement",
			"description": "Get a Holeshot in any game mode",
			"numberOfTrackedGamers": 607,
			"percantage": 36,
			"taRatio": 1.66
		},
		{
			"title": "First place 13 times",
			"url": "https://www.trueachievements.com/a319411/first-place-13-times-achievement",
			"description": "Get a total of 13 Holeshots in any game mode",
			"numberOfTrackedGamers": 163,
			"percantage": 10,
			"taRatio": 3.21
		},
		{
			"title": "Brave",
			"url": "https://www.trueachievements.com/a319412/brave-achievement",
			"description": "Win a Main Event with the Event Type option set on \"The Real Thing\"",
			"numberOfTrackedGamers": 146,
			"percantage": 9,
			"taRatio": 3.39
		},
		{
			"title": "Influencer",
			"url": "https://www.trueachievements.com/a319413/influencer-achievement",
			"description": "Purchase a total of 10 components for your Rider Customization",
			"numberOfTrackedGamers": 176,
			"percantage": 10,
			"taRatio": 3.09
		},
		{
			"title": "Young promise of the year",
			"url": "https://www.trueachievements.com/a319414/young-promise-of-the-year-achievement",
			"description": "Complete the Futures chapter in Career Mode",
			"numberOfTrackedGamers": 383,
			"percantage": 23,
			"taRatio": 2.09
		},
		{
			"title": "Ad maiora",
			"url": "https://www.trueachievements.com/a319415/ad-maiora-achievement",
			"description": "Complete the Rookie chapter in Career Mode",
			"numberOfTrackedGamers": 165,
			"percantage": 10,
			"taRatio": 3.19
		},
		{
			"title": "Bread, love and supercross",
			"url": "https://www.trueachievements.com/a319416/bread-love-and-supercross-achievement",
			"description": "Complete the Pro chapter in Career Mode",
			"numberOfTrackedGamers": 111,
			"percantage": 7,
			"taRatio": 3.89
		},
		{
			"title": "Too fast for you",
			"url": "https://www.trueachievements.com/a319417/too-fast-for-you-achievement",
			"description": "Reach the podium in 100 Main Events in any mode",
			"numberOfTrackedGamers": 37,
			"percantage": 2,
			"taRatio": 6.75
		},
		{
			"title": "Novice",
			"url": "https://www.trueachievements.com/a319418/novice-achievement",
			"description": "Reach Prestige level 20",
			"numberOfTrackedGamers": 271,
			"percantage": 16,
			"taRatio": 2.49
		},
		{
			"title": "Professional",
			"url": "https://www.trueachievements.com/a319419/professional-achievement",
			"description": "Reach Prestige level 60",
			"numberOfTrackedGamers": 126,
			"percantage": 7,
			"taRatio": 3.65
		},
		{
			"title": "Legend",
			"url": "https://www.trueachievements.com/a319420/legend-achievement",
			"description": "Reach Prestige level 100",
			"numberOfTrackedGamers": 85,
			"percantage": 5,
			"taRatio": 4.45
		},
		{
			"title": "The future is woman",
			"url": "https://www.trueachievements.com/a319421/the-future-is-woman-achievement",
			"description": "Create a rider with a female body type",
			"numberOfTrackedGamers": 386,
			"percantage": 23,
			"taRatio": 2.08
		},
		{
			"title": "Veteran",
			"url": "https://www.trueachievements.com/a319422/veteran-achievement",
			"description": "Complete all challenges in the Journal",
			"numberOfTrackedGamers": 11,
			"percantage": 1,
			"taRatio": 12.38
		},
		{
			"title": "Promoted",
			"url": "https://www.trueachievements.com/a319423/promoted-achievement",
			"description": "Meet a Contract Objective of an Official Team in Career mode",
			"numberOfTrackedGamers": 80,
			"percantage": 5,
			"taRatio": 4.59
		},
		{
			"title": "The greatest",
			"url": "https://www.trueachievements.com/a319424/the-greatest-achievement",
			"description": "Complete the entire Skill Tree",
			"numberOfTrackedGamers": 54,
			"percantage": 3,
			"taRatio": 5.58
		},
		{
			"title": "Extra-curricular",
			"url": "https://www.trueachievements.com/a319425/extracurricular-achievement",
			"description": "Take part in at least 10 Extra Events",
			"numberOfTrackedGamers": 8,
			"percantage": 0,
			"taRatio": 14.51
		},
		{
			"title": "Full-time Rider",
			"url": "https://www.trueachievements.com/a319426/fulltime-rider-achievement",
			"description": "Create a rider with a male body type",
			"numberOfTrackedGamers": 1,
			"percantage": 96,
			"taRatio": 1.02
		},
		{
			"title": "10 out of 10",
			"url": "https://www.trueachievements.com/a319427/10-out-of-10-achievement",
			"description": "Pass at least 10 Training Sessions with any result",
			"numberOfTrackedGamers": 192,
			"percantage": 11,
			"taRatio": 2.96
		},
		{
			"title": "The Rock",
			"url": "https://www.trueachievements.com/a319428/the-rock-achievement",
			"description": "Complete all the Training Sessions with the maximum result",
			"numberOfTrackedGamers": 21,
			"percantage": 1,
			"taRatio": 8.96
		},
		{
			"title": "Traveler",
			"url": "https://www.trueachievements.com/a319429/traveler-achievement",
			"description": "Ride 100 miles (160 km) in offline Free Roaming in the Compound",
			"numberOfTrackedGamers": 29,
			"percantage": 2,
			"taRatio": 7.62
		},
		{
			"title": "King of Anaheim 1",
			"url": "https://www.trueachievements.com/a319430/king-of-anaheim-1-achievement",
			"description": "Win a Main Event in Anaheim 1 in any game mode",
			"numberOfTrackedGamers": 222,
			"percantage": 13,
			"taRatio": 2.75
		},
		{
			"title": "King of St. Louis",
			"url": "https://www.trueachievements.com/a319431/king-of-st-louis-achievement",
			"description": "Win a Main Event at St. Louis in any game mode",
			"numberOfTrackedGamers": 166,
			"percantage": 10,
			"taRatio": 3.18
		},
		{
			"title": "King of Anaheim 2",
			"url": "https://www.trueachievements.com/a319432/king-of-anaheim-2-achievement",
			"description": "Win a Main Event in Anaheim 2 in any game mode",
			"numberOfTrackedGamers": 170,
			"percantage": 10,
			"taRatio": 3.14
		},
		{
			"title": "King of Glendale",
			"url": "https://www.trueachievements.com/a319433/king-of-glendale-achievement",
			"description": "Win a Main Event in Glendale in any game mode",
			"numberOfTrackedGamers": 148,
			"percantage": 9,
			"taRatio": 3.37
		},
		{
			"title": "King of Oakland",
			"url": "https://www.trueachievements.com/a319434/king-of-oakland-achievement",
			"description": "Win a Main Event in Oakland in any game mode",
			"numberOfTrackedGamers": 219,
			"percantage": 13,
			"taRatio": 2.77
		},
		{
			"title": "King of San Diego",
			"url": "https://www.trueachievements.com/a319435/king-of-san-diego-achievement",
			"description": "Win a Main Event in San Diego in any game mode",
			"numberOfTrackedGamers": 153,
			"percantage": 9,
			"taRatio": 3.31
		},
		{
			"title": "King of Tampa",
			"url": "https://www.trueachievements.com/a319436/king-of-tampa-achievement",
			"description": "Win a Main Event at Tampa in any game mode",
			"numberOfTrackedGamers": 125,
			"percantage": 7,
			"taRatio": 3.67
		},
		{
			"title": "King of Arlington",
			"url": "https://www.trueachievements.com/a319437/king-of-arlington-achievement",
			"description": "Win a Main Event in Arlington in any game mode",
			"numberOfTrackedGamers": 222,
			"percantage": 13,
			"taRatio": 2.75
		},
		{
			"title": "King of Atlanta",
			"url": "https://www.trueachievements.com/a319438/king-of-atlanta-achievement",
			"description": "Win a Main Event in Atlanta in any game mode",
			"numberOfTrackedGamers": 132,
			"percantage": 8,
			"taRatio": 3.57
		},
		{
			"title": "King of Daytona Beach",
			"url": "https://www.trueachievements.com/a319439/king-of-daytona-beach-achievement",
			"description": "Win a Main Event at Salt Lake City R11 in any game mode",
			"numberOfTrackedGamers": 131,
			"percantage": 8,
			"taRatio": 3.58
		},
		{
			"title": "King of Salt Lake City R11",
			"url": "https://www.trueachievements.com/a319440/king-of-salt-lake-city-r11-achievement",
			"description": "Win a Main Event at Salt Lake City R11 in any game mode",
			"numberOfTrackedGamers": 143,
			"percantage": 8,
			"taRatio": 3.43
		},
		{
			"title": "King of Salt Lake City R12",
			"url": "https://www.trueachievements.com/a319441/king-of-salt-lake-city-r12-achievement",
			"description": "Win a Main Event at Salt Lake City R12 in any game mode",
			"numberOfTrackedGamers": 156,
			"percantage": 9,
			"taRatio": 3.28
		},
		{
			"title": "King of Salt Lake City R13",
			"url": "https://www.trueachievements.com/a319442/king-of-salt-lake-city-r13-achievement",
			"description": "Win a Main Event at Salt Lake City R13 in any game mode",
			"numberOfTrackedGamers": 134,
			"percantage": 8,
			"taRatio": 3.54
		},
		{
			"title": "King of Salt Lake City R14",
			"url": "https://www.trueachievements.com/a319443/king-of-salt-lake-city-r14-achievement",
			"description": "Win a Main Event at Salt Lake City R14 in any game mode",
			"numberOfTrackedGamers": 174,
			"percantage": 10,
			"taRatio": 3.11
		},
		{
			"title": "King of Salt Lake City R15",
			"url": "https://www.trueachievements.com/a319444/king-of-salt-lake-city-r15-achievement",
			"description": "Win a Main Event at Salt Lake City R15 in any game mode",
			"numberOfTrackedGamers": 163,
			"percantage": 10,
			"taRatio": 3.21
		},
		{
			"title": "King of Salt Lake City R16",
			"url": "https://www.trueachievements.com/a319445/king-of-salt-lake-city-r16-achievement",
			"description": "Win a Main Event at Salt Lake City R16 in any game mode",
			"numberOfTrackedGamers": 167,
			"percantage": 10,
			"taRatio": 3.17
		},
		{
			"title": "King of Salt Lake City R17",
			"url": "https://www.trueachievements.com/a319446/king-of-salt-lake-city-r17-achievement",
			"description": "Win a Main Event at Salt Lake City R17 in any game mode",
			"numberOfTrackedGamers": 140,
			"percantage": 8,
			"taRatio": 3.47
		},
		{
			"title": "I'll win this time",
			"url": "https://www.trueachievements.com/a319447/ill-win-this-time-achievement",
			"description": "Beat a Rival in Career Mode in any race",
			"numberOfTrackedGamers": 141,
			"percantage": 8,
			"taRatio": 3.45
		},
		{
			"title": "It's easy at the beginning",
			"url": "https://www.trueachievements.com/a319448/its-easy-at-the-beginning-achievement",
			"description": "Complete your first Journal Challenge",
			"numberOfTrackedGamers": 583,
			"percantage": 35,
			"taRatio": 1.7
		},
		{
			"title": "Scrupulous",
			"url": "https://www.trueachievements.com/a319449/scrupulous-achievement",
			"description": "Save a custom Bike Setup",
			"numberOfTrackedGamers": 207,
			"percantage": 12,
			"taRatio": 2.85
		},
		{
			"title": "Fashion Stylist",
			"url": "https://www.trueachievements.com/a319450/fashion-stylist-achievement",
			"description": "Change the color of the nickname on the suit of your custom rider",
			"numberOfTrackedGamers": 352,
			"percantage": 21,
			"taRatio": 2.18
		},
		{
			"title": "Officially champion!",
			"url": "https://www.trueachievements.com/a319451/officially-champion-achievement",
			"description": "Complete an Official Championship of any class in Championship mode",
			"numberOfTrackedGamers": 45,
			"percantage": 3,
			"taRatio": 6.12
		},
		{
			"title": "Double victory",
			"url": "https://www.trueachievements.com/a319452/double-victory-achievement",
			"description": "Get a Holeshot and victory in the same Main Event in any mode",
			"numberOfTrackedGamers": 330,
			"percantage": 20,
			"taRatio": 2.26
		},
		{
			"title": "Master of the Scrubverse",
			"url": "https://www.trueachievements.com/a319453/master-of-the-scrubverse-achievement",
			"description": "Complete a total of at least 100 scrubs",
			"numberOfTrackedGamers": 107,
			"percantage": 6,
			"taRatio": 3.96
		},
		{
			"title": "Who's next?",
			"url": "https://www.trueachievements.com/a319454/whos-next-achievement",
			"description": "Beat the time of the Ghost of another player in Time Attack mode",
			"numberOfTrackedGamers": 98,
			"percantage": 6,
			"taRatio": 4.14
		},
		{
			"title": "Only 2 more to go",
			"url": "https://www.trueachievements.com/a319455/only-2-more-to-go-achievement",
			"description": "Complete at least two SX Challenges of the SX Profile",
			"numberOfTrackedGamers": 57,
			"percantage": 3,
			"taRatio": 5.43
		},
		{
			"title": "Go with the flow",
			"url": "https://www.trueachievements.com/a319456/go-with-the-flow-achievement",
			"description": "Complete a lap with the Dynamic Flow Aid activated",
			"numberOfTrackedGamers": 320,
			"percantage": 19,
			"taRatio": 2.29
		}
	]
}
```
