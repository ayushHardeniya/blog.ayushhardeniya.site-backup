---
title: "Solving PayPal & Ko-fi Integration While Hosting on GitHub with Custom Domain and Setting Up SEO — A Complete Guide"
seoTitle: "How I Set Up My Website, Ko-fi Button (with PayPal Integration)"
seoDescription: "A complete guide on setting up GitHub Pages, a custom domain, Ko-fi donations, and fixing PayPal verification issues-plus SEO & monetization stuff!"
datePublished: 2025-06-04T14:00:13.780Z
cuid: cmbi0lkus000i08jy8mne1nnm
slug: solving-paypal-and-ko-fi-integration-while-hosting-on-github-with-custom-domain-and-setting-up-seo-a-complete-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1749050362715/70545f8d-95df-4c37-8eef-24fabc1576ad.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1749051019515/9eaa33ad-574a-409e-9c71-fd7c5499704d.png
tags: web-development, paypal, githubpages, buymeacoffee

---

**Introduction:**  
Launching my personal website [ayushhardeniya.site](https://ayushhardeniya.site/) came with several exciting tasks and equally frustrating roadblocks. From integrating Ko-fi for support payments, configuring PayPal for Indian users, hosting on GitHub Pages using a custom domain, to getting indexed properly by Google Search - I faced real issues, dug into each, and here’s a human-first, complete technical + non-technical guide to help you avoid the same potholes.

---

### 🌐 Step 1: Hosting GitHub Repository on Custom Domain

#### Problem:

I had an existing GitHub Page live at `ayushHardeniya.github.io` but wanted my site to show up at `https://ayushhardeniya.site`.

#### Solution:

1. Bought domain from a registrar (mine was BigRock).
    
2. Went to GitHub Repo &gt; Settings &gt; Pages.
    
3. Added `ayushhardeniya.site` in the **Custom domain** section.
    
4. Created a `CNAME` file in the root of my repo with this line:
    

```txt
ayushhardeniya.site
```

5. In domain DNS settings:
    

* Added A records pointing to GitHub IPs:
    

```txt
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

* Added a CNAME record pointing to `ayushhardeniya.site`
    

6. Waited until **Enforce HTTPS** became available.
    

📌 **SEO Tip**: Google loves HTTPS. Be sure to enable “Enforce HTTPS” in GitHub Pages once available. It might take some hours.

---

### 📮 Step 2: Setting Up Zoho Mail for Custom Email

#### Problem:

Needed to use custom email IDs like `connect@ayushhardeniya.site`.

#### Solution:

1. Signed up on [Zoho](https://zoho.com/mail).
    
2. Added TXT record to verify domain.
    
3. Set MX records as given by Zoho.
    
4. Created user mailboxes.
    

💡 Now I have working professional email addresses under my own domain.

---

### ☕ Step 3: Integrating Ko-fi Button & PayPal Payments

#### Problem:

Ko-fi kept showing errors:

> "You cannot currently receive payments on your PayPal account..."

#### Detailed Fix:

##### 🧩 Fixing PayPal Setup

1. Went to [PayPal Business Setup](https://www.paypal.com/in/home).
    
2. Filled the form under **Account Settings &gt; Business Info**:
    

```plaintext
Business Type: Individual
PAN: <My PAN Number>
Purpose Code: P0805 (Personal use/Design/IT Services)
Industry Type: Services
CC Statement Name: PAYPAL*AYUSH
```

3. Matched PayPal name EXACTLY with PAN.
    
4. Revisited KYC page: [https://www.paypal.com/in/webapps/mpp/kyc](https://www.paypal.com/in/webapps/mpp/kyc)
    
5. Used desktop browser - mobile submissions were buggy.
    
6. Cleared cache, logged out and in again.
    

📞 Optional but helpful: Contact PayPal support if stuck in loop.

##### 🔄 Connecting with Ko-fi

* Back to [Ko-fi Settings](https://ko-fi.com/manage/payments)
    
* Clicked “Check if you're ready to go”
    
* Finally showed: ✅ Connected
    

---

### 📄 Step 4: Setting Up Contact Form with Google Sheets Integration

#### Problem:

My site had a contact form, but it failed to submit or redirected with an error.

#### Solution:

Replaced it with a working Google Sheet-based form using `formsubmit.co` or \[Google Apps Script\]. Here's a sample:

```html
<form action="https://formsubmit.co/your-email@example.com" method="POST">
  <input type="text" name="First Name" required>
  <input type="text" name="Last Name" required>
  <input type="email" name="Email" required>
  <textarea name="Message"></textarea>
  <button type="submit">Submit</button>
</form>
```

✅ Simple. No backend. Automatically sends to mail or Google Sheet if configured.

---

### 📈 Step 5: Pushing to Google Search Console for SEO

#### 1\. Domain Verification

* Go to [Google Search Console](https://search.google.com/search-console/about).
    
* Add new property &gt; Choose domain method.
    
* Added TXT record in DNS:
    

```txt
TXT @ google-site-verification=xxxxxxxxxxx
```

* Verified successfully.
    

#### 2\. Sitemap Setup

* Added sitemap URL:
    

```txt
https://ayushhardeniya.site/sitemap.xml
```

✅ Suggestion- You can generate one using [XML Sitemap Generator](https://www.xml-sitemaps.com/) and add it to your repo.

---

### 🔍 Step 6: Optimizing SEO (Meta Tags + Schema + OG)

#### Page Title:

```html
<title>Ayush Hardeniya - Developer, Creator & Explorer</title>
```

#### Meta Description:

```html
<meta name="description" content="Explore the world of Ayush Hardeniya - a passionate developer, reader, and creator sharing blogs, gallery, values, and more." />
```

#### Meta Open Graph:

```html
<meta property="og:title" content="Ayush Hardeniya - Official Website">
<meta property="og:description" content="My journey as a developer, reader, explorer & more">
<meta property="og:image" content="https://ayushhardeniya.site/preview.png">
```

#### Canonical URL:

```html
<link rel="canonical" href="https://ayushhardeniya.site/" />
```

#### Schema.org JSON-LD:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Ayush Hardeniya",
  "url": "https://ayushhardeniya.site",
  "sameAs": [
    "https://github.com/AyushHardeniya",
    "https://twitter.com/ayushhardeniya"
  ],
  "image": "https://ayushhardeniya.site/profile.png",
  "jobTitle": "Developer & Creator"
}
</script>
```

---

### 🧾 Final Thoughts

This blog is a real reflection of what I have faced and sorted accordingly and even a student/freelancer/early-stage creator faces when integrating modern tools together. From DNS misconfigurations to payment integration and SEO indexing - this guide covers it all, from my own experiences.

If you’re going through the same, just follow the steps - or hit me up on [Twitter](https://twitter.com/ayushhardeniya) or my [contact page](https://ayushhardeniya.site/).

---

**Author:** Ayush Hardeniya  
🌐 **Website:** [https://ayushhardeniya.site](https://ayushhardeniya.site/)  
☕️ **Buy Me A Coffee:** [https://ko-fi.com/ayushhardeniya](https://ko-fi.com/ayushhardeniya)

---

If you liked this blog or found it helpful, do consider sharing it. ❤️