## OSY-Site

This is the repository for the Old School Yoga website. The site is built using Jekyll, but at present is not using a packaged theme. The structure and styles are contained in the repository along with the content. That may change in the future. This readme documents how the site works.

### Main Featues

- Incorporates the W3.CSS Framework and themes
- Responsive - works equally well on a laptop ar mobile device
- 3-Panel layout. The content of each panel is configurable.
- Section layout - each section has a sidebar with its own table of contents
- Section index layout - filters posts for the section front page

#### 3-Panel Layout

The 3-Panel layout uses the panels collection to organize the contents for the panels.
```
collections_dir: osy
collections:
  panels:
    order:
      - idx-left.md
      - idx-mid.md
      - idx-right.md
```
The content for the panels is contained in the osy/_panels directory. There can be any number of documents in the _panels directory. The configuration determines which panels are rendered and where they are rendered, left, middle, or right.

Each panel in the 3-panel layout links to a section-index page, that is the welcome page and navigation to the section contents. For this to work, each panel document must contain a title key and a home key, which is the url to the section-index page. They may also contain image and alt-text keys for the image url and alt-text to be displayed in the panel. 

Panels can link to anything you like or nothing at all. If you were to create another layout with panels, each new panel needs to be assigend to a spot in the order array. In the example above the 3 panels are assigned to slots 0, 1, and two. Additional panels would start at 3, 4, etc. Any content  in the _panels directory can be assigned to any panel, or panels. 

#### Section Layout

Sections are designed to link to multiple related documents. Each section has its own folder under the root directory, which contains all the documents for that section. Data for the navigation is contained in _data/contents.yml . The navigation may appear in the sidebar on large screens, or by clicking a menu icon on mobile.
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
Each document appearing in a section must have these front matter keys:
- layout: section
- category: yoga
- title: Asta Anga (8 Limbs) Yoga

#### Section-index Layout

The section-index layout is designed for the section front page. In addition to the same table of contents as the section layout, It displays posts filtered by section. To accomplish this, the section index page and all posts intended to be displyed there must have identical category keys in the front matter. The _posts directory is under the collections directory (osy). If desired, separate folders can be maintained for each category, with a _posts directory placed under each category folder.