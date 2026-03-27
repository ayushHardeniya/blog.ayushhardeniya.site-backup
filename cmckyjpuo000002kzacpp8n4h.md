---
title: "🧠 How I Made a Backdated Git Commit Show on GitHub Contributions"
seoTitle: "How I Made a Backdated Git Commit Show on GitHub Contributions"
seoDescription: "Learn how to backdate a Git commit and push it to GitHub so it shows up on your contribution graph. A step-by-step guide with real errors and fixes."
datePublished: 2025-07-01T20:05:48.577Z
cuid: cmckyjpuo000002kzacpp8n4h
slug: how-i-made-a-backdated-git-commit-show-on-github-contributions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1751400192408/427e2de5-3839-4a69-bce0-1b880fdfb42e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1751400254838/b4cfed70-845d-4f53-9d99-ad1434c79131.png
tags: programming-blogs, github, git, developer, ayushhardeniya

---

## 🎯 Goal

I wanted to make a commit on GitHub **with a custom past date** - specifically, **July 1, 2025, at 12:00 PM - to reflect the actual date the work was completed** on my GitHub profile.

Sounds easy, right? I thought so too.  
But here's how it actually went 😅

---

## 📍Step 1: Creating the Commit Locally

I made a small change in my project and staged it with:

```bash
$ echo "Backdated test" >> backdated.txt
$ git add backdated.txt
```

To commit with a custom timestamp, I used:

```bash
$ GIT_AUTHOR_DATE="2025-07-01T12:00:00" GIT_COMMITTER_DATE="2025-07-01T12:00:00" git commit -m "Backdated commit to July 1, 2025"
```

✅ This created a commit with the exact timestamp I wanted.

---

## ❌ Problem 1: `bash: commit: command not found`

At first, Git Bash wouldn’t recognize the commit command because I broke it across lines incorrectly.

**Fix:** Run the full commit command **on a single line**, or use backslashes **with proper spacing**.

---

## ❌ Problem 2: Push Rejected

When I tried to push to GitHub, it said:

> `error: failed to push some refs to origin`

Turns out, Git wouldn't let me push because my local branch and the remote had different histories.

**Fix:** I pulled the latest changes using this:

```bash
$ git pull origin main --allow-unrelated-histories
```

---

## ❌ Problem 3: Vim Nightmare

During that pull, Git launched **Vim** to ask for a merge message... and I got stuck inside it.

**Fix:** Exited Vim by pressing:

```bash
$ Esc
:wq
Enter
```

Classic Git developer moment.

\[Screenshot- Vim Window in git Bash terminal\]

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751399156897/0feb4d89-c118-4075-b86a-81237489e683.png align="center")

---

## ✅ Final Steps

After escaping Vim, I added the file again just to be sure, then committed and pushed:

```bash
$ git add backdated.txt

GIT_AUTHOR_DATE="2025-07-01T12:00:00" GIT_COMMITTER_DATE="2025-07-01T12:00:00" git commit -m "Backdated push for July 1, 2025"

git push origin main
```

This time - everything worked.

---

## 🟩 The Green Square Appears

I went to my GitHub profile and hovered over July 1, 2025. Finally saw:

📸 **\[Screenshot: GitHub contribution graph showing green square on July 1, 2025\]**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751399330286/a28337e9-488f-411c-9b58-5a2e0acdb131.png align="center")

---

## 💡 What I Learned (the hard way)

* Backdating commits is possible - but only if you **set the environment variables correctly**.
    
* GitHub counts a commit only if:
    
    * It’s pushed to the default branch (usually `main`)
        
    * It uses a **verified email** linked to your GitHub account
        
* Git can reject pushes if the histories don’t match - `--allow-unrelated-histories` is your friend
    
* Git Bash doesn’t support `Ctrl + V` (use **right-click** to paste) (funny…)
    
* Vim will trap you if you’re not prepared
    

---

## 🧘 Final Thoughts

All of this… just to get **one green square** on the contribution graph.  
Was it a lot?  
Yes.  
Was it worth it?  
Absolutely. 😄

If you’re ever trying to do the same and getting stuck, just remember - I did too.

~**Ayush Hardeniya**