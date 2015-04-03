---
title: Hyperlink
page_title: Hyperlink | UI for ASP.NET AJAX Documentation
description: Hyperlink
slug: spreadprocessing/features/hyperlink
tags: hyperlink
published: True
position: 7
---

# Hyperlink



__Hyperlinks__ enable quick access to web pages, places in the workbook or email addresses. This article demonstrates how to use the feature in terms of the API exposed by the document model.

* [HyperlinkCollection](#hyperlinkcollection)

* [Add Hyperlink](#add-hyperlink)

* [Search for Hyperlink](#search-for-hyperlink)

* [Remove Hyperlink](#remove-hyperlink)

## HyperlinkCollection

Each worksheet object maintains a collection of the hyperlinks it contains. This collection can be reached through the __Hyperlinks__ property of the Worksheet class. This property is of type __HyperlinkCollection__ and facilitates the process of searching, adding and removing hyperlinks.

The __SpreadsheetHyperlink__ class is the representation of hyperlink in the document model. The class exposes the following properties:

* __Range__: Property of type CellRange; indicates the range of cells that holds the hyperlink info.

* __HyperlinkInfo__: Property of type __HyperlinkInfo__; indicates the type of the hyperlink (Url, MailTo, InDocument) and contains information about the target of the hyperlink.As the description of __HyperlinkInfo__ suggests, there are three supported types of hyperlinks:

* __Url__: The Url hyperlink refers to a page on the internet.

* __MailTo__: The MailTo hyperlink contains an e-mail address and, optionally, a subject.

* __InDocument__: The InDocument hyperlink holds a reference to a cell range in string format, e.g. A1:B3.

Depending on the type of the hyperlink, the __HyperlinkInfo__ object may contain additional information about the target. The class exposes the string properties Address, EmailSubject, ScreenTip and SubAddress and each hyperlink type requires a set of these properties to be filled. Note, however, that some of them are mutually exclusive. For example, if you have a Url hyperlink, you do not need to specify the EmailSubject.

You can create instances of each of those types, using the static methods of the __HyperlinkInfo__ class.

__Example 1__ creates a hyperlink to a web address.

````C#
	            HyperlinkInfo webAddres = HyperlinkInfo.CreateHyperlink("http://telerik.com", "Telerik");
````



__Example 2__ creates a hyperlink to a cell range somewhere in the document.

````C#
	            HyperlinkInfo inDocument = HyperlinkInfo.CreateInDocumentHyperlink("A1:B3", "Go to A1:B3");
````



__Example 3__ create a hyperlink to an email address.

````C#
	            HyperlinkInfo mailto = HyperlinkInfo.CreateMailtoHyperlink("someOne@someCompany.com", "someSubject", "Mail to someOne");
````



## Add Hyperlink

To add a hyperlink, you need to specify a cell range that will contain the hyperlink and a hyperlink info that will determine the type of the hyperlink.

__Example 4__ assigns the hyperlink created in __Example 1__ to A1:

````C#
	            CellIndex a1Index = new CellIndex(0, 0);
	            SpreadsheetHyperlink spreadsheetHyperlink = worksheet.Hyperlinks.Add(a1Index, webAddres);
````



## Search for Hyperlink

There are several ways you can retrieve hyperlinks from the __HyperlinkCollection__ depending on their position relative to a given cell range.

__Example 5__ defines two indexes and then a cell range out of those indexes.

````C#
	            CellIndex a1Index = new CellIndex(0, 0);
	            CellIndex b3Index = new CellIndex(2, 1);
	            CellRange a1b3Range = new CellRange(a1Index, b3Index);
````



1. __Example 6__ gets all hyperlinks the ranges of which are contained in the cell range from __Example 5__.

````C#
	            IEnumerable<SpreadsheetHyperlink> containingHyperlinks = worksheet.Hyperlinks.GetContainingHyperlinks(a1b3Range);
````



>note The __GetContainingHyperlinks()__ method has an overload which accepts a collection of cell ranges.
>


1. __Example 7__ gets all hyperlinks the ranges of which intersect with the cell range from __Example 5__.

````C#
	            IEnumerable<SpreadsheetHyperlink> intersectingHyperlinks = worksheet.Hyperlinks.GetIntersectingHyperlinks(a1b3Range);
````



1. __Example 8__ gets the last added hyperlink that intersects with the cell range from __Example 5__.

````C#
	            bool canGetHyperlink = worksheet.Hyperlinks.TryGetHyperlink(a1Index, out spreadsheetHyperlink);
````



>note The __TryGetHyperlink__ method has an overload that accepts a __CellIndex__ instead of __CellRange__ .
>


1. __Example 9__ gets the hyperlink which range matches the cell range from __Example 5__.

````C#
	            bool canGetHyperlinkExact = worksheet.Hyperlinks.TryGetHyperlinkExact(a1b3Range, out spreadsheetHyperlink);
````



## Remove Hyperlink

To remove a hyperlink you need to retrieve a __SpreadsheetHyperlink__ object and then remove it from the hyperlinks collection.

__Example 10__ removes a hyperlink.

````C#
	            SpreadsheetHyperlink spreadsheetHyperlink;
	            if (worksheet.Hyperlinks.TryGetHyperlink(a1Index, out spreadsheetHyperlink))
	            {
	                worksheet.Hyperlinks.Remove(spreadsheetHyperlink);
	            }
````

