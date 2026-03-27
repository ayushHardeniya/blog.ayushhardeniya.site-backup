---
title: "🧠 What I Learned Today: Fixing LinkedIn's Cached OG Image Like a Pro!"
seoTitle: "Fix LinkedIn OG Image Not Updating with Cache Busting Trick"
seoDescription: "Updated your OG image but LinkedIn still shows the old one? Learn how to fix preview cache issues using Post Inspector and versioning like ?v=2."
datePublished: 2025-06-29T10:41:50.183Z
cuid: cmchjiqnb000002lb6anz1tg1
slug: what-i-learned-today-fixing-linkedins-cached-og-image-like-a-pro
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1751193595349/4c54e5e1-0629-4af3-af47-b6dce1bc8663.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1751193665877/a228fcde-ad62-4778-9884-3fbbd5e679d1.png
tags: web-development, learning, coding, linkedin, ayushhardeniya

---

Ever pushed a shiny new Open Graph (OG) image on your website, shared it on LinkedIn... and saw the **old version still pop up?**  
Yep - same here. Here's how I fixed it in less than 10 minutes, and what I learned in the process.

---

## 🚩 Problem

I had just updated the OG image on my personal website. But when I tried sharing the link on LinkedIn, it still showed the **previous version of the image**.  
At first, I thought maybe I made a mistake while uploading...

🖼️ ***\[Screenshot: Old OG image being shown on LinkedIn\]***

![Old OG image being shown on LinkedIn](https://cdn.hashnode.com/res/hashnode/image/upload/v1751192754123/eb2aa367-07fa-4a36-9b2c-e0dcb5321f88.png align="center")

---

## 🕵️‍♂️ Investigating via LinkedIn Post Inspector

I headed to [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/) to see what was being cached.

Surprisingly, it showed the **correct updated OG image** - which meant LinkedIn's backend had already crawled and updated the image.

🧩 ***\[Screenshot: Post Inspector showing the updated OG image correctly\]***

![Post Inspector showing the updated OG image correctly](https://cdn.hashnode.com/res/hashnode/image/upload/v1751192954436/c012eea6-780c-4704-8920-f18afbf20827.png align="center")

---

## 🛠️ Solution: Cache Busting with \[ `?v=2` \]

Turns out, LinkedIn aggressively caches images, even after you update them.

### 🔧 The Fix? A simple query string:

```bash
<meta property="og:image" content="https://ayushhardeniya.site/assets/website-pw-1.png?v=2">
```

Just by adding `?v=2` to the image URL, LinkedIn thinks it's a new resource.  
I redeployed my website with the updated tag.

🧪 ***\[Screenshot: Code editor showing updated OG tag with*** `?v=2`\]

![Code editor showing updated OG tag with ?v=2](https://cdn.hashnode.com/res/hashnode/image/upload/v1751193073646/40549348-648e-41e9-8b18-e4fb3706bea6.png align="center")

---

## ✅ The Result: Success!

Went back to [Post Inspector](https://www.linkedin.com/post-inspector/), ran the URL again, and... **bam!** The updated OG image finally showed up.

🎉 ***\[Screenshot: LinkedIn showing the updated image after purging\]***

![LinkedIn showing the updated image after purging](https://cdn.hashnode.com/res/hashnode/image/upload/v1751193152478/273b1286-9814-4dd1-8ed1-31d6854111d7.png align="center")

---

## 📚 What I Learned

* LinkedIn aggressively caches OG images (more than expected).
    
* Adding a simple `?v=2` or any version number is a clean way to bust cache.
    
* Tools like LinkedIn Post Inspector are gold for debugging social previews.
    
* Don’t forget to redeploy your site after editing meta tags.
    

---

## 💬 Final Thought

Small fixes like these often seem trivial, but the clarity they bring to your digital identity is **huge**.  
It was a 10-minute fix, but I enjoyed learning something new.  
  
~Ayush Hardeniya