# San Diego Downtown Homeless Sleepers

This dataset provides geographic locations for homeless sleepers in Downtown San Diego, as counted by enumerators from the Downtown San Diego Partnership. These counts have been done monthly since 2012, and this dataset provides counts since 2014. 

<center><a href="https://i2.wp.com/www.sandiegodata.org/wp-content/uploads/sites/19/2019/09/Homeless-Sleepers.png?ssl=1"><img src="https://i2.wp.com/www.sandiegodata.org/wp-content/uploads/sites/19/2019/09/Homeless-Sleepers.png?ssl=1" width="400px"></a></center>


The count is done on paper maps with handwritten count marks. The San Diego
Regional Data Library's [Downton Homelessness
project](http://downtown-homelessness.sandiegodata.org/) converted these
scanned count maps using a [web based image annotation
tool](http://www.robots.ox.ac.uk/~vgg/software/via/).


## Caveats


* The ``total_count`` often does not match the sum of counts on the map. These sums were made by hand, buy the enumerator who made the counts, so there are occasional arithmetic errors.  
* There are many instances of missing values for ``rain`` or ``temp``
* Some dates include the day of the month, but many don't These dates have a day of month of 1