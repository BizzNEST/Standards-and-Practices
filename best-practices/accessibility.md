# Accessibility Best Practices

Accessibility (often shortened to **a11y**) means building websites and apps that everyone can use — including people who rely on screen readers, keyboard navigation, or other assistive technologies. Accessibility is not optional. It's a core part of building quality software.

---

## Why Accessibility Matters

- **It's the right thing to do.** Everyone deserves equal access to the web.
- **It's the law.** Many organizations are required to meet accessibility standards (ADA, Section 508, WCAG).
- **It improves the experience for everyone.** Good accessibility practices lead to cleaner HTML, better SEO, and a better experience for all users — not just those with disabilities.

---

## Fundamental Best Practices

### Use Semantic HTML

Semantic elements tell the browser (and assistive technologies) what your content means, not just how it looks.

> **DO**: Use `<button>` for clickable actions and `<a>` for navigation links.
>
> **DON'T**: Use `<div>` or `<span>` with click handlers to fake a button.

> **DO**: Use heading elements (`<h1>` through `<h6>`) in order to create a logical document outline.
>
> **DON'T**: Skip heading levels (e.g., jumping from `<h1>` to `<h4>`) or use headings just for styling.

> **DO**: Use `<nav>`, `<main>`, `<header>`, `<footer>`, and `<section>` to define page regions.
>
> **DON'T**: Build your entire layout out of `<div>` elements with no semantic meaning.

```html
<!-- BAD -->
<div class="button" onclick="submit()">Submit</div>

<!-- GOOD -->
<button type="submit">Submit</button>
```

### Provide Alt Text for Images

Screen readers read the `alt` attribute to describe images to users who can't see them.

> **DO**: Write alt text that describes what the image communicates, not what it looks like.
>
> **DON'T**: Leave the `alt` attribute empty on images that convey information.

> **DO**: Use an empty `alt=""` for purely decorative images (icons, backgrounds).
>
> **DON'T**: Write "image of" or "picture of" in alt text — the screen reader already announces it as an image.

```html
<!-- BAD — missing alt -->
<img src="team-photo.jpg">

<!-- BAD — unhelpful alt -->
<img src="team-photo.jpg" alt="image">

<!-- GOOD -->
<img src="team-photo.jpg" alt="BizzNEST team members at the 2025 summer hackathon">

<!-- GOOD — decorative image -->
<img src="decorative-line.svg" alt="">
```

### Keyboard Navigation

Many users navigate entirely with a keyboard. Every interactive element must be reachable and usable without a mouse.

> **DO**: Make sure all buttons, links, and form fields are reachable with the `Tab` key.
>
> **DON'T**: Remove the default focus outline (`outline: none`) without providing a visible alternative.

> **DO**: Use `tabindex="0"` if you need a non-interactive element to be focusable.
>
> **DON'T**: Use positive `tabindex` values (e.g., `tabindex="5"`) — they create confusing tab order.

> **DO**: Test your pages by putting your mouse away and navigating only with `Tab`, `Shift+Tab`, `Enter`, and `Space`.

### Color and Contrast

Not everyone sees colors the same way. Don't rely on color alone to communicate meaning.

> **DO**: Maintain a contrast ratio of at least **4.5:1** for normal text and **3:1** for large text (WCAG AA).
>
> **DON'T**: Use light gray text on a white background.

> **DO**: Use color **plus** another indicator (icon, underline, text label) to convey information.
>
> **DON'T**: Use only red/green to indicate success/failure — colorblind users may not distinguish them.

### Form Accessibility

Forms are where users interact most, and where accessibility mistakes cause the most frustration.

> **DO**: Associate every input with a `<label>` using the `for` attribute.
>
> **DON'T**: Use placeholder text as a substitute for labels — it disappears when the user starts typing.

> **DO**: Group related fields with `<fieldset>` and `<legend>`.
>
> **DON'T**: Leave form errors vague — tell the user exactly which field has a problem and how to fix it.

```html
<!-- BAD — no label -->
<input type="email" placeholder="Email">

<!-- GOOD -->
<label for="email">Email</label>
<input type="email" id="email" name="email">
```

