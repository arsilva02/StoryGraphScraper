# StoryGraphScraper
This scraper is meant to be used with an export from StoryGraph (not a webcrawler, just using your own information). 

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
- [Exporting Your Information](#exporting-your-information)
- [License](#license)


## Features
This scraper will get the following information:
1. Book ID (id utilized by StoryGraph to keep track of every edition of every book)
2. Year book was first published (not by edition)
3. Genres (teal tags on StoryGraph)
4. Moods (pink tags on StoryGraph, also includes pacing)
5. Series (True/False if book is in a series)
6. Series Name (left blank if book is not in a series)
7. Blurb
8. Number of reviews
9. Average star rating
10. Minutes (left blank if not in audio format)
11. Pages (left blank if in audio format)

The scraper will first search by ISBN, if available, then title and author if there is no ISBN. Full features can be found in the StoryGraphScraper.ipnyb file.

## Getting Started

Firstly, make sure you have your information from StoryGraph (the process is [here](#exporting-your-information))

Before you run, make sure you have the code read in where your file is. If you are using Google Colab, you can upload your file. If your file is in a different folder, make sure your path includes the relevant folder. Also make sure your file is the correct name (I renamed my file to storygraphExport in the following example).

```python
df = pd.read_csv('storygraphExport.csv')
```

Scroll to the end of the code. Here, we are pushing our file to be processed. The timeout variable is the amount of time you are willing to let the page load to gather information for each book. The default is 60 seconds, though books usually take much less time than that to load. This may be lowered if you have a truly huge amount of books in your export, though. You can adjust this to any time you want, in seconds.

```python
scraped = sg_scraper(df,timeout=60)
```

Finally, change the name here if you want your download to be saved under a different name (make sure to keep the .csv tag though). If you are utilizing Google Colab, you can download the file through the file manager.

```python
scraped.to_csv('scraped_storygraphExport.csv')
```

After everything is configured correctly to prefrence, you can select "Run All" to generate your new information. Keep in mind this process can be lengthy. My entire dataframe that I used for testing is about 700 entries long, and took about 30 minutes.

## Exporting Your Information
You can get your StoryGraph export in the following steps:
1. (making sure you are logged in) Click on your profile picture at the top of the StoryGraph website
2. Click on "Manage Account"
3. Scroll until you are able to click on "Export StoryGraph Library"
4. Click on "Generate Export"
5. Go to your email when export is done
6. Download your export

Using this .csv file, you can now use the notebook.

## License

This project is licensed under the MIT License.
