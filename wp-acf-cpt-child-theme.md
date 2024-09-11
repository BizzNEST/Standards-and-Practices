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

### Pre-requisite
1. Install Spectra-One Plugin
2. An IDE of your choice (VS code)
3. Install ACF plugin or CPT UI plugin
4. Install Meta Field Block
5. Install WP Code (or any other plugin that allows you to input shortcode)

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

### Custom Post Type (CPT)

Use custom post types in WordPress when you need to organize and manage different kinds of content beyond the default post and page types. Here are some situations where custom post types are useful:

1. **Specialized Content Structures:** If your site needs specific content that doesn’t fit the traditional blog post or page format (e.g., portfolio items, testimonials, team members, products), custom post types let you create a tailored structure for that content.

2. **Improved Organization:** Custom post types allow you to better categorize and display distinct content types. For example, you could have separate sections for “Projects,” “Events,” or “Services,” keeping them isolated from regular blog posts or pages.

3. **Better User Experience:** Custom post types improve the backend editing experience by simplifying the workflow for users. For instance, having a separate “Recipes” post type with custom fields for ingredients and cooking steps makes it easier to input and manage recipes.

4. **Custom Templates:** Custom post types let you apply custom templates and layouts for different types of content, allowing more design flexibility without affecting the rest of your site.

5. **Functionality Expansion:** Plugins like WooCommerce or other directory plugins often create custom post types for things like products or listings. You can create your own custom post types for similar use cases when building specific functionality.


> \[!NOTE]\
> There are many ways to create CPTs, but today we will create them through the ACF plugin

#### Creating A CPT

1. Into your ACF plugin go under the Post Types navigation and fill out the information
- Parent Template: Think of how you want to break up the general CPT (Like having a Book CPT, but you wanted a child Chapter CPTs, or if you Project CPT, needs a Phase CPT (Indicating the phases of the project))
- Fill out the rest of the information (ex. CPT name, unique key, ...etc)

