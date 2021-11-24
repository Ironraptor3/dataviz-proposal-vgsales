# vgsales Visualization Project

## Data
I plan on using this [data for video game sales](https://gist.github.com/Ironraptor3/34f3938c703111353ee5f28cc9b29d68) for the project.

This data is the sales of various video games in the year range \[1980, 2016].  It originates from [this](https://www.kaggle.com/kedokedokedo/vgsales) link.  Video games interest me because in my undergraduate degree, I was a Computer Science and IMGD double major.

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

### Scatter plot

This was my first rendering of the data being used in this project.  It takes the form of a very basic scatter plot with years plotted against various video game sales.  The circles are transparent to make overplotting more obvious.

[![image](https://user-images.githubusercontent.com/6307522/137227363-7fe5e5ad-6bc7-4ac0-8efa-85a462d2884f.png)](https://vizhub.com/Ironraptor3/ccdcdc9969ca4697b59e6457db7dbf30)


### Initial

This is my first prototype of the visualization:
[![image](https://user-images.githubusercontent.com/6307522/134274649-12f3a7b1-f87a-4795-90dd-f676ae88fbbd.png)](https://vizhub.com/Ironraptor3/af4ff68c075143b89021a0df39be3d70)

Each line graph within this set of small multiples convey information about sales for the various video game genres.  These are plotted against time on the x axis.  The first charge corresponds to global sales, followed by: NA, JP, EU, and Other.  Working functionality includes a crosshair that forms on your cursor on all small multiples.

Lines appear on click to give the user a guide to better compare values.  These guide lines likewise appear on all small multiples simultaneously.

### First Iteration

The next iteration looked like this: [![image](https://user-images.githubusercontent.com/6307522/137227461-8980f600-099a-49d0-9073-6c41875ac84c.png)](https://vizhub.com/Ironraptor3/763afd26abd24fe694f6a14c30d0d71c)

This improved version of the original prototype now has a key and titles above the various small multiples to explain which data each visualizes.  The key also comes with a higlighting feature: users hovering over an item will cause it to have a much thicker line, becoming more noticable.

Clicking on an item in the key causes the line to disappear/reappear, to allow users to compare specific lines.

On the technical side, many comments were added to the code, and many magic values were placed in constants.  Data aggregation (an expensive process) is now only performed once when the data is first loaded.


### Second Iteration

This is the next iteration: [![image](https://user-images.githubusercontent.com/6307522/137227684-2655cb59-10c5-4478-87e2-b3a2fa1d5b38.png)](https://vizhub.com/Ironraptor3/58056bddb4914d38aa01a85e7b4459f0)

A major improvement includes the ability to pan and zoom the graphs.  When this is done to one small multiple, all small multiples repond to keep the comparison aligned.

When highlighted, a line now comes to the top of the z ordering, and gains a black border.  Lines that are not highlighted still blend together now, reducing the effects of occlusion.

Adjustments were made to several constants to provide a better visual feeling.

### Third Iteration

This is the latest iteration of the project: [![image](https://user-images.githubusercontent.com/6307522/137227924-2dbb5a47-f0cd-4468-bbf2-5fd58608de5a.png)](https://vizhub.com/Ironraptor3/baa79abe42d8486fa829b80d31aefeeb)

While there does not appear to be a lot of changes in a static image, many interactions were improved:

The width of all shapes (lines, polylines, and circles) now decrease when small multiples are zoomed in on.  This allows users to more precisely compare values.  The axes are now within their own SVGs, meaning their viewbox gets updated in such a way that they remain on screen at most times.

For user convenience, a reset button is now present to reset the viewboxes of all small multiples, allowing a user to return to the starting state.

Panning now slows down on higher zoom levels (to allow a more consistent pan speed throughout zoom levels).

### Fourth Iteration

This iteration was mainly an exploratory iteration in which I created several different Visualizations in response to the feedback given by the professor.

I first added interaction to the alternative format proposed by the professor, and altered the aggregation method from entry count to sales summation:

[![image](https://user-images.githubusercontent.com/6307522/139158738-0f8f27f3-9200-4e45-8f9d-0cabfb6402b5.png)](https://vizhub.com/Ironraptor3/cf7cb8aa3a1742b89023befde3926ce3)

Specifically, there exists a dropdown menu to survey various sales (Global, NA, EU, JP, and Other).  I appreciated the professor's suggestion of a graph in this format, as it is very easy to see how the popularity/profitability of various game genres change over time within each region and overall.

I made a second variation of this graph without the interaction, but instead stacking the bar charts within the small multiples:

[![image](https://user-images.githubusercontent.com/6307522/139159339-75f3b237-d971-45fc-b392-d91e5f359ca8.png)](https://vizhub.com/Ironraptor3/873c10b2441d4dac8ade0ab34e0bd677)

Each color represents a different region (global sales have been excluded for obvious regions).  This allows an overview of how each region has contributed to the patterns within each genre, and ends up being a stronger way of comparing the global sales of each genre over time.  It is still rather hard to compare specific countries by eye, however.

This still requires a key, as the default behavior of the plot functionality of Observable Plot does not add it.

Finally, I experimented with a Streamgraph (Stacked area chart which is centered):

[![image](https://user-images.githubusercontent.com/6307522/139159617-18e4e58f-ca1e-4f8d-8df2-dcfcf69b5b78.png)](https://vizhub.com/Ironraptor3/e9f27fcd1af343cc8a0577364c35c873)

This is a way of visualizing how each genre contributed to the total sales in each country, though it is hard to directly compare genres.  Issues with this visualization include a lack of a key/legend (as in the previous graph), and odd line behavior in the beginning (left) side of the graph.

### Fifth Iteration

This iteration saw a return to the original set of small multiples that I had been working on.  The main change made to this iteration is fixes on the axes when the user zooms and pans.  The user cannot pan past the bounds of the original graph, and cannot zoom out past holding the entire graph of a small multiple.  Instead of modifying the viewports of the axes, I instead redraw the axes with a different domain when the user interacts with the graphs.

Quality of life changes include a fake-mask rectangle below the axes and the removal of the guide lines.  The rectangles prevent the graph from overlapping the axes as the user pans and zooms.  The removal of the guide lines was done (perhaps temporarily), because they appeared to be visual clutter and I am unsure on which direction I want to take their behavior at the moment.

[![image](https://user-images.githubusercontent.com/6307522/141236246-c09c752c-d762-497c-b492-699e017ea783.png)](https://vizhub.com/Ironraptor3/f9b500a0c59c44369cb3f14ec3d46a18)

### Sixth Iteration

This iteration was again an exploratory iteration, where I made two different graphs to showcase the dataset.

The first graph is a collection of scatter plots that measure the mean sales vs the variance in sales of publishers in each category.  I believed it would be interesting to see whether certain genres were more consistent vs their profitability.  Originally, very large variances obsured many of the data points.  To fix this, I measured the mean and variance of the variances, and then used a Z score as a cutoff filter to exclude severe outliers. Finally, hovering over points allows the user to see the name of the company the point represents, though this is clearly difficult when the points are very dense.

[![image](https://user-images.githubusercontent.com/6307522/142563659-c917ea7e-93e0-4a88-82ab-75efa2122b62.png)](https://vizhub.com/Ironraptor3/520c93f628574f71b9d506a43942a50c)

The next graph was much more interesting and clean.  It is a faux-box-and-whisker plot which compares consoles over time.  As median would not make sense to implement over time, I used a weighted mean over the years to get the quartiles.  To best format this data, I made a new array of data which had duplicates of years based on the rounded up aggregate sales per genre.  The ObservableHQ code then computed the quartiles on these to display the box and whisker plot.

[![image](https://user-images.githubusercontent.com/6307522/142563971-2b1a93a0-1961-48e8-9344-c3ac971dcd34.png)](https://vizhub.com/Ironraptor3/8c8893cc28e94e00a71888e2e4dbee90)

Finally, I began refactoring my [main graph](https://vizhub.com/Ironraptor3/bb25787fb96f4b4883d5ec972cafdad6) into modules.  I came across several questions while doing so, the top two being:
- What should I do about passing many constant values in various places?
- How should I deal with modules that all reference another module best?

To resolve this, I will meet with the professor again and discuss the best way of approaching this.

### Seventh Iteration

Within this iteration, I more deeply explored the visualizations produced by the last iteration.

To improve the story told by my scatter plot small multiples (plotting mean vs variance of companies in each genre), I added labels to outlier points:

[![image](https://user-images.githubusercontent.com/6307522/143296303-7fd85edf-0223-4bbd-96a4-ddaf8369fb9d.png)](https://vizhub.com/Ironraptor3/c917535473e64ccea1b1e25dd2102058)

Then, I transitioned to using a histogram for showing sales distributions of each Platform throughout the years.  There is interaction that allows the user to see various types of sales via a dropdown menu at the top.  As demonstrated within other graphs, Japan has behavior unlike the other regions.

[![image](https://user-images.githubusercontent.com/6307522/143296485-c9b2bcb8-c61d-4b4b-a4f6-bcacdf7abd21.png)](https://vizhub.com/Ironraptor3/27b5ea7171124cbfa90e44a4224d92f3)

Finally, I used a Jupyter Notebook to visualize the box and whisker version of the data as a Joyplot, to better understand distributions:

![JP_Screenshot](https://user-images.githubusercontent.com/6307522/143296615-66f2c147-285a-47e7-bbd2-eab3fa4b24ce.PNG)


## Interaction

Interaction is key within this project.  Many methods of interaction have been added throughout the iterations of it so far, enumerated here for convenience:

- Guidelines which appear when the user clicks
  + These now scale with zoom
  + These are drawn on all small multiples
- Interactive Key
  + Hover to highlight (now with a dark outline and a change in z ordering)
  + Click to toggle visibility
- Zoom and Pan
  + All small multiples follow this action
  + Pan speed scales with zoom
  + Including a reset button to recenter the viewbox to the default position
  + Shapes scale down to account for high zoom
  + Axes now remain (mostly) visible

I currently plan on adding the following features:

- Toggle entire graphs on and off
  + Rescaling the ones that remain and rearranging them
- Dropdowns that allow users to compare different values

## Schedule of Deliverables

- Code reorganization (November 3)
  + More modularity
  + Better segementation of tasks
  + More comments
  + Get rid of magic numbers
- Axis and guideline fixes (November 10)
  + Axis granularity changes with zoom level
  + Axis always on screen (infinite)
  + Guideline always on screen (infinite)
- Visual fixes (November 17)
  + Color pallette fixes
  + Constants involving margins, spacing, thickness
- Toggle graphs on and off (November 24)
  + A control panel to perform this functionality
  + Rescaling graphs
  + Redrawing graphs in the same state as they were previously in
- Using different data (December 1)
  + Dropdowns that respond to events
  + Re-rendering graphs based on different categories on each axis
- Final submission (December 8)
  + All overflow in schedule addressed
  + Bug fixes
  + Description Revamps
