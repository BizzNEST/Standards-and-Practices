# Intro to ACFs, CPTs, Child Themes, and Short Code

## Purpose of this Document

- An Introduction to Advanced Custom Fields (ACF), Custom Post Types (CPT), Child Themes, and Short Code
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
