#Overview

The catalog system, in many means, can be called the heart of Episerver Commerce. It might be the most used system in entirely Commerce. From cases to cases
implementations might want to replace the order system, or to let their CRM to handle customers data, but all of them use the Catalog system.

There are two API:s system in Episerver Commerce, the old one, which built around the famous ICatalogSystem and works directly with DTO objects, and the new 
API:s based on the CMS content provider system - IContentRepository. The latter uses the former internally, so you might ask why not use the ICatalogSystem directly,
but there are reasons to prefer the content way instead.

#ReferenceConverter - the brigde of two system.
One of the biggest features in Episerver CMS is its content provider system, which allow you to plug your own content provider to the system. 
So anything can be considered content, and can be manipulated with one unified API:s. However, to do that, you have to solve the first issue - the identity.

The Commerce catalog structure comes in 3 types of data: Catalog, Node and Entry. It would be easier to imagine it to be a tree (but of course in reality it's more complicated
with all kind of relations and associations). There are two problem Commerce had to resolve when they try to plug the catalog structure into the content provider system.
Firstly, the data are stored in three separated tables (and you might already know, Catalog, CatalogNode and CatalogEntry), with the auto incremented identity. So a content with ID =1
can be a Catalog, a Node or an Entry. Secondly, there can be multiple catalogs, while you need a "root" content to attach your content provider system.

The second one can be easily resolved by introducing a virtual root. It's just another content, but virtual, meaning you can never edit or delete it. It's there, created on the fly whenever you
need it. But the first one is a bit tricky. That was when ReferenceConverter came to life.

#The MetaData system

#Get to know the storage structure

#The strongly typed models
