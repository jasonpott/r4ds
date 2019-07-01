C4TS R-Club - Session 2
================
Jason Pott
30/06/2019

In our [first
session](https://github.com/jasonpott/r4ds/blob/master/01.%20Session%201%20/session_1.md)
we covered - Setting up our environment - installing packages -
introduction to ggplot - I gave an example of how to load a csv file
into R

Feel free to look back over the notes from that session, please come
back to me if you have any questions or need some clarification.

### Session 2

In this session we will work through some more useful ways of working in
R and Rstudio.

If you were not here last week the only prerequisite is to make your
Rstudio look like mine. Use the menus: Menu \> View \> Panes \> Pane
Layout, to acomplish this.

This week we will discuss: - Working in projects and why you should -
Getting data into R - Manipulating data - creating tables - passing
manipulated data to ggplot

## Projects in R and Rstudio

Why work in projects?

Projects are the first step in ensuring that your work is reproducible.
This is because each piece of analysis is wholly contained within a
folder which can be shared. Sharing a copy of your analysis as a project
means that it should run out of the box for other people regardless of
their system setup.

I have put together a folder template for you which you may find useful
for organising your projects. This is the suggested layout of analysis
projects by the [“data carpentry”
group](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510).

Please download the zip file from [this link]()

### Steps for project based working

  - Create a directory where you will store all your R analysis  
  - Copy and unzip the file you have just downloaded  
  - Name the folder - project template or something similar  
  - Open Rstudio  
  - File \> New Project  
  - If you have created a folder for your project choose existing
    directory, else select New directory.

When you want to work in your project navigate to the folder and open
the orijectname.Rproj

Final step - copy the contents of the template folder into your R
project folder. This is how you are going to structure data within your
project.

### Other helpful settings

Within your Rstudio general preferences make sure to deselect “Restore
.RData into workspace at startup”

If this option is selected each time that you log out of Rstudio the
data in your ctive R session will be saved to disk and loaded back in
next time. This can cause all sorts of problems. Whenever you are
running an analysis you always want to run from a fresh R session and
your code should be written so that there are no pre-requisites other
thant the objects and scripts that you have within your project folder.

![Important preference](Screenshot%202019-07-01%20at%2008.40.05.png)

## Importing data into R

The data types that we will cover here are: - csv - xls/xlsx

There are functions available to import data from SPSS files, SAS and
many other formats. If you have a specific file type that you would like
to import speak up and we can look for a function that serves your
purpose.

## Manipulating data

## Creating tables

## passing manipulated data to ggplot
