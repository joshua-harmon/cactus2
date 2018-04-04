---
author: "Joshua Mangiola"
date: 2018-03-29
linktitle: Simple Python iTunes Playlist Scraper
menu:
  main:
    parent: python
title: Simple Python iTunes Playlist Scraper
description: This is a simple rundown of a script I made that scrapes a iTunes Playlist web link and returns it in CSV form
weight: 10
---
## **Introduction**

This is a simple rundown of a script I recently made that was part of bigger project that is in progress, it scrapes an iTunes playlist page and returns all of the results in CSV which allows for easy processing and filtering. I used the beautifulSoup and requests library for the web scraping that was required and the csv library for exporting.

The full working example of this code available [Here](https://github.com/joshuamangiola/python-itunes-playlist-converter)

## **Scraping the Site - From HTML to an CSV**

Many HTML sites are easily readable with scrapers as they use the same classes for each element which we can take advantage of. The example below is from the iTunes site where it uses the following classes for each element.

![HTML To Scrape](/images/htmlToScrape.png)

With Python, we use requests to fetch the page and then we use BeautifulSoup to find the text within the elements. This quite simple and can be done with the few lines of code below. We then convert that into a new object which is added to an array.

{{< highlight python >}}
playlist_url = "PLAYLIST_URL_GOES_HERE"
page = urlopen(playlist_url)
soup = BeautifulSoup(page, "html.parser")
playlist_title = soup.find("h1", class_="product-header__title").get_text()

track_list = soup.find("ul", class_="tracklist")

soup.find_all('tracklist-item__text__headline')

class playlistItem:
    def __init__(self, title, artist):
        self.title = title
        self.artist = artist

playlist = []

for pi in track_list.select('li.tracklist-item'):
    title = pi.find("span", class_="tracklist-item__text__headline").get_text()[2:-1]
    artist = pi.find("a", class_="table__row__link--inline").get_text()
    playlist.append(playlistItem(title, artist))
{{< /highlight >}}

We then use the Python CSV DictWriter to read the array of the objects and write a row for the title and artist value for each object, this is a integrated python library and is easy to use.

{{< highlight python >}}
with open('output.csv', 'w') as csvfile:
    fieldnames = ['Title', 'Artist']
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)
    writer.writeheader()
    for pi in playlist:
        writer.writerow({'Title': pi.title, 'Artist': pi.artist})
{{< /highlight >}}

The script will then output a csv file that will be formatted like the following file below. That's a simple rundown of how the script and if you have any troubles feel free to comment and I will help out.

Title  |Artist
-------|-----
No Pain (feat. Khalid, Charlie Wilson & Charlotte Day Wilson) | DJDS
Always Be With You | Tom Trago
Miracle | Pional
Hey Sister (feat. The Deep Throat Choir) | Simian Mobile Disco
Somebody | Jim-E Stack
Creep (Take You Home) [Edit] | Mr. Mitch
Emerald Rush | Jon Hopkins
