#Overview

The catalog system, in many means, can be called the heart of Episerver Commerce. It might be the most used system in entirely Commerce. From cases to cases
implementations might want to replace the order system, or to let their CRM to handle customers data, but all of them use the Catalog system.

There are two API:s system in Episerver Commerce, the old one, which built around the famous ICatalogSystem and works directly with DTO objects, and the new 
API:s based on the CMS content provider system - IContentRepository. The latter uses the former internally, so you might ask why not use the ICatalogSystem directly,
but there are reasons to prefer the content way instead.

#ReferenceConverter - the brigde of two systems.
One of the biggest features in Episerver CMS is its content provider system, which allow you to plug your own content provider to the system. 
So anything can be considered content, and can be manipulated with one unified API:s. However, to do that, you have to solve the first issue - the identity.

The Commerce catalog structure comes in 3 types of data: Catalog, Node and Entry. It would be easier to imagine it to be a tree (but of course in reality it's more complicated
with all kind of relations and associations). There are two problem Commerce had to resolve when they try to plug the catalog structure into the content provider system.
Firstly, the data are stored in three separated tables (and you might already know, Catalog, CatalogNode and CatalogEntry), with the auto incremented identity. So a content with ID =1
can be a Catalog, a Node or an Entry. Secondly, there can be multiple catalogs, while you need a "root" content to attach your content provider system.

The second one can be easily resolved by introducing a virtual root. It's just another content, but virtual, meaning you can never edit or delete it. It's there, created on the fly whenever you
need it. But the first one is a bit tricky. That was when ReferenceConverter came to life.

The content provider system requires every content to be identified by a specific ContentReference, which is supposed to be unique in the system. A ContentReference consists of three parts:

### A sample catalog content reference: 123_1_CatalogContent

- The first one is the content id, which is mandatory. The ID is supposed to be unique
- The work id, which identifies the version of the content
- The content provider name. This will allow the content system to know which provider should be handling the content. For catalog content, it's always CatalogContentProvider who does the leg works.

*It was a big change in Commerce 9 in the way work id is hanled. Prior Commerce 9, the work id is only unique within the catalog content. So it's possible to have both 1_3_CatalogContent and 2_3_CatalogContent. This was not inline which how CMS handle the work id. In Commerce 9, the work id is unique across the system. So you can only have 1_3_CatalogContent and 2_4_CatalogContent and 2_5_CatalogContent and 1_6_CatalogContent and so on and so forth. This will introduce a limitation, as you can only have a maximum of 4294967295 catalog content versions in your entire system, but it's plenty even you have the biggest catalogs in your system. The change in the way work id is handled, was proved to improve the overall system performance.*

*It's CatalogContentProvider who does the hard work of processing catalog contents, but you should never work with it directly. The only API:s you should work with are IContentLoader and IContentRepository. Those will make sure to call the responsible content provider to handle the content it's processing (and doing other stuffs such as caching, raising events or so). I even make a bold statement: if you're working with CatalogContentProvider, you are doing it wrong. However, I think it deserves a honorable mention for its unsung works. You're the silent hero, CatalogContentProvider.*

#The MetaData system

It's hard to fully understand the Catalog system without knowing about the MetaData system, with its MetaClass(es) and MetaField(s). Note that there are two classes named MetaClass in Episerver Commerce. The one resides in Mediachase.MetaDataPlus.Configurator is the one we are talking about.

*(Yeah, it's not the best naming to have two classes named exactly the same in your framework, even if they are in two separated assemblies. I must admit I am still confused by them, and it takes me a few seconds to navigate to the correct class. However, they have been there since forever and any changes would become a big breaking change. We'll have to live with it for now.)*

#Get to know the storage structure

#The strongly typed models
