# Indenta

An attempt to fix the indentation of the first paragraph in typst.

It works.

## Usage

```typst
#set par(first-line-indent: 2em)
#import "@preview/indenta:0.0.2": fix-indent
#show: fix-indent()

```

## Demo

![image](https://github.com/flaribbit/indenta/assets/24885181/874df696-3277-4103-9166-a24639b0c7c6)

## Note

An empty line after heading is required for the fix to work. For example:

```typst
= Heading 1

First paragraph.
```

When you use `fix-indent()` with other show rules, make sure to call `fix-indent()` **after other show rules**. For example:

```typst
#show heading.where(level: 1): set text(size: 20pt)
#show: fix-indent()
```

This package is in very early stage and may not work as expected in some cases. Minor fixes will be made at any time but the package in typst universe may not be updated immediately. You can check the latest version on [GitHub](https://github.com/flaribbit/indenta) then copy and paste the code to your typst file.

If it still doesn't work as expected, you can try another solution (aka fake-par solution):

```typst
#let fakepar=context{box();v(-measure(block()+block()).height)}
#show heading: it=>it+fakepar
#show figure: it=>it+fakepar
#show math.equation: it=>it+fakepar
// ... other elements
```
