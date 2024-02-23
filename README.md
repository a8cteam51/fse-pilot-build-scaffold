# FSE Pilot Project

Welcome to the scaffold for your pilot build, this readme will help you get setup in your development environment, though if you find you have questions that remain unanswered, please reach out to your Automattic contact.

## Setting up the Project

### Cloning

This scaffold is set up as a `/wp-content` root, that means you should clone this through `git` locally to be the `/wp-content` folder of your local install.

### Dependencies

This scaffold has composer dependencies, to install these, open a terminal in the `/wp-content` root and run `composer i`. See more about the scripts this makes available in the section **Code Style & Quality**.

Having run `composer i` you should also see the **Create Block Theme** plugin in your WP Plugins, you'll be using this plugin to sync FSE changes back to theme files.

### Build Processes

This scaffold will handle all build processes for you, this includes theme CSS, JS and custom Gutenberg blocks. To get setup open a terminal in the `/wp-content` root and run `npm i`.

After a successful install you can run `npm start` to being monitoring all files that will build. When your work is ready for QA you can run `npm run build` to create production ready versions of your files.

See all the available build and linting scripts available in `package.json`.

### Post Feeds Demo Data

To make building the post feeds easier, an XML file of post demo data including excerpts and Featured Images is included in this scaffold, see `thebaseplate.WordPress.xml`, import that to your install as a great timesaver. Media assets are available in the `post-assets` folder.

### Design

[Designs are available in Figma.](https://www.figma.com/file/eb7htmHX8L9k6od2qICj2k/%F0%9F%9B%A0%EF%B8%8F-FSE-Pilot-Build-Theme?type=design&node-id=3468-563&mode=design)

## Project Structure

The `git` repository only keeps track of **custom** content inside the `wp-content` directory. In general, that entails:

- the theme **or** child theme directory inside the `themes` directory
- the custom plugins inside the `plugins` directory
- the `mu-plugins` directory

As a rule of thumb, if there is another source of updates for a piece of code, it must not be tracked via the repository (e.g., off-the-shelf plugins or parent themes).

### FSE Templates, Parts, Patterns, and `theme.json`

FSE template parts are included in this to show desired folder structure only. You will likely want to start from scratch with all FSE related files to avoid battling what's already here and been filled as a placeholder demonstration only.

### Gutenberg blocks

The pilot scaffold contains a mu-plugin called `fse-pilot-blocks` which contains two blocks ready for this build. 

The first is a dummy form block you can use for creating the subscribe area in the site footer, this does not need to be functional and other than styling, you do not need to modify this block.

The second is a table of contents block, this is the only custom block that this pilot build will require. Modify this block and the block plugin in general how you see fit to acheive the correct functionality.

By separating the blocks from the theme into a mu-plugin, we can ensure that the blocks are always available on the site, even if the theme is changed (e.g., because of a future redesign or as part of the debugging process). Moreover, it forces us, as developers, to think about the blocks as a separate entity from the theme and to design the code as such thus making it easier to reuse them in other projects.

The mu-plugin must contain enough CSS for the block to be functional and not appear broken. All other styling can be held in the mu-plugin or the theme. [Seedlet is an example](https://github.com/Automattic/themes/tree/trunk/seedlet/assets/sass/blocks) of a theme providing its own styling for the blocks.

## Code Style & Quality

This project uses PHP CodeSniffer for linting PHP files and the wrappers provided by `@wordpress/scripts` for linting JS/TS and CSS/SCSS files. You can find the scripts for linting and formatting PHP in the `composer.json` file and the scripts for linting and formatting JS/TS and CSS/SCSS in the `package.json` file.

While JS/TS/CSS/SCSS linting should be configuration-free (using the defaults provided by `@wordpress/scripts`), the PHP linting requires a configuration file called `phpcs.xml.dist` which is located [in the Composer dependency `a8cteam51/team51-configs`](https://github.com/a8cteam51/team51-configs). Ensure you have run `composer i` to pull down this dependency.

Moreover, you will likely notice `.phpcs.xml` files sprinkled throughout the project (e.g., in the child theme and in the features plugin). These files are used to enhance the default configuration provided by the centralized `phpcs.xml.dist` file for the files inside the respective folders. For example, they add checks for using the correct text domain for the theme and the features plugin, respectively, or for using the correct prefixes for global variables.

---

_Media assets are AI-generated, except `block-theme-test-project-image-5.jpg', which is a photo by Nik on <a href="https://unsplash.com/photos/selective-focus-photography-of-blue-lego-minifigure-l4ADb9OVqTY?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>._
