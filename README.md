# lalatechnology.github.io

[Github Pages](https://docs.github.com/en/pages/quickstart)

`gh-pages` branch is sampling `minima` theme and all the code is under `/docs` folder. Folders and files in the root are a placeholders and should be removed (shortly).

Site is configured to deploy from `gh-pages` branch and `/docs` folder.

All the deployable content is under `_site` folder.

To test the site locally run command below in the terminal from the `/docs` folder
```
bundle exec jekyll serve
```
Terminal will show the url site is available on, `http://127.0.0.1:4000/` and how to stop the server.

If you want to see draft blogs, add `--drafts` flag to the command above.

All the changes you do to files will be immediately avialbe in the browser. However, to see config changes you would need to restart the server.

`index.md` contains all the info for the `Home` page.

`about.md` - `About` page under `About` tab.

`contact.md` - `Contact Us` page under `Contact Us` tab.

`_layouts/default.html` is the defulat (index) `html` file that glues all parts of the pages together. Keep in mind that there is default implementation of the `minima` theme and we only need to overwrite the files that require customization:

- `_layouts/home.html` is the `Home` or `index` page. Since `header`, `footer` and `navigation bar` are referenced on the `_layouts/default.html` page, `_layouts/home.html` defines the layout of the content. The actual `Home` content is in the `index.md` file.
- `_layouts/posts.html` is the base page for all the blogs listed in chronological order. To add `Blogs` navigational item, I had to create `Blogs.md` file with an empty content (unlike `About.md` and `Contact.md`).
- `_includes/header.html` is the page that defines how navigation bar should look like. It picks the menu items from the `permalink` property defined in corresponding `.md` file.

Blogs should appear under the separate `Blogs` menu item. `Blogs` page shoes the list of all the blogs posted in the `_posts` folder. All draft blogs are located under `_drafts` folder and only visible in development.