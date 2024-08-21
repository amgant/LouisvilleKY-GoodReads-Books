# Louisville Metro Public Library & Popular GoodReads Books 📚🌸

<img src="https://media.architecturaldigest.com/photos/55f9df5a14adf283236d85f4/16:9/w_1280,c_limit/dam-images-architecture-2013-11-libraries-libraries-22-st-florian-monastery.jpg" alt="Beautiful European Library from Architectural Digest"/>

## Objective

The goal of this project is to compare physical book (print books & audiobook cd’s) inventory data of the Louisville Metro (KY) Free Public Library system with GoodReads.com’s print book & audiobook popularity ratings data.
Are there any trends or correlations between the GoodReads popularity of physical books and the Louisville Free Public Library’s inventory?

Some people think public libraries are obsolete because of the rise of ebooks, but the Louisville Metro Free Public Library system is bustling with patrons today, even for physical books. GoodReads is a website with 90 million international users, where readers can share critiques and compile personal lists of books that interest them (it does not sell or publish books). The hope is this project can be used to figure out whether Louisville is well-equipped for the global popular demand for certain books and media.

An assumption is that international GoodReads book/media demand may be similar to Louisville's book/media demand. The GoodReads data provides some potential insight into demand since it only includes the “top” books they’ve got listed on their site. The Louisville Metro Data/Library system does not provide such details to the public about their demand or decision-making process, so there is not much available to make the most educated guess. This exercise will display final visuals that may shed a light on interesting trends or lack thereof.


***How viewers may indulge:***
* **Clone this repo in your Git Bash/Terminal.**
* **Open the virtual environment (it might run best on a Windows computer):**

<ul>

1. Type in your project folder of the terminal `python3 -m venv venv`<br>
2. To open the Virtual Environment (you'll know it's open when you see "(venv)" at the top of your terminal prompt):<br>
For Windows, run in your terminal:<br>
`source venv/Scripts/activate`<br>
If you get an error, try this command:<br>
`venv/Scripts/activate`<br>
If you still get an error, try the below command and then the ones above again:<br>
`Set-ExecutionPolicy Unrestricted -Scope Process`<br>
For Unix or MacOS, run in your terminal:<br>
`venv/bin/activate`<br>
If you get an error, try this command:<br>
`source venv/bin/activate`<br>
If you still get an error, try this command and then the ones above again:<br>
`Set-ExecutionPolicy Unrestricted -Scope Process`<br>

3. Install the required packages. Type `pip install -r requirements.txt`<br>
4. Once you've installed, you might have one module error which is fine. You mainly just want the correct python version. Check the version at play by using the commands `python --version` and `pip -V`. Results should be "Python 3.12.5", and "pip (python 3.12)" consecutively. This is now setup to view the python file.
5. *After* you’ve finished looking at the project, type `deactivate` into your terminal before changing terminal directory to close the virtual environment.

</ul>

* **Check out bookspandas.ipynb for all the Pandas (Python) data cleaning and aggregations. You can Preview it here in Github.**
* **Check out the raw and clean csv files/datasets as you please.**
* **Check out the Outline pdf file attached. The links in it do not work though, you'll have to click on the links from this README/Github page.**
* **View the Tableau visual dashboard.** ***It is best viewed on a computer screen via the .twb file in this repo (if you have the Tableau Public program on your computer). You can also view it with a computer screen via the below link in fullscreen mode. The graphs are interactive, so you can filter to book titles & author names & see what it shows!*** **It is not really compatible with smaller or mobile devices. Unfortunately, the best way to view it on a smaller or mobile device is to view it from the link and click the Desktop Mode icon near the bottom of the page, scroll up to find the Desktop Mode prompt and click OK, & then pan around on each page so you can see & read it all. All other mobile views don't show up the way they should.**
* **See the conclusion in the visual dashboard, but also know that I will keep working on this for fun, and the most updated conclusion will be in this README file in the conclusion section, rather than in the Tableau dashboard.**

<ul>

https://public.tableau.com/app/profile/aliyah.gant/viz/LouisvilleKY-GoodReads-Books-ConclusionTableauDash/1#1 

</ul>


## Methodology

