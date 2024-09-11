# Intro to Child Themes, CPTs, ACFs, and Short Code

## Purpose of this Document

- An Introduction to Child Themes, Custom Post Types (CPT), Advanced Custom Fields (ACF), and Short Code
- Common practices and how / when to use these.

## Summary

- Create a Child Theme to write custom code to the theme files. (Do this at the start of every project to prevent theme conflicts)
- Use Custom Post Type (CPT) to manage and organize different kinds of content beyond post and pages. (CPT Plugin or ACF plugin)
- Use Advanced Custom Fields (ACF) when you need more control over the way content is managed, displayed, and structured within custom post types, pages, or even default post types. (Use ACF plugin)
- Use shortcodes in when you need a simple way to add dynamic or complex custom content into posts, pages, or widgets. (This can be done in writing in theme files or plugins)


> \[!NOTE]\
> **Small disclaimer:** This is a basic overview of these tools, to learn more about this content, feel free to explore WP API + Other common practices, and make a PR to add on to this document.

### Child Themes

The purpose of a child theme in WordPress is to allow you to modify or add functionality to an existing theme (the parent theme) without directly altering its code. Child themes are essential for maintaining customizations when the parent theme is updated, ensuring that your changes aren’t lost.

> \[!WARNING]\
> It’s best to create a child theme at the start of your web development project because, if you’ve already made modifications to theme files—such as through the theme editor in WordPress—there’s a strong possibility that those changes will be lost during theme updates.

#### When to use Child Themes
- Preserving Customizations During Updates
- Customizing Themes Without Breaking Core Features
- Experimenting and Learning
- Overriding Specific Files or Features
- Custom Styling
- Adding New Functionality
- Keeping Parent Theme Features
- Collaboration or Customization Requests

#### When not to use Child Themes
- If your modifications are minimal (e.g., only a few CSS tweaks) use a plugin.
- If you want to make deep customizations and the parent theme isn’t well-suited to your needs, building a custom theme from scratch might be a better approach.

> \[!NOTE]\
> If you are unsure if a project needs custom / complex solution. Then I still believe it doesn't hurt making a child theme.

#### Creating A Child Theme

1. Create a child theme directory in your theme folder (usually named `parent-theme-child`) and create a `functions.php` and `style.css` file.
   
![image](https://github.com/user-attachments/assets/8dde035f-ce5c-4460-b594-f18349d99eb7)

2. Enqueue parent styles into your `functions.php`

```php []
<?php
// Enqueue parent and child theme styles
function spectra_child_enqueue_styles() {
  // Enqueue parent theme styles
  wp_enqueue_style('parent-style', get_template_directory_uri() . '/style.css');
  
  // Enqueue child theme styles, making sure it's loaded after the parent styles
  wp_enqueue_style('child-style', get_stylesheet_directory_uri() . '/style.css', array('parent-style'), null);
}
```
3. Write the commented top portion (Theme Name, Template, Description, Author, and version), and import parent styles.

```css []
/*
Theme Name: Spectra One Child
Template: spectra-one
Description: A child theme for the Spectra One theme.
Author: Eli Manzo
Version: 1.0.0
*/

/* Import parent theme styles */
@import url("../spectra/style.css");

/* Add your custom styles below */
```

4. If it all works, then you can activate your theme in WordPress

![image](https://github.com/user-attachments/assets/f4fdfdfa-ed68-4cf2-a897-49545f17dff2)

