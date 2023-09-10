# pandoc-table

The task at hand is to convert example.md to out.pptx with a lua filter to handle the table. This will only convert the first table.

```bash
pandoc example.md --lua-filter list-table.lua -o out.pptx
```

I need a lua filter which follows the workflow of this bash script:

```bash
bash render_table.sh table.yaml table.png -a l,c -w 2,1 -W 200
```

Your task is to create list-table.lua such that this second table is being rendered as an image. list-table would expand on list-table.lua by converting the table output into an image in the background. Very handy for creating quick-and-dirty presentations. The workflow I use above is to convert from a list to a table via pandoc. That table I store in a .html file which I then render into an image. Not sure if there is a less convoluted way of doing it. So the task is write the lua filter for this command to successfully convert the second list in my example into an image in the final output:

```bash
pandoc example.md --lua-filter list-image.lua --lua-filter list-table.lua -o out.pptx
```

Ideally, the .css information that I stored in render_table.css would be stored directly in the lua filter, at the top so I can easily modify it or add additional arguments later. Also, in the example I export to .png via ```wkhtmltoimage```. Feel free to use something else for this task. If you use ```wkhtmltoimage```, it should export to .png by default but include an alternative flag to export to .svg, which does not respect widths but sets line breaks according to the longest word in each column -- a neat way to get a nice table with little effort.
