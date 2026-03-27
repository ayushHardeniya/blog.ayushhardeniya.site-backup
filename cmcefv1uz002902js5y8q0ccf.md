---
title: ".nojekyll + Canonical Tag: My Simple Fix for Indexing Errors"
seoTitle: ".nojekyll + Canonical Tag: My Simple Fix for Indexing Errors"
seoDescription: "Learn how I fixed Google Search Console indexing errors on GitHub Pages using .nojekyll, canonical URLs, and Git commands in VS Code."
datePublished: 2025-06-27T06:36:07.595Z
cuid: cmcefv1uz002902js5y8q0ccf
slug: nojekyll-canonical-tag-my-simple-fix-for-indexing-errors
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1751005988289/545ae70f-b566-400b-97d5-0b201a9a7b55.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1751006113329/300dfef8-4a7b-4132-9d4b-985a2853b1d8.png
tags: github, web-development, seo, git, google, indexing, google-search-console, ayushhardeniya

---

**🗓️ Date: June 27, 2025 | 🕦 Time: 11:30 AM**

Two days back, I received a mail from **Google Search Console** saying that **two of my website pages weren’t being indexed**. The report showed that both pages were **stopped from being crawled** due to an error.

📸 *\[Search Console error message\]*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751005138799/fb47e431-32f2-450b-85b5-f26203819df5.png align="center")

---

### 🔍 Investigating the Issue

After some research, I discovered that this could be happening due to a **redirecting issue**. To fix it, I added a **canonical URL** to the `<head>` section of both HTML pages. This helps tell search engines the correct version of a page, avoiding confusion.

📸 *\[Canonical tag added in HTML\]*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751005215010/40fe4ca9-8f2f-4302-a560-37f92cd3263b.png align="center")

---

### 🤔 And Then I Found Out About `.nojekyll`

While researching more about indexing issues on GitHub Pages, I came across something new – a file named `.nojekyll`.

> `.nojekyll` is a special file you add to your GitHub Pages repo to tell GitHub **not to use Jekyll processing**.  
> Why? Because Jekyll, by default, ignores folders that start with an underscore (\_), and we don’t want that.

📸 *\[Explanation of* `.nojekyll` - Reference image\]

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751005268755/ea513791-0306-4d65-a728-f76c72bc4e9e.png align="center")

---

### 💻 Making the Change Using Git (From VS Code)

Until now, I always created files **manually using the cursor**, but this time, I wanted to do it **via the Git terminal** inside VS Code.

At first, I ran:

```bash
add .nojekyll
```

But got an error because the file didn’t exist yet 😅

📸 *\[Git error for missing file\]*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751005474416/21ba249f-efb8-4c22-bec3-848c3fa74404.png align="center")

---

### 💡 Learning to Create a File via Terminal

Then I Googled it, and finally discovered the correct way to **create a new file using the command line**:

```bash
echo > .nojekyll
```

And boom! File created 🎉

---

### ✅ Staging, Committing, and Pushing Changes

Once the file was there, I staged the change using:

```bash
git add .nojekyll
```

> *Staging simply tells Git: “Hey! This file exists now. I’m ready to save this change.”*

Then committed it:

```bash
git commit -m "Added .nojekyll to disable jekyll processing"
```

And finally pushed to the main branch:

```bash
git push origin main
```

📸 *\[Staging + Commit + Push process\]*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751005595418/88d8e02f-70de-4bbc-a0b2-ffe71b459a49.png align="center")

---

### 🔁 Re-submitted to Search Console

After the file was live, I went back to Google Search Console and **resubmitted both pages for indexing**.

📸 *\[Reindexing request\]*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751005674034/e20f0422-266a-49ae-8b34-5ec52d302677.png align="center")

---

### Still facing the issue? Here is the solution…

Final Cleanup & Indexing Success!

After adding the `.nojekyll` file and canonical URLs, I noticed that the **real issue** was with inconsistent URLs - especially those **missing the trailing slash** (like `/about` instead of `/about/`).

🔧 So here’s what I did next:

* ✅ **Updated all internal links** (e.g., `/about` → `/about/`)
    
* ✅ **Fixed URLs in the** `sitemap.xml` to include trailing slashes
    
* ✅ **Set canonical tags** with proper URLs ([`https://ayushhardeniya.site/about/`](https://ayushhardeniya.site/about/))
    
* ✅ **Re-submitted URLs and sitemap** in Google Search Console
    

📸 *\[Updated Sitemap.xml with trailing slash\]*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751034063968/4d8a227d-0334-4fda-921f-73274c254d17.png align="center")

---

### 🎉 Final Result?

**Google indexed the pages successfully!**  
And I learned the importance of consistent URL formatting - especially on static site hosts like GitHub Pages.

📸 *\[Search Console showing indexed page confirmation\]*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751034105922/8a9fca56-4975-4710-b272-64a700e9bf65.png align="center")

This was one of those small but **super insightful learning days**, and I’m glad I documented it here!;

~Ayush Hardeniya