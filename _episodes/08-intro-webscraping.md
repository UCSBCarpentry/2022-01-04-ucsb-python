---
title: "Introduction: What is web scraping?"
teaching: 15
exercises: 0
questions:
- "What is web scraping and why is it useful?"
- "What are typical use cases for web scraping?"
- "When is web scraping OK and when is it not?"
- "Is web scraping legal? Can I get into trouble?"
- "How can I make sure I'm doing the right thing?"
- "What can I do with the data that I've scraped?"
objectives:
- "Introduce the concept of structured data"
- "Discuss how data can be extracted from web pages"
- "Introduce the examples that will be used in this lesson"
- "Discuss the legal implications of web scraping"
- "Establish a code of conduct"
keypoints:
- "Humans are good at categorizing information, computers not so much."
- "Often, data on a web site is not properly structured, making its extraction difficult."
- "Web scraping is the process of automating the extraction of data from web sites."
- "Web scraping is, in general, legal and won't get you into trouble."
- "There are a few things to be careful about, notably don't overwhelm a web server and don't steal content."
- "Be nice. In doubt, ask."
---

## What is web scraping?

Web scraping is a technique for extracting information from websites. This can be done manually
but it is usually faster, more efficient and less error-prone to automate the task.

Web scraping allows you to acquire non-tabular or poorly structured data from websites and convert it
into a usable, structured format, such as a .csv file or spreadsheet.

Scraping is about more than just acquiring data: it can also help you archive data and track changes to data online.

It is closely related to the practice of
web _indexing_, which is what search engines like Google do when mass-analysing the Web to build
their indices. But contrary to _web indexing_, which typically parses the entire content of a web
page to make it searchable, _web scraping_ targets specific information on the pages visited.

For example, online stores will often scour the publicly available pages of their competitors,
scrape item prices, and then use this information to adjust their own prices. Another common
practice is "contact scraping" in which personal information like email
addresses or phone numbers is collected for marketing purposes.

