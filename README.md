Simple Python Search Spider, Page Ranker, and Visualizer
This is a set of programs that emulate some of the functions of a search engine. They store their data in a SQLITE3 database named 'spider.sqlite'.  This file can be removed at any time to restart the process.   
You should install the SQLite browser to view and modify the databases from:
http://sqlitebrowser.org/

This program crawls a web site and pulls a series of pages into the database, recording the links between pages.
RUN spider.py
Enter web url:https://en.wikipedia.org/wiki/Portal:Current_events
How many pages:50
![Sprider py](https://user-images.githubusercontent.com/87746876/126529506-71a3b79b-348c-4bb6-a5cc-fd64ea043af9.png)

In this sample run, we told it to crawl a website and retrieve two pages.  If you restart the program again and tell it to crawl more pages, it will not re-crawl any pages already in the database. Upon restart it goes to a random non-crawled page and starts there. So each successive run of spider.py is additive.
RUN spdump.py
![Spdump](https://user-images.githubusercontent.com/87746876/126529846-0b595950-e846-4692-98c2-5c2f66ef3292.png)


This shows the number of incoming links, the old page rank, the new page rank, the id of the page, and the url of the page.  The spdump.py program only shows pages that have at least one incoming link to them.

Once you have a few pages in the database, you can run Page Rank on the pages using the sprank.py program.  You simply tell it how many Page Rank iterations to run.

RUN sprank.py
![sprank](https://user-images.githubusercontent.com/87746876/126530489-d830e026-4238-420b-b58c-fba780b1f3f8.png)

You can dump the database again to see that page rank has been updated:

You can run sprank.py as many times as you like and it will simply refine the page rank the more times you run it. You can even run sprank.py a few timesand then go spider a few more pages sith spider.py and then run sprank.pyto converge the page ranks.

If you want to restart the Page Rank calculations without re-spidering the  web pages, you can use spreset.py
All pages set to a rank of 1.0

For each iteration of the page rank algorithm it prints the average change per page of the page rank.   The network initially is quite unbalanced and so the individual page ranks are changing wildly. But in a few short iterations, the page rank converges.  You should run prank.py long enough that the page ranks converge.

If you want to visualize the current top pages in terms of page rank, run spjson.py to write the pages out in JSON format to be viewed in a web browser.

RUN spjson.py
![spjson](https://user-images.githubusercontent.com/87746876/126530957-bca413c8-dbe3-4e30-8331-3616674b98e8.png)


Open force.html in a browser to view the visualization

You can view this data by opening the file force.html in your web browser.  
This shows an automatic layout of the nodes and links.  You can click and drag any node and you can also double click on a node to find the URL that is represented by the node.

This visualization is provided using the force layout:
![visual](https://user-images.githubusercontent.com/87746876/126531184-4319f4bd-387c-464a-9f78-2eef84f94d56.png)

If you rerun the other utilities and then re-run spjson.py - you merely have to press refresh in the browser to get the new data from spider.js.