The GoodReads data used is noted on Kaggle as the top book publications from 1/1/1980-12/30/2023 and their current ratings, reviews, and “want to read” count. “Want to read” is a public user feature similar to “liking” on social media, where users can note that they want to read a certain book. The Louisville Metro library inventory data was compiled on 3/1/2024 and it gives basic detail of all items owned by the library system, even if they’re currently being borrowed by library users. All 2024 publications in the library database were removed to allow more closely related time ranges. All electronics and ebooks were filtered out from both datasets.

The raw data used in this program was acquired from Louisville Metro Open Data and Kaggle.com via the below links.
https://data.louisvilleky.gov/datasets/372216992aea4b2cb5b02837d7a48eaf/about
https://www.kaggle.com/datasets/cristaliss/ultimate-book-collection-top-100-books-up-to-2023/data

## Questions
1. How many physical book copies does the Louisville Library system have of the popular physical books on GoodReads?
2. Does the number of editions of a particular book available thru the library correlate significantly to GoodReads popularity?
3. Does the GoodReads book value/price correlate to Louisville Metro library inventory?

## Programming Methodology
1. Reading CSV files in via Pandas(Python) in Jupyter Notebook
2. Cleaning & Combining data via Pandas Merge, and using some DataFrame summaries.
3. Visualizations via Tableau.
4. Virtual environment to ensure compatibility.
5. Annotations via Jupyter Notebooks & README.

## Data Cleaning Goals & Considerations:
* Created a relational database including a Books table, GoodReads Popularity table, & Library Inventory table.
* Added a total library copies column, removing the branch name column.
* Added a total versions/editions column to avoid ambiguity around different publications of the same book, removed duplicates of the same title & author as such.
* Removed other duplicates from both datasets.
* Removed ebooks & electronics from both datasets, to leave only physical books & audiobooks.
* Removed post-2023 publications from the library dataset.
* Removed irrelevant item types such as the library “Laptop”.
* Cleaned up publication dates and author names to match across tables.
* Replaced blanks or invalid values when useful.
* *GoodReads Ratings >= Reviews by count, because users can rate without reviewing. But reviewers must rate.*
* *Raw Library data - Each line is one copy of an item.*
* *Raw GoodReads data - Each line is one recording of data (some duplicates).*

*Raw Louisville Metro Library Data Makeup*
* 1.07MM rows and about 20 columns
* Each line is one copy of an item
* Authors formatted as last name comma first name, some blanks
* Some blank ISBN’s
* Some publication years look invalid (0, 120, 150, 2025) & months or days not provided
* Some blank item collections/genres
* Some items with 0 price, items like “Laptops” with high prices
* No index
* Louisville Open Data/Louisville Metro Government: 
> “Definitions: BibNum - The unique identifier of a bibliographic record within our materials database. Materials with the same bibliographic # will generally have the same cataloging metadata, differing only in the barcode number, assigned location and anything else specific to the individual copy.”
* https://catalog.data.gov/dataset/louisville-metro-ky-library-collection-inventory-5e94f   

