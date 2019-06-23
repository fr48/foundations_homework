# Billboard: Hot 100 (Scraping to a CSV)

https://www.billboard.com/charts/hot-100

Scrape the fields below, and save as a CSV file.

* Rank
* Artist name
* Song name

This one is pretty simple.

# Goodreads: Science Fiction Books by Female Authors (Scraping to a CSV)

https://www.goodreads.com/list/show/6934.Science_Fiction_Books_by_Female_Authors

Scrape the fields below, and save as a CSV file.

|Field|Example|
|---|---|
|Rank|1|
|Title|The Handmaid's Tale|
|Author|Margaret Atwood|
|Score|score: 30,733|
|Votes|314 people voted|
|Rating|4.09 avg rating — 1,101,120 ratings|

This one is a little tougher, but the main difficulty is in cleaning the data! Clean and separate the scraped data, cleaning up columns and creating new ones like so:

|Before|After|
|---|---|
|A Wrinkle in Time (Time Quintet, #1)|A Wrinkle in Time|
|_Series_|Time Quintet|
|_Number in series_|1|
|score: 30,733|30733|
|4.09 avg rating — 1,101,120 ratings|4.09|
|_Number of ratings_|1101120|

# Epicurious (Pagination, scraping 1x per row)

https://www.epicurious.com/search/cucumbers - or whatever other search term

Remember, we're scraping multiple pages of search results, so the **URL will be different!**

Scrape 10 pages of cucumber search results, and save as a CSV file. Include the following fields:

* Tag/category
* Title
* Summary
* Rating (We'll only want the `2`, not the `2 / 4`)
* Would make again
* Link/URL

**Tip:** You'll need to `try`/`escape` on some of these fields

### Epicurious, Part 2: Once-per-row scraping

Then, open your search results csv, filter for ONLY recipes. Merge the following fields with your original recipes and save as a new CSV file:

* Ingredients
* Directions
* Tags

**Tip:** If you use `.find` for your directions/ingredients, it'll print them all on one line. But if you use `.find_all` to separate them, it makes your life a lot harder! ...unless you just steal this code:

```python
# Get the text from each step individually
# Then join them together with \n between each step
'\n'.join([step.text for step in steps])
```

# Metrolyrics (Pagination, scraping 1x per row)

http://www.metrolyrics.com/rem-lyrics.html (or whatever other musician you'd like!)

Remember, we're scraping multiple pages of search results, so the **URL will be different!**

Scrape all pages of search results for your musician, and save as a CSV file. Include the following fields:

* Song title
* URL
* Popularity
* Year

**Bonus:** Make the popularity a normal number (e.g., `6`)

### Metrolyrics, Part 2: Scrape the lyrics pages

Then, open your search results csv, and scrape the following field:

* Lyrics

Merge with your original song information and save as a new CSV file

**Tip:** If you use `.find` for your lyrics, they'll have a bunch of ads inside! You can use the ingredients/directions trick from above, or you can clean them with regex.

# BONUS: AZLyrics (Scraping 1x per row, getting banned from a website)

> Want to know what it feels like to get banned from scraping? Try this one! If someone else tries it before you, you might be out of luck until you get home. If you scrape too much you'll get banned for a couple days, or you'll need to use a VPN. Feel free to come ask me about it, it's a fun one!

_Unlike MetroLyrics and Epicurious, this is **not multiple pages of search results**._

Scrape the following fields, and save as a CSV file:

* Song title
* Song URL

**Tip:** You might need to clean up the song URL before you save it
https://www.azlyrics.com/r/rem.html

### AZLyrics, Part 2: Fields to scrape

Then, open your search results csv, and scrape the following field:

* Lyrics

Merge with your original song information and save as a new CSV file
