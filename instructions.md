# Hugo + GitHub + Netlify + Cloudflare
#saved

Here’s a fully rewritten **Markdown** guide using the **GitHub-first approach** for setting up a Hugo site with GitHub, Netlify, and Cloudflare.

---

# **🚀 Setup Guide for Hugo + GitHub + Netlify + Cloudflare**

This guide will walk you through setting up a **Hugo site**, deploying it to **GitHub**, hosting it on **Netlify**, and configuring **Cloudflare** to manage DNS and HTTPS.

---

## **📌 Overview**
### **You will:**
1. **Create a GitHub repository first**.
2. **Clone it & initialize Hugo inside**.
3. **Push the Hugo site to GitHub**.
4. **Deploy the site on Netlify**.
5. **Configure Cloudflare for DNS and HTTPS**.
6. **(Optional) Configure email forwarding via Loopia**.

---

## **✅ Step 1: Create a GitHub Repository**
1. Go to [GitHub](https://github.com/) and **log in**.
2. Click **New Repository**.
3. Name it **`machinepsychology`**.
4. **DO NOT add** a README, `.gitignore`, or license (we'll do this later).
5. Click **Create Repository**.

GitHub will now display a page with setup instructions.

---

## **✅ Step 2: Clone the Repository to Your Computer**
Open a terminal and run:

```sh
git clone https://github.com/YOUR-USERNAME/machinepsychology.git
cd machinepsychology
```

This downloads an **empty repository** into a `machinepsychology` directory.

---

## **✅ Step 3: Initialize a Hugo Site in the Repository**
Inside the cloned `machinepsychology` directory, run:

```sh
hugo new site .
```

This initializes a **Hugo site inside the GitHub repository**.

---

## **✅ Step 4: Add a Theme**
Pick a theme from [Hugo Themes](https://themes.gohugo.io/).  
For example, using the **PaperMod** theme:

```sh
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

Edit the Hugo configuration file:

```sh
nano config.toml
```

And add:

```toml
theme = "PaperMod"
```

---

## **✅ Step 5: Add Content**
Create a homepage:

```sh
hugo new content/index.md
```

Edit the file:

```sh
nano content/index.md
```

Add the following content:

```md
---
title: "Machine Psychology"
date: 2025-02-16
---

Welcome to Machine Psychology!
```

---

## **✅ Step 6: Test the Site Locally**
Run:

```sh
hugo server -D
```

Visit **http://localhost:1313** to preview the site.

---

## **✅ Step 7: Commit & Push Everything to GitHub**
Now, commit all changes to GitHub:

```sh
git add .
git commit -m "Initialize Hugo site"
git push origin main
```

Your Hugo site is now **fully versioned in GitHub**.

---

## **✅ Step 8: Deploy the Site on Netlify**
1. **Go to [Netlify](https://app.netlify.com/)** and log in.
2. Click **"New site from Git"**.
3. Select **GitHub** and choose your `machinepsychology` repository.
4. Set the **build settings**:
   - **Branch:** `main`
   - **Build command:** `hugo`
   - **Publish directory:** `public`
5. Click **Deploy Site**.

Netlify will now **build and deploy** your Hugo site.

---

## **✅ Step 9: Configure Cloudflare for DNS**
### **9.1 Move Domain to Cloudflare**
1. **Go to [Cloudflare](https://dash.cloudflare.com/)**.
2. Click **Add a site**.
3. Enter **`machinepsychology.se`** → Click **Continue**.
4. **Choose the Free plan** → Click **Continue**.
5. Cloudflare will show **new nameservers** (e.g., `newt.ns.cloudflare.com`, `emily.ns.cloudflare.com`).
6. **Go to Loopia's control panel** → Change the nameservers to Cloudflare’s.

Once Loopia updates the nameservers, Cloudflare will take control of DNS.

---

### **9.2 Add Netlify DNS Records in Cloudflare**
Once Cloudflare is active:

1. **Delete any existing A/CNAME records** for `machinepsychology.se`.
2. Add a **CNAME record** for the root domain:
   - **Type:** `CNAME`
   - **Name:** `machinepsychology.se`
   - **Target:** `machinepsychology.netlify.app`
   - **Proxy Status:** **DNS Only (grey cloud)**
3. Add a **CNAME record** for `www.machinepsychology.se`:
   - **Type:** `CNAME`
   - **Name:** `www`
   - **Target:** `machinepsychology.netlify.app`
   - **Proxy Status:** **DNS Only (grey cloud)**
4. Click **Save**.

---

### **9.3 Enable HTTPS (SSL)**
1. **Go to Cloudflare → SSL/TLS**.
2. Set **SSL mode to "Full (Strict)"**.

This ensures your site is fully secured.

---

## **✅ Step 10: Verify Deployment**
1. Push a new update to GitHub → Netlify will deploy automatically.
2. Visit **https://machinepsychology.se** to confirm the site is live.

---

## **✅ Step 11: (Optional) Configure Email Forwarding via Loopia**
If you want **email forwarding** (e.g., `contact@machinepsychology.se` → your Gmail), you need to **add Loopia's MX records in Cloudflare**.

1. **Go to Loopia → Check your MX records**.
2. **Add them in Cloudflare** (DNS → Add Records).
3. Now you can set up email forwarding in Loopia.

---

# **🎉 Final Summary**
✅ **GitHub Repository First** → `machinepsychology`  
✅ **Cloned it & Initialized Hugo inside**  
✅ **Pushed back to GitHub**  
✅ **Set up Netlify for auto-deployment**  
✅ **Configured Cloudflare for DNS & HTTPS**  
✅ **(Optional) Set up email forwarding with Loopia**  

Your site is now **fully operational**! 🚀  

---

### **✨ Next Steps**
- Customize your site by editing `config.toml`.
- Add more content inside `content/`.
- Explore [Hugo Documentation](https://gohugo.io/documentation/) for advanced features.

---

Let me know if you have any questions! 🚀