![image](https://github.com/user-attachments/assets/29ef11ba-6369-4547-a7d7-d05ed29fd103)

2. Under the advanced tab you can also see what customization you'd like for this. For this project in particular I'm not going to include an editor
   - There's also more customization to explore like proper REST API standards.
  
![image](https://github.com/user-attachments/assets/f11bd2aa-8c74-486f-805b-86d8c6ee38e5)

3. There you go! You made a CPT. You can now use the add new button to create, and you can view all the posts under that CPT.

![image](https://github.com/user-attachments/assets/fc9285a0-a468-409b-be1f-6a4fc42681df)

### Advanced Custom Field (ACF)

You'd want to use Advanced Custom Fields (ACF) in WordPress when you need more control over the way content is managed, displayed, and structured within custom post types, pages, or even default post types. Here are some situations where ACF is useful:

1. **Custom Data Entry Fields:** If your site requires complex or structured data input (e.g., contact details, event dates, image galleries), ACF allows you to create custom fields that make it easy for content creators to add structured data without requiring them to mess with HTML or shortcodes.

2. **Tailored Content Presentation:** When you need specific layouts or sections for different pages or post types (e.g., testimonials, FAQs, team member profiles), ACF helps you create custom fields for text, images, links, and other media, so the content displays exactly how you want it.

3. **Extending Custom Post Types:** When you use custom post types (e.g., "Projects," "Products," or "Portfolio"), ACF enables you to attach extra fields like descriptions, tools used, ratings, links, and more to provide more detailed and structured information.

4. **Simplifying Content Management:** ACF allows you to define fields in the admin that correspond to specific areas in your theme. This means users can easily fill out content (like headlines, feature images, or text sections) without needing to understand how the theme works or write custom HTML.

5. **Reusable Content Blocks:** If your site uses repeatable content blocks or needs flexible layouts (e.g., for landing pages, services, or case studies), ACF lets you create groups of fields and repeat them as needed, giving your site editors flexibility.

6. **Creating User-Friendly Admin Interfaces:** ACF lets you design custom back-end experiences for non-technical users. With options like dropdowns, checkboxes, date pickers, and relationship fields, you can make the content editing experience intuitive for users who aren’t familiar with WordPress code.

7. **Custom Fields for Taxonomies:** ACF also allows adding custom fields to taxonomies (e.g., categories or tags), giving you more control over how taxonomies are used and displayed on the front end.

8. **Dynamic Data Display:** When you need to display dynamic data in templates (e.g., related posts, custom metadata, or conditional content), ACF makes it easy to output that data in a structured way, based on how fields are configured in the admin.

#### Creating an ACF

1. Navigate through the ACF plugin, and add a new field group (for this project, I added, `project_description`, `project_link`, and `project_tools`)

![image](https://github.com/user-attachments/assets/346e0826-8400-413b-b82a-76a48df8a17c)

2. Make sure to hook the fields to the right post type, page, taxonomy, ...etc.

![image](https://github.com/user-attachments/assets/f4c161d9-ada9-4910-9192-8a5c1228ffea)

3. Congrats you've made ACFs for your Posts! You can view it at the bottom of the editor, or if you didn't include an editor to your post types they should be displated in the admin dashboard like below.

![image](https://github.com/user-attachments/assets/5aa356a7-7f28-413c-88dc-2e46dc082ce9)

4. Display ACFs can be done by installing plugins (Meta Field Block plugin), and in the WPE editor hook the field ids to the post

> \[!WARNING]\
> ACF Pro has a setting to have more customization, but since we have the free version, we'd need to install a plugin to display the ACFs. This plugin only displays the text of the ACF, and quickly you'll start to realize that you need a more custom solution (ex. having a link be a button instead of a text), and you'll have to rely on short codes for that

#### In WPE Editor

![image](https://github.com/user-attachments/assets/949ac71c-3820-4794-982a-de7ffb346edb)

#### Page displaying the ACFs

![image](https://github.com/user-attachments/assets/60fd8d92-903e-4091-84f9-e6c01c773efc)

### Short Code

Use shortcodes in WordPress when you need a simple way to add dynamic or complex content into posts, pages, or widgets. Here are some situations where shortcodes are useful:

1. **Reusable Dynamic Content:** If you have a piece of content or functionality that you want to reuse across different posts or pages (e.g., embedding forms, buttons, maps, or custom queries), shortcodes allow you to insert that content using a simple [shortcode] instead of duplicating code.

2. **Custom Features in Posts or Pages:** When you need to include custom features, such as galleries, contact forms, sliders, or any other interactive elements within posts or pages, shortcodes provide a user-friendly way for editors to do this without knowing code.

3. **Embedding External Content:** You can use shortcodes to embed third-party content like YouTube videos, social media posts, or external forms. Plugins often provide shortcodes to make embedding easy for site administrators.

4. **Simplifying Complex Layouts:** Shortcodes allow you to wrap complex HTML structures into simple tags. For example, if you’re building grid layouts or displaying multiple columns on a page, shortcodes make it easier for non-technical users to manage complex layouts.

5. **Custom Post Type Display:** Shortcodes can be used to display lists or specific content from custom post types dynamically (e.g., a list of recent projects, a slider for testimonials, or product grids). This is useful when you need to show custom post type content in various parts of your site.

6. **Plugin Integration:** Many WordPress plugins offer shortcodes for adding functionality to pages or posts (e.g., WooCommerce product grids, forms from Contact Form 7, or newsletter subscription forms). Using shortcodes allows you to easily integrate these features without writing custom code.

7. **Conditional Content Display:** Shortcodes can also be written to display content conditionally based on certain criteria, like user roles, logged-in status, or custom field values.

8. **Custom Queries:** If you need to display specific posts or custom content based on certain criteria (e.g., showing posts from a certain category or tag), shortcodes allow you to easily write custom queries and display that content without manually altering theme files.


