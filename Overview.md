#A view from 10.000 feet

*(Episerver was formerly known as EPiServer AB, but follow the merge with Ektron in early 2015, recently it was rebanded to Episerver (without 
the capitalized P and S. Throughout this book, we will always call the company as Episerver for consistency, even for the dates before the rebanding).)*

Episerver Commerce, of course, is one product in entire Episerver platform, which consists of Episerver CMS (Core and UI) and Episerver Find.
The history of Episerver Commerce dates back to 2010, when it was still a white brand product. Episerver already had a full-fledged CMS, but there was no 
e-Commerce solution to provide to customers, so they decided to buy. Mediachase eCommerce Framework was bought and then integrated to Episerver CMS in 
white brand manner. Essentially, there were still two products: the front-end (Episerver CMS) and the back-end (Commerce Manager). The integration part 
was mainly CatalogPageProvider, a "PageProvider" which allows the front-end pages access to the catalog system. All changes to functionalities as well
bug fixes had to go through Mediachase development. Severals releases were released, mostly to keep it compatible with CMS releases and fix bugs, from R1 to R1 SP2 in April 2012.

In the shift of strategy, Episerver saw the need of a full-fledged Commerce system. In several options available, they decided to buy Mediachase as a whole
to get both their source code, staffs and markets. The acquisition was made in April 2012, and with the source code of Mediachase, the development of 
Episerver Commerce became full speed. The first version after the acquisistion was not a big release, R3a, released in November 2012 to make it 
compatible with Episerver CMS 7. There were new concepts, but the time was not enough, so they focused on stablization on the system instead.

The true new major version of Episerver Commerce was only released one year later, in the bundle of Episerver 7.5. The biggest feature of new version was
the CatalogContentProvider (along with the death of CatalogPageProvider, as the PageProvider was removed in Episerver CMS 7.5). From now on, the catalog 
system can be handled in the same way with CMS content via IContentRepository. New Catalog UI, a steamlined editing UI for catalog content was also introduced, and Episerver Commerce now is officially
a first class platform of Episerver. The features which were targeted for R3a were then finished and released, too, most notably Market concept. 

After 7.5, Episerver changed their release model. Instead of a major release every year, they switched to continous release cycle. New versions, which contain new features
and bug fixes, are released in every couple of weeks via Nuget packages. 

