## OSY-Site

This is the repository for the Old School Yoga website. The site is built using Jekyll, but at present is not using a packaged theme. The structure and styles are built along with the content in this repository. That may change in the future. This readme documents how the site works.

### Main Featues

- Incorporates the W3.CSS Framework and themes
- Responsive - works equally well on a laptop ar mobile device
- 3-Panel layout. The content of each panel is configurable.
- Section layout - each section has a sidebar with its own table of contents
- Section index layout - filters posts for the section front page

#### 3-Panel Layout

The 3-Panel layout uses a collection to organize the contents for the panels.
```
collections_dir: osy
collections:
  panels:
    order:
      - idx-left.md
      - idx-mid.md
      - idx-right.md
```
The content for the panels is contained under the collections directory (osy) in the _panels subdirectory. There can be any number of documents in the _panels directory. The configuration determines which panels are rendered.

The 3-Panel layout is coded to link each panel to a page. To accomplish this, each panel document must contain a title key, which serves as the link text, and a home key, which is the link url. This can be disabled by simply leaving out the home key.

The 3-Panel layout also accept an image, which displays centered above the panel contents and links to same page as title. To place an image on the panel, in the front matter you must include an image key with the url of the image, and an alt-text key.

#### Section Layout

Sections are designed to link to multiple related documents. Each section has its own folder under the root directory, which contains all the documents for that section. Data for the sidebar links is contained in contents.yml under the _data directory.
```
section-1:
  articles:
    - link-text: Section-1 Home
      url: /section-1/welcome.html
    - link-text: Page S1
      url: /section-1/page-s1.html
section-2:
  articles:
    - link-text: Section-2 Home
      url: /section-2/welcome.html
    - link-text: Page S2
      url: /section-2/page-s1.html
```
Each document appearing in a section must have front matter keys:
- layout: section
- category:
- title:

#### Section-index Layout

The section-index layout is designed for the section front page. In addition to the same table of contents as the section layout, It displays posts filtered for this page. To accomplish this, the section index page and all posts intended to be displyed there must have identical category keys in the front matter. The _posts directory is under the collections directory (osy). If desired, separate folders can be maintained for each category, with a _posts directory placed under each category folder.