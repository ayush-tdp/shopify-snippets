Great! Here's a fully working `README.md` file with example folder structure, code snippets, and inline setup instructions. You can copy and paste this directly into your GitHub repo.

---

```markdown
# 🛍️ Shopify Snippets & Functionalities Showcase

A curated collection of powerful Shopify features, reusable Liquid snippets, and custom sections to enhance the functionality and user experience of any Shopify store.

---

## 🚀 Features

### ✅ Cart Page Enhancements

#### 🔹 Auto-Apply Discount
Automatically applies a discount code at the cart page.

**Code: `snippets/auto-discount.liquid`**
```liquid
<script>
  window.onload = function () {
    const discountCode = 'AUTOSAVE10';
    if (!window.location.href.includes('discount=')) {
      window.location.href = '/discount/' + discountCode;
    }
  };
</script>
```

---

### 📄 PDF Viewer

Embed a PDF viewer on any page or section.

**Code: `sections/pdf-viewer.liquid`**
```liquid
<div class="pdf-wrapper">
  <iframe src="{{ section.settings.pdf_url }}" width="100%" height="600px" style="border: none;"></iframe>
</div>

{% schema %}
{
  "name": "PDF Viewer",
  "settings": [
    {
      "type": "url",
      "id": "pdf_url",
      "label": "PDF File URL"
    }
  ],
  "presets": [{
    "name": "PDF Viewer"
  }]
}
{% endschema %}
```

---

### 🎨 Custom Sections

#### 🔹 Countdown Timer

**Code: `sections/countdown-timer.liquid`**
```liquid
<div id="countdown" data-end="{{ section.settings.end_date }}"></div>

<script>
  const countdown = document.getElementById('countdown');
  const endDate = new Date(countdown.dataset.end).getTime();

  const x = setInterval(() => {
    const now = new Date().getTime();
    const distance = endDate - now;

    if (distance < 0) {
      clearInterval(x);
      countdown.innerHTML = "EXPIRED";
    } else {
      const days = Math.floor(distance / (1000 * 60 * 60 * 24));
      const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((distance % (1000 * 60)) / 1000);
      countdown.innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;
    }
  }, 1000);
</script>

{% schema %}
{
  "name": "Countdown Timer",
  "settings": [
    {
      "type": "text",
      "id": "end_date",
      "label": "End Date (YYYY-MM-DDTHH:MM:SS)"
    }
  ],
  "presets": [{
    "name": "Countdown Timer"
  }]
}
{% endschema %}
```

---

## 🧩 Snippet Library

#### 🔹 Product Badge

**Code: `snippets/product-badge.liquid`**
```liquid
{% if product.tags contains 'New' %}
  <span class="badge badge--new">New</span>
{% endif %}
```

Use this in your product-card:
```liquid
{% render 'product-badge', product: product %}
```

---

## 📁 Folder Structure

```plaintext
/
├── snippets/
│   ├── auto-discount.liquid
│   └── product-badge.liquid
├── sections/
│   ├── countdown-timer.liquid
│   └── pdf-viewer.liquid
├── assets/
│   └── js/
│       └── extra-scripts.js (optional)
├── README.md
```

---

## 🛠 How to Use

1. Copy the `.liquid` file to the respective `snippets` or `sections` folder of your Shopify theme.
2. Include snippets using:
   ```liquid
   {% render 'snippet-name' %}
   ```
3. Add sections via Shopify’s theme customizer or insert them directly into templates.

---

## 🙌 Contribute

Pull requests and forks are welcome! Share your ideas, issues, or improvements to grow this library together.

---

## 💬 Contact

For freelance work, custom Shopify builds, or feedback:

**[Your Name]**  
📧 [your.email@example.com]  
🌐 [yourwebsite.com] *(optional)*

---

## ⭐️ Like this repo?

If this helped you, please give it a ⭐️ on GitHub and share it with other Shopify devs!
```

---

Let me know if you want help creating individual files (`.liquid` snippets or section files) or need a `demo-store` setup as part of the repo.
