# commit-comments

## HW2

### General
- Add README.md, LICENSE, possibly .gitignore.
- Folder structuring - this works good for me:
```
index.html
+ css
  - style.css
+ img
  - logo.img
```
- Use CSS reset files
- Don't use `<br>` tags or non-breaking spaces (`&nbsp;`) to separate things. Use margins instead.
- Format your CSS files cleanly:
```
.class#id {
  margin: 0 10px;
  border: 1px solid #000;
}

tag:nth-child(1) {
  padding: 15px;
}
```

### emer7/Homework-2
- What's with the tidle files? You might want to add an .gitignore for them
- Why do you have a "The Odin Project" folder in root...?

### Alina-PANG/HW2
- Separate css into new file
- Where are the buttons?
- You don't need a form to put an input tag
- `position: relative; left: 300;` makes `.texts` push to the right. Use `margin-left: 300` instead.

### HanamaruSS/google-clone
- Why put `p` at top? Maybe a list is better?
- `img#gimage` margin-top so big? :o Also, it's a redundant tag, can just go with `#gimage`.
  - Even `#gimage` might be a bad name. What if suddenly Google renames itself into 'Indra'? Maybe `#logo` is better.
- You don't need a form to put a button tag. You can just use `a` tags and style it
- Why are you stalking me D:
- What's the difference between `index.html` and `hard.html`?

### KhooDesmond/commIT-homework
- `<section style="height: 100px; color: white;"></section>` cannot lah. :p Use margins.
- Empty section tag?
- `span { padding-left: 10px; padding-right: 10px; }` maybe not... Use classes instead.
- In the top section why are you putting span inside span inside span lol
- Use `bottom: 0; left: 0; right: 0;` for bottom navbar
