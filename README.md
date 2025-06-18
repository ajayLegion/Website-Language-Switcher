# Website-Language-Switcher
 website that can change its language dynamically
To create a website that can change its language dynamically (i.e., support **multiple languages or localization**), you need to follow these basic steps:

---

### 🌐 1. **Decide on Language Options**

Choose the languages your website will support (e.g., English, Hindi, Tamil, etc.).

---

### ⚙️ 2. **Use Language Files (Best Practice)**

Store text content in separate files for each language. For example:

```plaintext
en.json (for English)
{
  "welcome": "Welcome",
  "about": "About Us"
}

hi.json (for Hindi)
{
  "welcome": "स्वागत है",
  "about": "हमारे बारे में"
}
```

---

### 💻 3. **Frontend (HTML/JavaScript Example)**

#### HTML:

```html
<select id="languageSwitcher">
  <option value="en">English</option>
  <option value="hi">हिंदी</option>
</select>

<h1 id="welcomeText"></h1>
```

#### JavaScript:

```javascript
let langData = {};

function loadLanguage(lang) {
  fetch(`${lang}.json`)
    .then(res => res.json())
    .then(data => {
      langData = data;
      updateText();
    });
}

function updateText() {
  document.getElementById("welcomeText").innerText = langData["welcome"];
}

document.getElementById("languageSwitcher").addEventListener("change", function() {
  loadLanguage(this.value);
});

// Default language
loadLanguage("en");
```

---

### 🌍 4. **For Large Websites / Frameworks**

If you're using frameworks like:

* **React** → Use `react-i18next`
* **Vue** → Use `vue-i18n`
* **Next.js** → Use built-in i18n support or `next-i18next`

---

### 🔁 5. Optional: Auto-detect Language

Detect browser language:

```javascript
const userLang = navigator.language || navigator.userLanguage;
loadLanguage(userLang.startsWith("hi") ? "hi" : "en");
```

---

### ✅ Summary

| Step | Task                           |
| ---- | ------------------------------ |
| 1    | Create language text files     |
| 2    | Load selected language file    |
| 3    | Update DOM with translations   |
| 4    | Optional: Save user preference |


---

### 📁 Folder Structure

```
/project-folder
│
├── index.html
├── en.json
└── hi.json
```

---
<img title="Website-Language-Switcher" alt="Website-Language-Switcher view" src="">
