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
