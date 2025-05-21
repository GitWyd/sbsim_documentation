# SBSIM Documentation - Contributing Guide
You can view the [SBSIM Documentation](https://gitwyd.github.io/sbsim_documentation/) by visiting the following link: [https://gitwyd.github.io/sbsim_documentation/](https://gitwyd.github.io/sbsim_documentation/).

This document outlines how to contribute to the SBSIM Documentation, which is built using Jekyll and the "Just the Docs" theme, and hosted on GitHub Pages.

## Documentation Structure

The documentation is organized as follows:

* **`_config.yml`**: Contains global Jekyll configuration settings, including the theme (`just-the-docs`), site title, description, logo, navigation settings (e.g., `nav_enabled`, `search_enabled`), and search parameters.
* **`index.md`**: The main landing page of the documentation. It uses front matter to define its title and navigation order.
* **`docs/` directory**: Contains all the individual documentation pages in Markdown format (`.md`).
    * Subdirectories within `docs/` can be used to organize content into logical sections (e.g., `reinforcement-learning-module/`).
* **`.github/workflows/`**: Contains GitHub Actions workflows.
    * `ci.yml`: Defines the Continuous Integration process, which includes checking out the code, setting up Ruby, and building the Jekyll site.
    * `pages.yml`: Defines the workflow for building and deploying the Jekyll site to GitHub Pages. This includes setting permissions, configuring pages, building with Jekyll (including `JEKYLL_ENV: production`), and uploading the artifact for deployment.
* **`.github/dependabot.yml`**: Configures Dependabot for automatic dependency updates (e.g., for Bundler).

## Adding New Documentation Pages

1.  **Create a new Markdown file**:
    * Place your new `.md` file in the `docs/` directory or an appropriate subdirectory.
    * Use descriptive filenames (e.g., `new-feature.md`).

2.  **Add Front Matter**:
    * At the top of your Markdown file, include YAML front matter to control its title, navigation order, and position in the hierarchy.
    * **Required fields**:
        * `layout: "default"`: Specifies the page layout.
        * `title: "Your Page Title"`: The title that will appear in the navigation and at the top of the page.
    * **Navigation fields**:
        * `nav_order: <number>`: A number that determines the order of the page in the navigation menu relative to its siblings. Lower numbers appear first. (e.g., `nav_order: 3`)
        * `parent: "Parent Page Title"`: The title of the parent page in the navigation hierarchy. This makes the current page a child of the specified parent. (e.g., `parent: "Reward Functions"`)
        * `grand_parent: "Grandparent Page Title"`: The title of the grandparent page, if you have a deeper level of nesting. (e.g., `grand_parent: "Smart Control Project Documentation"`)
        * `has_children: true`: If this page should act as a parent for other pages that will be nested under it. (e.g., `has_children: true` on `docs/simulation-components.md`)

    **Example Front Matter:**
    ```yaml
    ---
    layout: "default"
    title: "My New Feature"
    nav_order: 5
    parent: "Simulation Components"
    grand_parent: "Smart Control Project Documentation"
    ---
    ```

3.  **Write Content**:
    * Write your documentation content using Markdown syntax.
    * You can include links to other pages, images, code blocks, etc.
    * Ensure internal links are relative, for example: `[Back to Home](../index.md)` or `[Back to Reinforcement Learning]({% link docs/reinforcement-learning-module.md %})`.

## Changing the Navigation Order and Hierarchy

The navigation order and hierarchy are controlled by the `nav_order`, `parent`, and `grand_parent` front matter parameters in each Markdown file.

* **To change the order of pages at the same level**:
    * Modify the `nav_order` value in the front matter of the respective files. Pages are sorted in ascending order based on this value.
    * For example, a page with `nav_order: 1` will appear before a page with `nav_order: 2` under the same parent.

* **To move a page under a different parent**:
    * Change the `parent: "New Parent Page Title"` value in the page's front matter.
    * If necessary, also update `grand_parent` if the new parent is itself nested.

* **To create a new top-level section that can have children**:
    1.  Create an `.md` file for the new top-level section (e.g., `docs/new-main-section.md`).
    2.  In its front matter, set `parent: "Smart Control Project Documentation"` (i.e., the root `title` in `index.md`).
    3.  Add `has_children: true` to its front matter.
    4.  Assign it a `nav_order`.
    5.  For child pages, set `parent: "New Main Section Title"` (matching the title of your new top-level section file).

## Building and Previewing Locally (Recommended)

Before pushing changes, it's good practice to build and preview the site locally to ensure your changes look correct and links are working.

1.  **Install Jekyll and Bundler**: Follow the instructions on the [Jekyll website](https://jekyllrb.com/docs/installation/) and the [Just the Docs theme documentation](https://just-the-docs.github.io/just-the-docs/docs/installation/).
2.  **Navigate to the repository root**.
3.  **Install dependencies**: `bundle install`
4.  **Serve the site**: `bundle exec jekyll serve`
5.  Open your browser to `http://localhost:4000` (or the address shown in the terminal).

## Committing and Pushing Changes

1.  Once you are satisfied with your changes, commit them to your local Git repository with a clear commit message.
2.  Push your changes to the `main` branch (or submit a Pull Request if you are working on a fork or feature branch).
3.  The GitHub Actions workflow (`.github/workflows/pages.yml`) will automatically build and deploy the updated documentation to GitHub Pages.

## Theme and Global Settings

* The documentation uses the `just-the-docs` theme, as specified in `_config.yml` (`remote_theme: just-the-docs/just-the-docs`).
* Other global settings like site `title`, `description`, `logo`, `favicon_ico`, and search behavior (`search_enabled`, `search.heading_level`, etc.) are also configured in `_config.yml`.
* The site search can be focused by pressing `ctrl + k` (or `cmd + k` on macOS).
