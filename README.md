# Drupal 8 Avatar Maker Demo
## What it Does
This module creates a content type called "Avatar", which allows you to control the output of inline SVG elements,change
colors, and apply animation to the resulting graphic.
## Requirements
Drupal 8
## How to Install it
Download the `master` branch from repo as a .zip file, unzip it, rename the unzipped directory `avatar`, and place it 
in `modules/custom/` within your Drupal site structure. After that you can go to the `NAME-OF-YOUR-SITE/admin/modules` page on your Drupal 
site and find **Avatar Maker Module** in the list, check the box, and click **Install** at the bottom of the page.

Or you can navigate to the directory using a CLI. Navigate to the root of your Drupal site. Navigate into the custom 
module folder `cd modules/custom`, and then clone the repo into the directory using git `git@github.com:ahorn-ucd/drupal-avatar.git avatar`.
Now you can go to the **Extend** admin page and enable it or enable it via Drush `drush pm-install avatar -y`.
## Create an Avatar
1. Go to `/node/add` on your site and choose **Avatar**.
2. At the very least give it a name and choose a gender. Feel free to play with the other options.
3. Save and publish your work.
4. Check out what you created!
## How it works
So there are a few moving parts to make all of this work. 
### Inline SVG
First I created all my avatar shapes, items, and head ware in Adobe Illustrator and exported the file as a `.svg`.
### Avatar Options
Second I created a content type called **Avatar** and created all my fields to add head ware, items, and some custom options.
### Theming with Twig
Third I opened my `.svg` file in a code editor and moved the `<svg>` element and all of it's contents to a twig template 
for my nodes full view mode. Once I had an inline svg in my template I was able to use twig conditional logic to make code
render, or not render, based on the user selected options. See `templates/node--avatar--full.html.twig`.
### Preprocessing
Fourth, since there is already a system for adding and removing classes from node templates using `hook_preprocess_node()`, 
I used this to add a modifier class for animation, and color based on the user selected settings. 
See `avatar.module`.
### CSS Colors and Animation
The colors and animation are added if the appropriate classes are added to the markup, allowing us to target elements within
the SVG element and make changes to element colors as well as animate them using CSS animations. See `dist/style.css`.
