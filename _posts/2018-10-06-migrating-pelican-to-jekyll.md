---
Title: Migrating Pelican blog posts to Jekyll
Date: 2018-10-06 18:06
Author: jamesleighton
categories: How-To
tags: [blog, pelican, jekyll, markdown, projects]
Slug: migrating-pelican-blog-posts-to-jekyll
Status: published
image: /images/jekyll-logo.png
---
Pelican and Jekyll both use markdown formatting for their posts, but their post metadata (front matter in Jekyll parlance) formatting is slightly different. I have over 150 posts to migrate, so started looking for a few ways to make this process easier.

Jekyll metadata needs to be surrounded by two lines containing three dashes `---`. This is easily achieved with the use of [sed](https://www.cyberciti.biz/faq/how-to-use-sed-to-find-and-replace-text-in-files-in-linux-unix-shell/). To add the line to very top of the file, use the following [sed command](https://unix.stackexchange.com/a/269758).

```shell
sed  -i '1i ---' *.md
```

To add the line directly underneath your front matter, you can use something like this which looks for a line that contains 'Status:' then adds a new line with '---' underneath it.

This worked for me as all my metadata finished up with 'Status: Published' but you may need to adjust this as nessecary for your files. Alternatively if your front matter is the same number of lines in every file, you could adjust the sed command from above.

```shell
sed -i 's/.*Status:.*/&\n---/' *.md
```

Swap 'Category:'' for 'categories:' in the metadata. I'm not sure why I had to do this, but my post categories started working when I used 'categories' and not category so I used sed to swap them over as below.

```shell
sed -i 's/Category:/categories:/g' *.md
```

You will also need to remove commas from any tag listing you have. I haven't figured out how to do this programatically but it didn't take too long to do manually. Open all your posts in your favourite text editor and update them all. I also took this as a chance to tidy up and consolidate the categories on each post.

```shell
nano *.md
```

The final step is to rename each post as per 'YYYY-MM-DD-post-name.md'. My bash skills are rusty, so I whilst I am sure this is possible within a script I felt it would take me longer to learn how to do this than doing it manually.

Use the following command to save the top of every file into a text file. This made it super simple to rename each file and not miss any when working through the files manually.

If anyone knows a simpler method, please leave a comment below.

```shell
head -n 10 *.md > front.txt
```
