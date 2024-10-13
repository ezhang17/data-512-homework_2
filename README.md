# data-512-homework_2
### Purpose
This project analyzes the English Wikipedia article coverage and quality per capita for politicians over different regions and countries. This project also aims to take a look into biases in data and its implications in analysis.

### Licensing
Any Wikipedia content is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

API code is adapted from [page info code example, Revision 1.2 - September 16, 2024](https://drive.google.com/file/d/1iGH_pOMlspeCwDzKCPRlQdq73iS16R6k/view?usp=drive_link) and [ORES code example, Revision 1.0 - August 15, 2023](https://drive.google.com/file/d/1GN1ULxKombHRzVsNKzj7tBhnBrSWUWXc/view?usp=drive_link) developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/).

### Data
Politician data is crawled from [this Wikipeidia category](https://en.wikipedia.org/wiki/Category:Politicians_by_nationality) and stored as a CSV file [here](https://drive.google.com/file/d/1UZ9QUYQ1R2T3Nzau85ToSNkvEzXwLUtf/view?usp=sharing). Population data is from the [world population data sheet](https://www.prb.org/international/indicator/population/table/) published by the Population Reference Bureau and stored as a CSV file [here](https://drive.google.com/file/d/1PlBRdx1t2eSCymXmOqtWXFJPiMn_gTQS/view?usp=sharing). 
Politician data was then cleaned by filtering out keywords (council of, family, president) to keep the dataset to individual politicians. 

Article revision IDs and quality data are retrieved using the following APIs:
Article revision IDs:
Revision IDs are necessary to retrieve quality scores. These IDs are retrieved using the [MediaWiki REST API for the EN Wikipedia](https://www.mediawiki.org/wiki/API:Main_page).

Article ORES scores:
ORES scores are retrieved from the [ORES API](https://wikitech.wikimedia.org/wiki/Machine_Learning/LiftWing).
Quality scores are defined as such:
FA - Featured article
GA - Good article (also known as A-Class)
B - B-Class article
C - C-Class article
Start - Start-class article
Stub - Stub-class article

#### Output Files
The Jupyter Notebook outputs 2 files, wp_countries-no_match.txt and wp_politicians_by_country.csv.

wp_countries-no_match.txt contains the list of countries with no match between the politicians and populations datasets (if the country is present in one dataset and not the other, it will be in this list regardless of source dataset).

wp_politicians_by_country.csv contains the country, region, population, article title, revision id, and article quality data.
Schema:
| Column    | Data Type |
| -------- | ------- |
| country | String | 
| region | String |
| population | Float |
| article_title | String |
| revision_id | Integer |
| article_quality | String |

### Research Implications
Through this project, I learned more about Wikipedia article quality and how bias can shape the outcomes of an analysis. I was surprised to see the lack of data for North American politicians in the politician dataset, considering that this is an English Wikipedia dataset. Because of this missing data, the outcomes of the analyses conducted may not reflect the true distribution of politicians' English Wikipedia pages, but I still think that the outcomes can be used as food for thought and a starting point for further investigation. The analyses showed that European countries had the best coverage and article quality per capita, while African and Asian countries had the worst coverage and quality per capita.

During the process of the project, I noticed that some of the politicians listed were denoted as "Korean", with no mention of North or South. A simple investigation into these articles showed that these politicians were from before the Korean War, before the split into North and South Korea. This poses a couple questions - what time period are these politicians from? And what time period is the population data from? Is this comparison meaningful? I think this would be a good starting point for any further investigation or improvements upon this analysis.

What biases did you expect to find in the data (before you started working with it), and why?

I expected to find more pages for English-speaking countries, namely European and North American countries, since English Wikipedia would mainly be used by English speakers. I also expected more pages for the Western countries due to the nature of politics and the general focus on Western politics on the global scale. There may also be more pages for controversial or notorious politicians with more issues related to them, and likely a better quality rating due to the increased material available.

What (potential) sources of bias did you discover in the course of your data processing and analysis?

In the course of processing the data, I discovered that the original dataset of politicians was already biased - there were no North American politicians and very few politicians for countries like China and Great Britain. I also discovered that the Korean politician list included politicians from before North and South Korea were formed, leading to an inability to map these politicians to a country's population. During analysis, I found that the regions with the most coverage and quality were mainly in Europe, with African and Asian regions having the worst coverage/article quality. This aligns with my original hypothesis about Wikipedia having more coverage for Western regions than others.

What might your results suggest about (English) Wikipedia as a data source?

These results suggest that English Wikipedia is biased towards Western countries. There's more information on Western countries than other regions, so using Wikipedia as a data source may lead to a skewed dataset with less representation of other regions. It can also be noted that English Wikipedia caters to English speaking regions, so it may be better to use another region's Wikipedia (in another language) for that region's data. 