Web scraping is also increasingly being used by scholars to create data sets for
text mining projects; these might be collections of journal articles or digitised texts. The practice of
[data journalism](https://en.wikipedia.org/wiki/Data_journalism), in particular, relies on the
ability of investigative journalists to harvest data that is not always presented or published in a form
that allows analysis.

## Before you get started

As useful as scraping is, there might be better options for the task. Choose the right (i.e. the easiest) tool for the job.

- Check whether or not you can easily copy and paste data from a site into Excel or Google Sheets. This might be quicker than scraping.
- Check if the site or service already provides an API to extract structured data. If it does, that will be a much more efficient and effective pathway. Good examples are the
[Facebook API](https://developers.facebook.com/tools/explorer/), the [Twitter APIs](https://dev.twitter.com/rest/public) or the [YouTube comments API](https://developers.google.com/youtube/v3/docs/commentThreads/list).
- For much larger needs, Freedom of information requests can be useful. Be specific about the formats required for the data you want.

we will be discussing some of the issues to be aware of when
scraping websites, and we will establish a [code of conduct (below)](#web-scraping-code-of-conduct)
to guide our web scraping projects.

> ## This section does not constitute legal advice
>
> Please note that the information provided on this page is for information
> purposes only and does not constitute professional legal advice on the
> practice of web scraping.
>
> If you are concerned about the legal implications of using web scraping
> on a project you are working on, it is probably a good idea to seek
> advice from a professional, preferably someone who has knowledge of the
> intellectual property (copyright) legislation in effect in your country.
>
{: .callout}

## Don't break the web: Denial of Service attacks

The first and most important thing to be careful about when writing a web scraper is that
it typically involves querying a website repeatedly and accessing a potentially large
number of pages. For each of these pages, a request will be sent to the web server that
is hosting the site, and the server will have to process the request and send a response
back to the computer that is running our code. Each of these requests will consume resources
on the server, during which it will not be doing something else, like for example responding
to someone else trying to access the same site.

If we send too many such requests over a short span of time, we can prevent other "normal" users
from accessing the site during that time, or even cause the server to run out of resources and crash.

In fact, this is such an efficient way to disrupt a web site that hackers are often doing it on purpose.
This is called a [Denial of Service (DoS) attack](https://en.wikipedia.org/wiki/Denial-of-service_attack).

Since DoS attacks are unfortunately a common occurence on the Internet, modern web servers include
measures to ward off such illegitimate use of their resources. They are watchful for large amounts
of requests appearing to come from a single computer or IP address, and their first line of defense often involves
refusing any further requests coming from this IP address.

A web scraper, even one with legitimate purposes and no intent to bring a website down, can exhibit
similar behaviour and, if we are not careful, result in our computer being banned from accessing
a website.

The good news is that a good web scraper, such as Scrapy, recognizes that this is a risk and includes
measures to prevent our code from appearing to launch a DoS attack on a website. This is mostly
done by inserting a random delay between individual requests, which gives the target server enough
time to handle requests from other users between ours.

This is Scrapy's default behaviour, and it should prevent most scraping projects from ever causing problems.
To be on the safe side, however, it is good practice to limit the number of pages we are scraping
while we are still writing and debugging our code. This is why in the previous section, we imposed
a limit of five pages to be scraped, which we only removed when we were reasonably certain the scraper
was working as it should.

Limiting requests to a particular domain, by using Scrapy's `allowed_domains` property is another
way to make sure our code is not going to start scraping the entire Internet by mistake.

Thanks to the defenses web servers use to protect themselves against DoS attacks and Scrapy's
measure to avoid inadvertently launching such an attack, the risks of causing trouble is limited.

## Don't steal: Copyright and fair use

It is important to recognize that in certain circumstances web scraping _can_ be illegal. If the terms
and conditions of the web site we are scraping specifically prohibit downloading
and copying its content, then we could be in trouble for scraping it.

In practice, however, web scraping is a tolerated practice, provided reasonable
care is taken not to disrupt the "regular" use of a web site, as we have seen above.

In a sense, web scraping is no different than using a web browser to visit a web page,
in that it amounts to using computer software (a browser vs a scraper) to acccess
data that is publicly available on the web.

In general, if data is publicly available (the content that is being scraped is not
behind a password-protected authentication system), then it is OK to scrape it,
provided we don't break the web site doing so. What is potentially
problematic is if the scraped data will be shared further. For example, downloading
content off one website and posting it on another website (as our own), unless
explicitely permitted, would constitute copyright violation and be illegal.

However, most copyright legislations recognize cases in which reusing some, possibly
copyrighted, information in an aggregate or derivative format is considered
"fair use". In general, unless the intent is to pass off data as our own, copy
it word for word or trying to make money out of it, reusing publicly available
content scraped off the internet is OK.

### Better be safe than sorry
Be aware that copyright and data privacy legislation typically differs from country
to country. Be sure to check the laws that apply in your context. For example, in Australia,
it can be illegal to scrape and store personal information such as names, phone
numbers and email addresses, even if they are publicly available.

If you are looking to scrape data for your own personal use, then the above
guidelines should probably be all that you need to worry about. However,
if you plan to start harvesting a large amount of data for research
or commercial purposes, you should probably seek legal advice first.

If you work in a university, chances are it has a copyright office that
will help you sort out the legal aspects of your project. The
university library is often the best place to start looking for help on
copyright.

## Be nice: ask and share

Depending on the scope of your project, it might be worthwhile to consider asking
the owners or curators of the data you are planning to scrape if they have it
already available in a structured format that could suit your project. If your
aim is do use their data for research, or to use it in a way that could potentially
interest them, not only it could save you the trouble of writing a
web scraper, but it could also help clarify straight away what you can and cannot do
with the data.

On the other hand, when you are publishing your own data, as part of a research project,
documentation or a public website, you might want to think about whether someone might
be interested in getting your data for their own project. If you can, try to provide
others with a way to download your raw data in a structured format, and thus save
them the trouble to try and scrape your own pages!

## Web scraping code of conduct

This all being said, if you adhere to the following simple rules, you will probably
be fine.

1. __Ask nicely.__ If your project requires data from a particular organisation, for example,
   you can try asking them directly if they could provide you what you are looking for.
   With some luck, they will have the primary data that they used on their website in a
   structured format, saving you the trouble.
2. __Don't download copies of documents that are clearly not public.__ For example, academic
   journal publishers often have very strict rules about what you can and what you cannot
   do with their databases. Mass downloading article PDFs is probably prohibited and can
   put you (or at the very least your friendly university librarian) in trouble. If your
   project requires local copies of documents (e.g. for text mining projects), special
   agreements can be reached with the publisher. The library is a good place to start
   investigating something like that.
3. __Check your local legislation.__ For example, certain countries have laws protecting
   personal information such as email addresses and phone numbers. Scraping such information,
   even from publicly avaialable web sites, can be illegal (e.g. in Australia).
4. __Don't share downloaded content illegally.__ Scraping for personal purposes is usually
   OK, even if it is copyrighted information, as it could fall under the fair use provision
   of the intellectual property legislation. However, sharing data for which you don't
   hold the right to share is illegal.
5. __Share what you can.__ If the data you scraped is in the public domain or you got
   permission to share it, then put it out there for other people to reuse it (e.g. on
   [datahub.io](https://datahub.io)). If you
   wrote a web scraper to access it, share its code (e.g. on GitHub) so that others can
   benefit from it.
6. __Don't break the Internet.__ Not all web sites are designed to withstand thousands of
   requests per second. If you are writing a recursive scraper (i.e. that follows
   hyperlinks), test it on a smaller dataset first to make sure it does what it is
   supposed to do. Adjust the settings of your scraper to allow for a delay between
   requests. By default, Scrapy uses conservative settings that should minimize this risk.
7. __Publish your own data in a reusable way.__ Don't force others to write their own
   scrapers to get at your data. Use open and software-agnostic formats (e.g. JSON, XML),
   provide metadata (data about your data: where it came from, what it represents, how
   to use it, etc.) and make sure it can be indexed by search engines so that people can
   find it.

## Going further

This lesson only provides an introduction to the practice of web scraping and highlights
some of the tools available. Scrapy has many more features than those mentioned in the
previous section, be sure to refer to its [full documentation](https://doc.scrapy.org/en/latest/)
for details.

## Example: scraping government websites for contact addresses

In this lesson, we will extract contact information
from government websites that list the members of various constituencies. Librarians could use this example
to scrape information from any site listing contact details.

Let's start by looking at the current list of members of the Canadian parliament, which is available
on the [Parliament of Canada website](http://www.parl.gc.ca/Parliamentarians/en/members).

This is how this page appears in November 2016:

![Screenshot of the Parliament of Canada website]({{ page.root }}/fig/canparl.png)

There are several features (circled in the image above) that make the data on this page easier to work with.
The search, reorder, refine features and display modes hint that the data is actually stored in a (structured)
database before being displayed on this page. The data can be readily downloaded either as a comma separated values (.csv)
file or as XML for re-use in their own database, spreadsheet or computer program.

Even though the information displayed in the view above is not labelled, anyone visiting this site with some
knowledge of Canadian geography and politics can see what information pertains to the
politicians' names, the geographical area they come from and the political party they represent. This is because human
beings are good at using context and prior knowledge to quickly categorise information.

Computers, on the other hand, cannot do this unless we provide them with more information.
Fortunately, if we examine the source HTML code of this page, we can see that the information displayed is actually
organised inside labelled elements:

~~~
(...)
<div>
    <a href="/Parliamentarians/en/members/Ziad-Aboultaif(89156)">
        <img alt="Photo - Ziad Aboultaif - Click to open the Member of Parliament profile" title="Photo - Ziad Aboultaif - Click to open the Member of Parliament profile" src="http://www.parl.gc.ca/Parliamentarians/Images/OfficialMPPhotos/42/AboultaifZiad_CPC.jpg" class="picture" />
        <div class="full-name">
		    <span class="honorific"><abbr></abbr></span>
            <span class="first-name">Ziad</span>
            <span class="last-name">Aboultaif</span>
        </div>
    </a>
    <div class="caucus-banner" style="background-color:#002395"></div>
    <div class="caucus">Conservative</div>
    <div class="constituency">Edmonton Manning</div>
    <div class="province">Alberta</div>        
</div>
(...)
~~~
{: .output}

Thanks to these labels, we could relatively easily instruct a computer to look for all parliamentarians from
Alberta and list their names and caucus information.

> ## Structured vs unstructured data
>
> When presented with information, human beings are good at quickly categorizing it and extracting the data
> that they are interested in. For example, when we look at a magazine rack, provided the titles are written
> in a script that we are able to read, we can rapidly figure out the titles of the magazines, the stories they
> contain, the language they are written in, etc. and we can probably also easily organize them by topic,
> recognize those that are aimed at children, or even whether they lean toward a particular end of the
> political spectrum. Computers have a much harder time making sense of such _unstructured_ data unless
> we specifically tell them what elements data is made of, for example by adding labels such as
> _this is the title of this magazine_ or _this is a magazine about food_. Data in which individual elements
> are separated and labelled is said to be _structured_.
>
{: .callout}

Let's look now at the current list of members for the [UK House of Commons](https://www.parliament.uk/mps-lords-and-offices/mps/).

![Screenshot of the UK House of Commons website]({{ page.root }}/fig/ukparl.png)

This page also displays a list of names, political and geographical affiliation. There is a search box and
a filter option, but no obvious way to download this information and reuse it.

Here is the code for this page:

~~~
(...)
<table>
    <tbody>
        (...)
        <tr id="ctl00_ctl00_(...)_trItemRow" class="first">
            <td>Aberavon</td>
            <td id="ctl00_ctl00_(...)_tdNameCellRight">
                <a id="ctl00_ctl00_(...)_hypName" href="http://www.parliament.uk/biographies/commons/stephen-kinnock/4359">Kinnock, Stephen</a>(Labour)
            </td>
        </tr>
        (...)
    </tbody>
</table>
(...)
~~~
{: .output}

We see that this data has been structured for displaying purposes (it is arranged in rows inside
a table) but the different elements of information are not clearly labelled.

What if we wanted to download this dataset and, for example, compare it with the Canadian list of MPs
to analyze gender representation, or the representation of political forces in the two groups?
We could try copy-pasting the entire table into a spreadsheet or even manually
copy-pasting the names and parties in another document, but this can quickly become impractical when
faced with a large set of data. What if we wanted to collect this information for every country that
has a parliamentary system?

Fortunately, there are tools to automate at least part of the process. This technique is called
_web scraping_.

>
> "Web scraping (web harvesting or web data extraction) is a computer software technique of
> extracting information from websites."
> (Source: [Wikipedia](https://en.wikipedia.org/wiki/Web_scraping))
>

Web scraping typically targets one web site at a
time to extract unstructured information and put it in a structured form for reuse.

In this lesson, we will continue exploring the examples above and try different techniques to extract
the information they contain. But before we launch into web scraping proper, we need to look
a bit closer at how information is organized within an HTML document and how to build queries to access
a specific subset of that information.

# References

* [Web Scraping (Wikipedia)](https://en.wikipedia.org/wiki/Web_scraping)
* [The Data Journalism Handbook: Getting Data from the Web](http://datajournalismhandbook.org/1.0/en/getting_data_3.html)
* The [Web scraping Wikipedia page](https://en.wikipedia.org/wiki/Web_scraping) has a concise
  definition of many concepts discussed here.
* The [School of Data Handbook](http://schoolofdata.org/handbook/courses/scraping/) has a
  short introduction to web scraping, with links to resources e.g. for data journalists.
* [This blog](https://blog.rubyroidlabs.com/2016/04/web-scraping-1/) has a discussion on
  the legal aspects of web scraping.
* [Scrapy documentation](https://doc.scrapy.org/en/latest/)
* [morph.io](https://morph.io/) is a cloud-based web scraping platform that supports multiple
  frameworks, interacts with GitHub and provides a built-in way to save and share extracted
  data.
* [import.io](https://www.import.io/) is a commercial web-based scraping service that requires
  little coding.
* [Software Carpentry](https://software-carpentry.org/) is a non-profit organisation that
  runs learn-to-code workshops worldwide. All lessons are publicly available and can be
  followed indepentently. This lesson is heavily inspired by Software Carpentry.
* [Data Carpentry](http://www.datacarpentry.org/) is a sister organisation of Software Carpentry
  focused on the fundamental data management skills required to conduct research.
* [Library Carpentry](https://librarycarpentry.github.io/) is another Software Carpentry spinoff
  focused on software skills for librarians.
