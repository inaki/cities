# Code for America 2015 Fellow Cities

![alt tag](https://raw.githubusercontent.com/inaki/cities/master/public/images/snapshot.png?token=AAdoq6kUUreX__04LAZwJvp7nZXZlDenks5UUZYKwA%3D%3D)

#### This project have the intention of gather information about the 2015 Fellow Cities.


We decide to do a simple jekyll site so everybody can contribute, coders and non-coders.
Here Content is the king, so the most important thing is that we get the most valuable information
about the Fellow Cities that will help us before and during the fellowship year. For us, as fellows
is important to know very well about the cities we'll have the opportunity to serve as well as the
cities that other fellows friends are working with so we can work together to get the most useful apps
for the people of this cities this year.

## jekyll site

#### Installing Jekyll

If you don't have jekyll installed, check out the [installation docs](http://jekyllrb.com/docs/installation/). 

Additionally, if you are running an older version of OSX, it's possible that you won't be able to build the site properly because your version of Ruby is too old. If this happens, you can try to [homebrew](http://brew.sh/) the new version of Ruby, and set your PATH to prioritize that one. (`export PATH=export PATH=/usr/local/bin:$PATH`)

#### Running the cities app

 1. **Fork** the repo
 2. **Download** to your local machine
 3. Open de **terminal**
 4. ``cd /path/to/repo``
 5. run: ```jekyll serve```
 6. Open your **web browser**  
 7. In the url bar enter ```localhost:4000```
 8. And *"Voilà!"*

## Editing the cities pages
**Editing**
 1. Open your **text editor** of preference.
 2. Look in the **root** of the project for the directories named after the cities.
 3. You will find a markdown doc called **index.md** inside.
 4. Edit the **index.md** file.
   a. If you are adding photos, links to data resources, or links to news pieces, you can edit the YAML on the top of the page. Just keep the formatting the same, and they will automatically appear properly.*
   b. If you are adding more detailed information, just edit the page directly with Markdown syntax.
 5. And make a **pull request** in github repo page.

## Resources
Here some very good resources related to this project.

- [Jekyll Official Website](http://jekyllrb.com/)
- [Markdown Basics](https://help.github.com/articles/markdown-basics/)
- [Jekyll Tutorial](https://www.youtube.com/watch?v=iWowJBRMtpc)

* Note on YAML: If your news article has quotes in quotes in quotes (see Indianapolis for an example), you'll have to give YAML the unicode character for a double quote, which is \u0022. Please refer to the Indy page for an example.
