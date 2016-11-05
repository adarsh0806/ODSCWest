## Applying Data Science to drive infrastructure decisions - Avijit Mukherjee, Facebook ##

Focus on cellular coverage in rural areas. How do we solve this problem?

* Can we get data from satellites and build a vizualization so governments take that data to decide where to deploy cellular towers.
* 70% of people in rural areas dont have cellular coverage.
* Where do people live? Where are the gaps?
* Does other infrastructure exist that can be used?
* Deploying towers everywhere is too expensive.

Main factors to be considered:

* Population presence
* Phone penetration
* Income
* Cost of Service
* Quality of service
* Relevance

Where do people live?

* Housefinder - using satellite images find houses
* DBSCAN clusters - where are the communities
* Settlments - these groups of clusters will form a settlement.
* Concave hull

House detections

* Raw satellite data -> divide images to 30x30m grids 

DBSCAN

* Method used for clustering problems
* Useful for spatial data
* 2 main parameters - distance threshold, number of neighbors
* Partition data - based on density(so parameters can be set based on urban/rural areas), computational benefits.
* Results - India/Philipines have administrative boundaries can be used, density based not used here. Applied DBSCAN