*Raw GoodReads Data Makeup*
* 10k rows and about 30 columns
* Some books are listed twice with everything the same except a slight difference in ratings or reviews.
* Some ISBN’s are blank or start with “(ISBN10:“ and are invalid
* Authors formatted as first name then last name
* Some blank “formats”/media types
* Genres are in a “[,]” format with multiple genres per item
* Publication dates are in several different formats, some blanks
* ‘Current Readers’ has some decimals & some blanks
* ‘Want To Read’ has some decimals & some blanks
* Price has some 0’s and some blanks
* Index starts at 0 & is numbered accurately


## Conclusion

***While correlation does not necessarily equal causation, the following are what we can say about these datasets.***

* The Louisville Metro Free Public Library system has atleast 1 copy each of a total of 255 physical published books that are within the 3,752 GoodReads' physical books listings. They also have atleast 1 copy each of a total of 427,203 physical published books that are outside of the GoodReads physical books listing database.

* The strongest significant correlations I found among the two datasets were all between the GoodReads measurements themselves, but there are moderate and weak correlations as well between the two datasets.

*Moderate Correlations:*
* *Sometimes*, physical books that the library holds *more* than 1 Edition of draw in *more* GoodReads users to Rate the physical books out of 5 stars, vs books that the library holds only 1 Edition of.

* *Sometimes*, physical books that the library holds *more* than 1 Edition of have a *larger* quantity of GoodReads user notings of "Want to Read", vs books that the library only holds 1 Edition of.

* *Sometimes*, GoodReads physical book listings with *higher* Ratings out of 5 will have *higher* Numbers of Ratings, Numbers of Reviews, users noting "Want to Read", *and* users noting themselves as a "Current Reader".

*Strong Correlations:*
* We can also say that *more often than not*, if a GoodReads physical book listing has a *high* Number of Ratings, then it also has a *high* Number of Reviews, users clicking the "Current Reader" button, *and* users clicking the "Want To Read" button for that book; **and vice versa** for all of those 4 GoodReads metrics.

*Weak Correlations:*
* There are a few *very weak* correlations among the quantity of physical library book copies, total editions of physical library books within the library system, the GoodReads number of "Current Readers", & their number of "Want to Read"'s.
* There are also some *very weak* correlations between physical book *Price* vs. *GoodReads Ratings out of 5, Number of ratings, and Number of Reviews*. There is almost an **opposite** correlation between *library copies/book edition totals* and the book *Price* vs. *the aforementioned GoodReads ratings* & *Price*.
* I would not consider these weak correlations truly significant, though they're fun to look at on a graph.

##

<ul>

* Things to consider/limits:
* A reminder that I excluded ebooks from both datasets for this project. The raw data used was so large it kept crashing my computer & confusing Python, so I had to save memory somewhere.
* Perhaps GoodReads has a large amount of books that exist as physical books but are *only* listed on their website as ebooks. This could've cut out a lot of what their site was able to give. There were some inaccuracies I noticed in both datasets before clearing them appropriately.
* Perhaps the print books the library has that GoodReads doesn't acknowledge are gems in their own regard. There are American favorites and Louisville favorites that don't do as well internationally & on GoodReads.
* The users of these services are definitely different. These public libraries are typically very much local-community-minded & even have kids go there after school to use the computer & play Roblox before checking out their summer reading books, and young adults using the 3D printer, adults using the printer & checking out current cd's or cassetes. They run programs regularly to inform & uplift Louisville commununities with way more resources than just physical books & audiobooks, even in some ways that don't require folks to have library cards. Anyone can go there & users can get ebooks through the library for free off their website, a few ways they're quite accessible. GoodReads can't be browsed without you creating an account, so if someone doesn't want/have what's needed to create an account (a computer or smart device, an email address or social media account, etc.), they can't benefit from the site at all. So even though it's got an international user base, it's still *(arguably)* more selective in who indulges with the site.
* We may never know if a survey of Louisville library users asking them which books they are currently reading, want to read, and would rate out of 5 stars would look anything like this GoodReads data. Perhaps it's a bit above the library's resources or intent. I am probably more curious now than ever what algorithm or process they use to decide what books to replenish when they go missing or what books to get their first copies of, and what books not to get.

<br>

It's not necessarily a bad thing that there are so few books in common with the datasets, it doesn't mean they're not getting their users what they need! I thought it was cool the libary data was basically the library's online catalogue, just without the info on whether or not items are currently checked out/available/on hold. I will be playing around more with this data/project, as I did not have time to work with SQL like I wanted to. I also have plenty of questions/ideas on what questions this database can answer & I learned Tableau is shockingly very different from Power BI yet they basically have the same capabilities. I'd like to look deeper in to the book price aspect of things, for one. The raw library data has prices that look accurate, for the ebook version and hardcover version of the same books for example, & some of them didn't exactly match GoodReads' price listings. Where does GoodReads get their book price/value data if they don't even sell books?

If anything, this data can be used to show that multi-edition print books/audiobooks at the library are *a bit* likely to have more GoodReads Ratings & GoodReads users who "Want to read"; and separately, if there are a lot of ratings/reviews/"Want to Reads"/"Current Readers" (any 1 of the 4) for a print book per GoodReads, then the rest of the 4 metrics will be high as well, and a slightly weaker correlation for the 5th metric (actual overall GoodReads Rating of the book itself); and if one of those metrics are low, the rest are likely low with the slightly weaker correlation of the overall book Rating. So, I've done what I was set out to do! Feel free to star this project if you'd like to keep tabs!

***Enjoy the interactive graphs & thanks for reading! ~ 🌸***

</ul>
