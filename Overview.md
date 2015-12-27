# Chapter 1: A view from 10.000 feet

*(Episerver was formerly known as EPiServer AB, but follow the merge with Ektron in early 2015, recently it was rebanded to Episerver (without 
the capitalized P and S. Throughout this book, we will always call the company as Episerver for consistency, even for the dates before the rebanding).)*

Episerver Commerce, of course, is one product in entire Episerver platform, which consists of Episerver CMS (Core and UI) and Episerver Find.
The history of Episerver Commerce dates back to 2010, when it was still a white brand product. Episerver already had a full-fledged CMS, but there was no 
e-Commerce solution to provide to customers, so they decided to buy. Mediachase eCommerce Framework was bought and then integrated to Episerver CMS in 
white brand manner. Essentially, there were still two products: the front-end (Episerver CMS) and the back-end (Commerce Manager). The integration part 
was mainly CatalogPageProvider, a "PageProvider" which allows the front-end pages access to the catalog system. All changes to functionalities as well
bug fixes had to go through Mediachase development. Severals releases were released, mostly to keep it compatible with CMS releases and fix bugs, from R1 to R1 SP2 in April 2012. The product was distributed as a plugin of Episerver Deployment center, and also came with Click+Talk, a sample WebForm site, based on the template site from Mediachase. Episerver then developed their own sample, Enoteca, still a WebForm site but with AJAX functionalities, for demonstration.

In the shift of strategy, Episerver saw the need of a full-fledged Commerce system. In several options available, they decided to buy Mediachase as a whole
to get both their source code, staffs and markets. The acquisition was made in April 2012, and with the source code of Mediachase, the development of 
Episerver Commerce became full speed. The first version after the acquisistion was not a big release, R3a, released in November 2012 to make it 
compatible with Episerver CMS 7. There were new concepts, but the time was not enough, so they focused on stablization on the system instead (in other words, fixing bugs). The most notably new feature is the new pricing system. Previously, prices were part of SKUs, but now they can managed separately. Commerce R3a came with Enoteca as default sample site.

The true new major version of Episerver Commerce was only released one year later, in the bundle of Episerver 7.5. The biggest feature of new version was
the CatalogContentProvider (along with the death of CatalogPageProvider, as the PageProvider was removed in Episerver CMS 7.5). From now on, the catalog 
system can be handled in the same way with CMS content via IContentRepository. New Catalog UI, a steamlined editing UI for catalog content was also introduced, and Episerver Commerce now is officially
a first class platform of Episerver. The features which were targeted for R3a were then finished and released, too, most notably Market concept. Commerce 7.5 also replace Enoteca with a new Sample site. While Enoteca was intended to be a fully featured site, it was more suitable for demonstration than to be a starter template. Developers, especially new Commerce developers, found it hard to customize the site to match their needs. New Sample site was intended to be a simple Starter package where developers can quickly get full speed and use it as a base to develop their site.

After 7.5, Episerver changed their release model. Instead of a major release every year, they switched to continous release cycle. New versions, which contain new features
and bug fixes, are released in every couple of weeks via Nuget packages. The shorter release cycle mean new features can find their way to partner developers quicker, and Episerver can get more responsive feedback, allow them to adapt more quickly to customers' needs. Along with new nuget packages, Episerver Deployment center, which has been there forever, was ditched.

Episerver, in general, goes with sematic version. Basically, a major version comes with breaking changes, a minor version comes with new features while a revision change means bug fixes. While there are no fixed schedules for releases, Episerver Commerce has been on track with one major release every year. In October 2014, Episerver Commerce 8.0 was released, with the most significant changes are to make it Cloud compatible. Episerver CMS has been Cloud compatible since 7.5 and Commerce needed to be able to deploy to cloud, primmarily Microsoft Azure and Amazon Elastic Compute Cloud, as well. The dependencies on Common Framework, mostly to support community features such as rating and comment, were removed. Fulltext Search, which was not supported by SQL Azure Database, was ditched. Some others notable changes were enhancements to Catalog UI and an interesting internal system, Migration Steps (will be discussed later).

If 7.5 was the first version that Commerce can be considered to be a first-class product in Episerver framework, 8.0 strengthened that statement. More and more edges were refined. Support for Catalog editing in new UI was improved. However, there were still many not-so-great parts of the system. Performance was still questionable. Order system was still not great to work with, and promotion system was still a pain point.

Episerver Commerce continues to evolve. Two of the main target for 8.x versions are to rework the promotion system, and to improve performance in most important areas. The new promotion system comes with the idea of BETA API:s, where special API:s get marked with a BETA tag, meaning it's subject to change. This allows Episerver to change their API:s to adapt with feedbacks from developers, without having to release a new major version. While new promotion system is a still ongoing work, performance improvments have been completed in specific areas: for example, loading orders performance was improved to be 4 times faster. However, the big change is still ahead: Commerce 9.

Catalog system was not designed to support versions. When Episerver integrated the Catalog system into the content provider, they had to work around to make it support versions. The solution at the time of Commerce 7.5 was to use a hybrid system: the DTO:s to store published data, while any other versions had to be stored in DDS. That worked at the time, but it came with its cost: there were limitations with that approach (language version handling was not consitent, the performance was not the best, if not quite bad in big system)...Commerce 9, released in October 2015, addressed those problems with a new architect. The relian on DDS was removed. The underlying metadata system was reworked. The result was worth it: In some benchmarks, the improvement was 10 times fold.

Commerce 9, by any mean, is not the final version of Episerver Commerce. It is still being actively developed. New features are being added, bugs are being fixed. Episerver Commerce was a good framework, with it quirks. It is now a great framework. It will be, no doubt, an even better framework.

Time to get our hands dirty?

