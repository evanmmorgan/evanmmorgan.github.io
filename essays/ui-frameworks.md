---
layout: essay
type: essay
title: "Twelve Columns and a Lot of Class Names"
# All dates must be YYYY-MM-DD format!
date: 2026-10-10
published: true
labels:
  - Software Engineering
  - Bootstrap 5
  - UI Frameworks
---

<img width="600px" class="rounded" src="../img/ui-frameworks/with-without-bootstrap.png" alt="The same page built with plain HTML and CSS (left) and with Bootstrap 5 (right)">

*The same page built twice: plain HTML and CSS on the left, Bootstrap 5 on the right.*

## The first hour is miserable

The first time you open the Bootstrap 5 documentation, it feels like you signed up to learn a second language. There are containers, rows, and columns. There are breakpoints called `sm`, `md`, `lg`, `xl`, and `xxl`. There are spacing classes like `mt-3`, `px-2`, and `gy-4`, and you have to memorize what each letter and number means before you can center a box on the screen.

My first attempt at rebuilding an existing website with Bootstrap took me well over an hour, and most of that time went into reading docs and guessing which class did what. I knew how to write a `div` and give it a margin. Why should I learn a whole vocabulary of class names to do the same thing?

That question is fair. It took a few more weeks of practice before I had an answer I believed.

## What raw CSS asks of you

Here is a simple layout most sites need: two columns side by side on a laptop, stacked on a phone. In plain CSS, you write something like this:

```css
.container {
  max-width: 1140px;
  margin: 0 auto;
  padding: 0 12px;
}
.row {
  display: flex;
  flex-wrap: wrap;
}
.col-half {
  flex: 0 0 100%;
}
@media (min-width: 768px) {
  .col-half {
    flex: 0 0 50%;
  }
}
```

That works. Now you need a three-column section. Then a navbar that collapses into a menu button on small screens. Then a form, a card grid, and buttons that look the same on every page. Each one is another block of CSS you write, test on several screen sizes, and debug when a teammate's change breaks it.

Here is the same two-column layout in Bootstrap 5:

```html
<div class="container">
  <div class="row">
    <div class="col-md-6">Left side</div>
    <div class="col-md-6">Right side</div>
  </div>
</div>
```

You write no CSS at all. The `md` means "side by side from 768 pixels and up," and the `6` means "take half of the 12-column grid." Once you know that rule, you know how to build every grid on the site.

## What you get back for the time

### Speed after the learning curve

The learning cost is real, but you pay it once. After a few practice sessions, I could rebuild a page layout in a fraction of the time it took me the first day. Most of that gain came from the grid, the navbar component, and the spacing utilities. I stopped writing media queries by hand and started reading layouts as rows and columns.

### Pages that work on phones by default

More than half of web traffic now comes from mobile devices. With raw CSS, responsive design is extra work you must remember to do. With Bootstrap, it is the default. A navbar built with the `navbar-expand-lg` class collapses into a toggle button on small screens without any JavaScript you write yourself.

### A shared language for a team

This is the software engineering benefit that matters most to me. If five people write their own CSS, you end up with five naming styles, three slightly different shades of blue, and buttons that change size from page to page. If those five people use Bootstrap, a new teammate can read `class="btn btn-primary mt-3"` and know exactly what it does. The framework acts as a coding standard for the visual layer, the same way ESLint acts as a coding standard for JavaScript.

### Fewer browser bugs

Bootstrap has been around since 2011 and is used on millions of sites. Its maintainers have already found and fixed the odd cases where Safari, Chrome, and Firefox disagree. When you write raw CSS, you find those cases yourself, usually the night before a deadline.

## What it costs you

A framework is not free, and you should go in knowing the tradeoffs.

**Your site looks like other Bootstrap sites.** The default buttons, cards, and navbars are easy to recognize. If you don't customize colors and fonts, your project will look like a template.

**You can lose touch with CSS.** It is possible to use Bootstrap for months without understanding flexbox. When something breaks and no class fixes it, you still need to know what the framework is doing underneath.

**You ship code you don't use.** The full minified Bootstrap stylesheet is around 30 KB after compression. For a small personal page, most of that goes unused.

**Your HTML gets noisy.** A single element can carry eight or ten class names. That is easy to write and harder to read later.

## A word on other frameworks

Bootstrap is one choice among several. Semantic UI took a different approach, with class names written like English phrases, such as `ui large blue button`. That reads well, but the project has seen little development since its last major release in 2018, and a community fork called Fomantic UI now carries it forward. Tailwind CSS goes the other direction and gives you only small utility classes, with no ready-made components. You get more control over the look, and you write even more class names.

The right pick depends on your project. For a team of students who need a working, responsive web app in a few weeks, Bootstrap's ready-made components and huge documentation base make it a safe choice. For a design-heavy site where the look is the product, Tailwind or hand-written CSS might serve you better.

## So is it worth it?

Yes, with one condition: learn enough CSS to understand what the framework does for you. Bootstrap saves you from rewriting the same grid, navbar, and form styles on every project. It gives your team one shared set of rules. It makes mobile support the default instead of an afterthought.

The frustration of the first week is real. But compare one week of learning class names against writing and maintaining your own responsive layout code for every project you build. The framework wins that trade for most web apps.

---

*AI usage: This essay was written using Claude (Anthropic), an AI assistant, based on the assignment prompt. I reviewed and edited the result before publishing.*
