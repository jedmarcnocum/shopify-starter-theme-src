#### Shopify starter theme based on [Shopify Theme Lab](https://github.com/uicrooks/shopify-theme-lab) without CSS/JS libraries.

- This repo utilizes the mentioned repo above for the structure and build tools with slight modifications (removed Tailwind/Vue). You can install your chosen css/js framework, just follow the documentation of [Shopify Theme Lab](https://themelab.uicrooks.com/guide/css-frameworks.html).
- This repo also utilizes the separation of source and compiled codes in separate repositories using https://github.com/ingydotnet/git-subrepo for ease of development.



##### Example repository for source and compiled code:

Source repo 
(`shopify-starter-theme-src`) - source files goes here

Compiled repo: 
(`shopify-starter-theme-dist`) - compiled theme files. It lives inside the source repo under the folder name `dist`. This repository is connected to your Shopify store via [Shopify Github Integration](https://shopify.dev/themes/tools/github)

**Structure:**

```
.
├── dist       # connected branch via subrepo: shopify-starter-theme-dist
├── src        # source files
├── other files/tools/build/etc
└── README.md
```

Workflow:

1. Let's say the development starts with a feature branch named `slideshow`. This branch will be developed under your source repo. 
2. Once you're done developing the branch `slideshow`, you can now push the branch and create a PR on your source github repo (`shopify-starter-theme-src`). 
3. Once your feature branch is now merged to main/master, The next step is to push those changes to your compiled repo (`shopify-starter-theme-dist`) by executing the command: `git subrepo push dist --branch="branch_name_here"`. 
4. A new branch will be pushed on your compiled repo (`shopify-starter-theme-dist`), you can now do a PR and finalize stuff. Once the changes are merged to main/master, Shopify will pull those changes to the theme connected to your Shopify store. 

Note: I recommend to pull the changes on the compiled repo every time you develop under your source repo -- the reason for this is for your source repo to always fetch the latest changes made to the compiled repo (via shopify theme editor changes).

