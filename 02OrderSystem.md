No matter how shiny your website is, no matter how cool your URL is, and no matter how fancy the technologies you used to build it - in the end, it's the orders 
you take that really matter - the most important measure to a success of a e-Commerce website.

This chapter will be focus on how the order system works, and how you can do better.

##Overview

Order system, as same as the catalog system, is based on the MetaDataPlus MetaClass system. That means, you can extend your classes with additional
attributes to match with your business need. By default, it can be seen as even more complicated than the catalog system. With Catalog system, you only
have two base classes (CatalogEntry and CatalogNode, you can consider CatalogEntryEx and CatalogNodeEx are default classes, but they are rarely used), 
but for the order system, it's quite many: 
Here's the list of default order metaclasses from the default installation:
![Default order metaclasses](https://github.com/vimvq1987/proepiservercommerce/blob/master/02DefaultOrderMetaclasses.PNG "From default installation")

##OrderGroup - the core of anything.