### ARIA (When Necessary)

ARIA (Accessible Rich Internet Applications) attributes add accessibility information to elements that don't have it natively. Use them sparingly.

> **DO**: Use ARIA only when native HTML can't achieve the same result.
>
> **DON'T**: Add ARIA attributes to elements that already have built-in accessibility (e.g., don't add `role="button"` to a `<button>`).

> **DO**: Use `aria-label` to provide accessible names for elements that have no visible text.
>
> **DON'T**: Use `aria-label` on elements that already have visible text — it overrides the visible text for screen readers.

```html
<!-- GOOD — icon-only button needs an aria-label -->
<button aria-label="Close menu">
  <svg><!-- X icon --></svg>
</button>
```

---

## Using Lighthouse for Accessibility Audits

Lighthouse is built into Google Chrome DevTools and scores your page's accessibility from 0 to 100. Run it on every page you build.

### How to Run a Lighthouse Audit

1. Open your page in **Google Chrome**.
2. Open DevTools (`Cmd + Option + I` on Mac, `Ctrl + Shift + I` on Windows).
3. Click the **Lighthouse** tab.
4. Under **Categories**, check **Accessibility** (you can uncheck the others for a faster run).
5. Choose **Navigation** mode and your device type (Mobile or Desktop).
6. Click **Analyze page load**.

### Understanding the Results

- **Score 90–100**: Good. Minor improvements may be suggested.
- **Score 70–89**: Needs work. Review each failing audit and fix them.
- **Score below 70**: Significant issues. Prioritize fixing these before shipping.

Each issue includes:
- **What's wrong** — a description of the problem.
- **Why it matters** — how it affects users with disabilities.
- **How to fix it** — specific guidance and links to documentation.

### Common Lighthouse Accessibility Failures

| Issue | What It Means | How to Fix |
|---|---|---|
| Image elements do not have `[alt]` attributes | Screen readers can't describe the image | Add descriptive `alt` text |
| Form elements do not have associated labels | Screen readers can't identify the field | Add `<label>` with matching `for` attribute |
| Background and foreground colors do not have sufficient contrast ratio | Text is hard to read for low-vision users | Increase contrast to meet WCAG AA (4.5:1) |
| Links do not have a discernible name | Screen readers say "link" with no context | Add visible text or `aria-label` to links |
| Heading elements are not in a sequentially-descending order | Document outline is confusing for screen reader users | Fix heading levels to follow logical order |
| `[id]` attributes on active, focusable elements are not unique | Assistive tech may target the wrong element | Ensure all `id` values are unique |

### Tips for Using Lighthouse Effectively

- **Run it early and often.** Don't wait until the project is done — audit each page as you build it.
- **Test on both Mobile and Desktop.** Accessibility issues can differ between viewport sizes.
- **Lighthouse doesn't catch everything.** A score of 100 does not mean your site is fully accessible. Manual testing (keyboard navigation, screen reader testing) is still necessary.
- **Use it alongside other tools.** Try the [axe DevTools extension](https://www.deque.com/axe/devtools/) for more detailed audits.

---

## Accessibility Checklist

Use this checklist before submitting a PR:

- [ ] All images have meaningful `alt` text (or `alt=""` for decorative images)
- [ ] All form inputs have associated `<label>` elements
- [ ] Page has a logical heading hierarchy (`h1` → `h2` → `h3`, no skipped levels)
- [ ] All interactive elements are reachable and usable with keyboard only
- [ ] Color contrast meets WCAG AA standards (4.5:1 for normal text)
- [ ] Color is not the only way information is communicated
- [ ] Focus styles are visible on all interactive elements
- [ ] Page uses semantic HTML (`<nav>`, `<main>`, `<button>`, etc.)
- [ ] Lighthouse accessibility score is 90 or above
- [ ] Manually tested keyboard navigation (Tab through the full page)

---

## Resources

- [WCAG 2.1 Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/) — the official guidelines
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) — check your color contrast ratios
- [axe DevTools](https://www.deque.com/axe/devtools/) — browser extension for detailed accessibility audits
- [The A11Y Project](https://www.a11yproject.com/) — community-driven accessibility resource
