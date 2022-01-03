---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "University of California, Santa Barbara"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "1021 Anacapa St, Santa Barbara, CA 93101"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "us"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "34.422710"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-119.701970"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "January 4th, 7th 2022"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "Tuesday, 1 pm - 5 pm; Friday 9 am - 1 pm PST"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2022-01-04      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2022-01-04        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Greg Janée", "Amanda Ho"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Sam Csik", "Kat Le", "Ian Lessing", "Jamie Montgomery"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["library-collaboratory@ucsb.edu"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes: https://pad.carpentries.org/2022-01-04-ucsb-python  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite: 229634923237  # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% comment %}
{% endcomment %}


<h3><strike>This workshop will take place between the main UCSB Campus and the NCEAS downtown location</strike><h3>
This workshop will now be online due to temporary remote instruction. Please keep an eye on your email for more information.
<br>


{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% if site.pilot %}
This is a pilot workshop, testing out a lesson that is still under development. The lesson authors would appreciate any feedback you can give them about the lesson content and suggestions for how it could be further improved.
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://www.latlong.net/ to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>

This workshop's location will be split between the main UCSB Campus and NCEAS Downtown. 
<br>
Jan 4th will be at the UCSB Library
Jan 7th will be at NCEAS Downtown
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody.  For workshops at a physical location, the workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of the workshop if you require any accommodations or if there is
  anything we can do to make this workshop more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
{% if site.carpentry == "incubator" %}
<p><a href="{{ site.incubator_pre_survey }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.incubator_post_survey }}">Post-workshop Survey</a></p>
{% elsif site.incubator_pre_survey or site.incubator_post_survey %}
<div class="alert alert-danger">
WARNING: you have defined custom pre- and/or post-survey links for
a workshop not configured for The Carpentries Incubator
(the value of `curriculum` is not set to `incubator` in `_config.yml`).
Please comment out the `incubator_pre_survey` and `incubator_post_survey` fields
in `_config.yml` or, if this workshop is teaching a lesson in the Incubator,
change the value of `carpentry` to `incubator`.
</div>
{% else %}
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Schedule</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% elsif site.carpentry == "incubator" %}
This workshop is teaching a lesson in [The Carpentries Incubator](https://carpentries-incubator.org/).
Please check [the lesson homepage]({{ site.incubator_lesson_site }}) for a list of lesson sections and estimated timings.
{% endif %}

{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom-schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}

{% if site.pilot %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. Please [contact the workshop organisers](#contact) if you would like more information about the planned schedule.
{% endif %}

<hr/>


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to software as described below.
  In addition, you will need an up-to-date <a href="https://www.google.com/chrome/">Chrome web browser</a>.
</p>
<ul style="list-style-type:circle">
  <li> <a href="https://www.anaconda.com/products/individual">Anaconda</a></li> 
  <li> <b>Windows</b>: Make sure that <b>Register Anaconda as my default Python 3.x</b> option is selected. It should be the latest version of Anaconda</li>
  <li> <b>Mac</b>:Make sure install location is set to <b>install only for me</b> so Anaconda will install files locally</li>
  <li> Verify the installation by opening the terminal and typing in <span style="font-family: monospace;">jupyter lab</span> to launch a jupyter interface</li>
</ul>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

<h2 id="setup">Data</h2>

<p>
  Data for this lesson is from the
  <a href= "https://figshare.com/articles/Portal_Project_Teaching_Database/1314459">Portal Project Teaching
    Database</a>.
  Specifically, we use the following eight data files:
 </p>
 <ul style="list-style-type:circle">
  <li> surveys.csv </li>
    <li> surveys2001.csv </li>
    <li> surveys2002.csv </li>
    <li> species.csv </li>
    <li> speciesSubset.csv </li>
    <li> plots.csv </li>
    <li> bouldercreek_09_2013.txt </li>
    <li> portal_mammals.sqlite </li>
  </ul>
<p>
  Please download them (by clicking on the corresponding links) and move them to the same directory, or
  <a href= "https://datacarpentry.org/python-ecology-lesson/data/portal-teachingdb-master.zip">download all
    the files as a zip</a>
  which will give you everything in a single compressed file. You'll need to unzip
  this file after downloading it.
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "incubator" %}

## Data
Data for this lesson is from the
[Portal Project Teaching Database](https://figshare.com/articles/Portal_Project_Teaching_Database/1314459).
Specifically, we use the following eight data files:
- [surveys.csv](https://ndownloader.figshare.com/files/10717177)
- [surveys2001.csv]({{ page.root }}/data/yearly_files/surveys2001.csv)
- [surveys2002.csv]({{ page.root }}/data/yearly_files/surveys2002.csv)
- [species.csv](https://ndownloader.figshare.com/files/3299483)
- [speciesSubset.csv]({{ page.root }}/data/speciesSubset.csv)
- [plots.csv](https://ndownloader.figshare.com/files/3299474)
- [bouldercreek_09_2013.txt]({{ page.root }}/data/bouldercreek_09_2013.txt)
- [portal_mammals.sqlite](https://ndownloader.figshare.com/files/11188550)
>
Please download them (by clicking on the corresponding links) and move them to the same directory, or
[download all the files as a zip](https://drive.google.com/file/d/1cx6-azDBVf9cbjY60R3DTimQPbImxmyZ/view?usp=sharing)
which will give you everything in a single compressed file. You'll need to unzip
this file after downloading it.


## Installing Python using Anaconda

[Python][python] is a popular language for scientific computing, and great for
general-purpose programming as well. Installing all of the scientific packages we use in the lesson
individually can be a bit cumbersome, and therefore recommend the all-in-one
installer [Anaconda][anaconda].

Regardless of how you choose to install it, please make sure you install Python
version 3.x (e.g., 3.6 is fine).

## Installing Anaconda

{::options parse_block_html="true" /}
<div>
<ul class="nav nav-tabs" role="tablist">
  <li role="presentation" class="active"><a data-os="windows" href="#anaconda-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
  <li role="presentation"><a data-os="macos" href="#anaconda-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
  <li role="presentation"><a data-os="linux" href="#anaconda-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
</ul>

<div class="tab-content">
<article role="tabpanel" class="tab-pane active" id="anaconda-windows">

1.  Open <https://www.anaconda.com/products/individual> in your web browser.
2.  Download the Anaconda Python 3 installer for Windows.
3.  Double-click the executable and install Python 3 using the recommended settings.
    Make sure that **Register Anaconda as my default Python 3.x** option is checked --
    it should be in the latest version of Anaconda.
4.  Verify the installation:
    click Start, search and select `Anaconda Prompt` from the menu.
    A window should pop up where you can now type commands
    such as checking your Conda installation with:

    ~~~
    conda --help
    ~~~
    {: .language-bash}

#### Video Tutorial

<div class="yt-wrapper2">
<div class="yt-wrapper">
<iframe type="text/html" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" src="https://www.youtube-nocookie.com/embed/xxQ0mzZ8UvA?modestbranding=1&playsinline=1&iv_load_policy=3&rel=0" class="yt-frame" allowfullscreen></iframe>
</div>
</div>
</article>

<article role="tabpanel" class="tab-pane" id="anaconda-macos">

1.  Visit <https://www.anaconda.com/products/individual> in your web browser.
2.  Download the Anaconda Python 3 installer for macOS.
    These instructions assume that you use the graphical installer `.pkg` file.
3.  Follow the Anaconda Python 3 installation instructions.
    Make sure that the install location is set to "Install only for me"
    so Anaconda will install its files locally, relative to your home directory.
    Installing the software for all users tends to create problems in the long run
    and should be avoided.
4.  Verify the installation:
    click the Launchpad icon in the Dock, type Terminal in the search field, then click Terminal.
    A window should pop up where you can now type commands
    such as checking your conda installation with:

    ~~~
    conda --help
    ~~~
    {: .language-bash}

#### Video Tutorial

<div class="yt-wrapper2">
<div class="yt-wrapper">
<iframe type="text/html" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" src="https://www.youtube-nocookie.com/embed/TcSAln46u9U?modestbranding=1&playsinline=1&iv_load_policy=3&rel=0" class="yt-frame" allowfullscreen></iframe>
</div>
</div>
</article>

<article role="tabpanel" class="tab-pane" id="anaconda-linux">
Note that the following installation steps require you to work from the terminal (shell).
If you run into any difficulties, please request help before the workshop begins.

1.  Open <https://www.anaconda.com/products/individual> in your web browser.
2.  Download the Anaconda Python 3 installer for Linux.
3.  Install Anaconda using all of the defaults for installation.
    * Open a terminal window.
    * Navigate to the folder where you downloaded the installer.
    * Type `bash Anaconda3-` and press <kbd>Tab</kbd>.
      The name of the file you just downloaded should appear.
    * Press <kbd>Return</kbd>
    * Follow the text-only prompts.  When the license agreement appears (a colon
      will be present at the bottom of the screen) press <kbd>Spacebar</kbd> until you see the
      bottom of the text. Type `yes` and press <kbd>Return</kbd> to approve the license. Press
      <kbd>Return</kbd> again to approve the default location for the files. Type `yes` and
      press <kbd>Return</kbd> to prepend Anaconda to your `PATH` (this makes the Anaconda
      distribution your user's default Python).
4.  Verify the installation:
    this depends a bit on your Linux distribution, but often you will have an Applications listing
    in which you can select a Terminal icon you can click. A window should pop up where you can now
    type commands such as checking your conda installation with:

    ~~~
    conda --help
    ~~~
    {: .language-bash}

</article>
</div>
</div>

[anaconda]: https://www.anaconda.com/
[jupyter]: https://jupyter.org/
[python]: https://www.python.org/


## Required Python Packages

The following are packages needed for this workshop:

* [Pandas](https://pandas.pydata.org/)
* [Jupyter notebook](https://jupyter.org/)
* [Numpy](https://numpy.org/)
* [Matplotlib](https://matplotlib.org/)
* [Plotnine](https://plotnine.readthedocs.io/en/stable/)

All packages apart from `plotnine` will have automatically been installed with Anaconda
and we can use Anaconda as a package manager to install the missing `plotnine` package:
You need to open up a *Terminal*, if you are using Mac OSX, or Linux (see instructions above),
or launch an *anaconda-promt*, if you are using Windows. In your terminal window type the following:

~~~
conda install -y -c conda-forge plotnine
~~~
{: .language-bash}

This will then install the latest version of plotnine into your conda environment.

## Required packages: Miniconda

Miniconda is a lightweight version of Anaconda. If you install Miniconda instead of Anaconda,
you need to install required packages manually in the following way:
~~~
conda install -y numpy pandas matplotlib jupyter
conda install -c conda-forge plotnine
~~~
{: .language-bash}

### _(Alternative)_ Installing required packages with environment file
Download the
[environment.yml](https://raw.githubusercontent.com/datacarpentry/python-ecology-lesson/gh-pages/environment.yml)
file by right-clicking the link and selecting save as.
In the directory where you downloaded the environment.yml file run:

~~~
conda env create -f environment.yml
~~~
{: .language-bash}

Activate the new environment with:
~~~
conda activate python-ecology-lesson
~~~
{: .language-bash}

You can deactivate the environment with:
~~~
conda deactivate
~~~
{: .language-bash}

## Launch a Jupyter notebook

After installing either Anaconda or Miniconda and the workshop packages,
launch a Jupyter notebook by typing this command from the terminal:

~~~
jupyter notebook
~~~
{: .language-bash}

The notebook should open automatically in your browser. If it does not or you
wish to use a different browser, open this link: <http://localhost:8888>.

For a brief introduction to Jupyter Notebooks, please consult our
[Introduction to Jupyter Notebooks](.{% link _extras/jupyter_notebooks.md %}) page.

Please check the "Setup" page of
[the lesson site]({{ site.incubator_lesson_site }}) for instructions to follow
to obtain the software and data you will need to follow the lesson.
{% endif %}
