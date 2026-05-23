# OpenCart 4.1+ Maintenance Mode Mobile Layout Fix

## 🐛 The Problem
In the default installation of OpenCart 4 (and 4.1+), turning on "Maintenance Mode" results in a critical layout failure, especially visible on mobile devices. The footer completely overlaps and hides the header and the maintenance message, making the page look unprofessionally broken.

<img width="300" alt="opencart-4-maintenance-mode-broken-mobile png" src="https://github.com/user-attachments/assets/3fcce413-0850-4f41-9b47-96ee841bc775" />

This happens because the default template file is missing the core `<div id="content">` HTML wrapper. Without it, the default CSS framework cannot maintain the page grid, causing elements to collapse onto each other.

## 🛠️ The Solution
To fix this, simply wrap the maintenance message in the correct `#content` div. 

**File path:** `catalog/view/template/common/maintenance.twig`

**Replace the broken default code:**
```twig
{{ header }}
<div id="common-maintenance" class="container">
  <div class="row">
    <div class="col-12">{{ message }}</div>
  </div>
</div>
{{ footer }}
```

**With the fixed code:**
```twig
{{ header }}
<div id="content">
  <div id="common-maintenance" class="container">
    <div class="row">
      <div class="col-12">{{ message }}</div>
    </div>
  </div>
</div>
{{ footer }}
```
<img width="300" alt="opencart-4-maintenance-mode-fixed-mobile png" src="https://github.com/user-attachments/assets/bdbb50ee-3594-44f9-b161-b186da0f0ee7" />

## 🤝 Partnership for OpenCart Developers

**Project AAX OPCART·EU** invites independent authors to a mutually beneficial partnership. We offer expert support for bringing your developments to the European market based on our specialized B2B platform for OpenCart 4.1+.

Our interaction is built on a professional division of labor: **you create a high-quality software product, and we handle all the associated routine of its localization, adaptation, and promotion.**

### 🌟 Cooperation Principles
* **Unconditional retention of authorship:** You remain the full owner of your development, while we act as a technological partner and publisher.
* **First-level technical support:** Our team fully handles communication with users and basic setup of the modules.
* **Transparent economy:** We provide marketing, sales, and billing under the AAX OPCART·EU brand, guaranteeing you a stable and transparent income as an author.

### ⚙️ Technological Advantages
* **Adaptation and renovation:** Assistance in migrating your modules to modern architecture (Namespaces, Events, PSR). This guarantees flawless compatibility with updates.
* **European localization:** Professional translation of the interface and documentation into all European languages, opening access to markets across all of Europe.
* **B2B Focus:** Creating tools that comply with EU standards, making your products more valuable in the eyes of professional business.

We strive to completely free authors from routine tasks — support, localization, and technical adaptation. This allows you to focus on the main thing: creating new opportunities and improving your products.

✉️ **Looking for a reliable partner?** Send a description of your products to **partners@opcart.eu** or send a request to discuss publication terms.
