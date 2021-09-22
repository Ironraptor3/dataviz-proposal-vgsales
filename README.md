# vgsales Visualization Project

## Data
I plan on using this [data](https://gist.github.com/Ironraptor3/34f3938c703111353ee5f28cc9b29d68) for the project.

This data is the sales of various video games in the year range \[1980, 2016].  It originates from [this](https://www.kaggle.com/kedokedokedo/vgsales) link.

A full breakdown of this data is available on the README associated with the linked Github Gist above, but it is also here for convenience:

Attributes:
- Rank: The ranking of the video game sales overall
- Name: The name of the video game.
- Platform: The platform the game was sold under.  This is interesting to show the difference in popularity between platforms.
  I may also want to normalize sales per platform to better compare how successful games were.
- Year: The year the game was released.  Interesting to gauge popular platforms per year, as well as various genres and overall sales
  per year.
- Genre: The official genre of the game.  Interesting because different regions may prefer different genres.  Various genres may
  perform differently across different platforms.  Moreover, various genres may be more or less popular over time.
- Publisher: The publisher of the game.  Could be used to draw similarities about performances of games released under the same
  developer.
- NA_Sales: Sales in North America.  Good to compare total sales, console popularity, and genre popularity.
- EU_Sales: Sales in the European Union.  See NA_Sales.
- JP_Sales: Sales in Japan.  See NA_Sales.
- Other_Sales: Sales not in North America, the European Union, or Japan.  See NA_Sales.
- Global_Sales: Total global sales.  Interesting to compare overall success of a game.

## Questions and Tasks
- Which regions prefer which platform the most for playing video games?
- Which platforms for playing video games have been the most popular each year?
- What is the most popular platform for playing video games?
- Which regions prefer which genre the most?
- Which genres have been more or less popular with the passing of time?
- How do annual video game sales vary per year in each country?
- Which region purchases the most video games?

## Sketches
The following sketch has myriad ideas about the ways to answer the questions and tasks that I have scoped in on.  The first section envisions small multiples which use line graphs to show the sales of each genre/platform over time.  The multiples are broken by the region the sales are happening.  There would be a key present.  Functionality would include the ability to toggle the visibility of various multiples.

The next set of sketches utilize donut charts to display the various genres/platforms distributed at a certain time through each region.  The user could indicate what time to select by hovering their mouse over the previously described set of small multiples.

Finally, perhaps a stacked area graph could be used to show how many sales occured in each of the regions over time.
![dataviz_sketches-1](https://user-images.githubusercontent.com/6307522/134273253-ed9240d0-f6fc-4f0e-a0cf-6b519e92498d.jpg)

The next sketch is more refined, and more recent. The image shows a sketch of the visualization I ultimately made to protoype, and includes some of the functionality.  I use a set of small multiples to display the data, as in the first image.  In later iterations, these multiples will be accompanied by appropriate titles and a key.  The use cases for interaction are written out, and typed here for clarity and ease:

Use Case: Toggle Multiple
Participating Actor: User
Entry Condition: Data is loaded, at least one multiple is on display
Exit Condition: The multiples toggled as visible are rendered
Flow of Events:
- User requests to change the visibility of a multiple
- The system updates the multiple and re-renders all multiples to accomodate the change.

Use Case: Pinpoint Cursor
Participating Actor: User
Entry Condition: Data is loaded, at least one multiple is on display
Exit Condition: 2 lines per multiple have been drawn
Flow of Events:
- User marks the position of the cursor on each rendered multiple
- The system renders marks reflective of the cursor location on all rendered multiples

Use Case: Toggle Data
Participating Actor: User
Entry Condition: Data is loaded
Exit Condition: The data toggled as visible is rendered
Flow of Events:
- User requests to change the visibility of a data label
- The system updates the label and hides or shows marks associated with it.

![dataviz_sketches_2-1](https://user-images.githubusercontent.com/6307522/134273271-a4a12b66-1e2b-4086-a781-2c4fd88ecac2.jpg)

## Prototypes

This is my latest prototype of the visualization:
[![image](https://user-images.githubusercontent.com/6307522/134274649-12f3a7b1-f87a-4795-90dd-f676ae88fbbd.png)](https://vizhub.com/Ironraptor3/af4ff68c075143b89021a0df39be3d70)

Each line graph within this set of small multiples convey information about sales for the various video game genres.  These are plotted against time on the x axis.  The first charge corresponds to global sales, followed by: NA, JP, EU, and Other.  Working functionality includes a crosshair that forms on your cursor on all small multiples.

The next iteration of this prototype hopefully includes:
- A key explaining each of the colors
- Code smell fixes (calculate aggregate data once, more modularity, less magic values)
- Titles at the top of each graph
- The ability to toggle each graph and re-render
- The ability to render different data within the csv
- The ability to toggle various lines/colors
- Zoom and drag (seems to be a native svg function)

All of the information about this prototype, including more detailed information about the code, is included within the VizHub source (You can click the picture).
