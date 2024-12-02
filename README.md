# 📖 Vue Article Page README  

This README provides a concise overview of a **Vue 3 component suite** built with 💡 **TypeScript** and 🎨 **SCSS**, focusing on content presentation and interactivity. These components include:  

- 🖊️ **Author Section** – Showcases the author’s details.  
- 📚 **Main Content Section** – Displays the article body with dynamic features.  
- 🔄 **Related Articles Carousel** – Dynamically fetches and displays related articles.  

Let’s dive into the details! 🚀  

---

## **📦 Components**  

### 🖊️ **Author Section**  
The **Author Section** is designed to display key information about the author, including their name, avatar, bio, and a button linking to their full profile.  

#### **Features:**  
- **Avatar and Name:** Displays the author’s image and full name.  
- **Bio Display:** A brief bio with truncation for long text.  
- **Profile Button:** A clickable button to access the full profile.  

#### **Data Injection:**  
This component relies on the following injected `author` object:  
```typescript  
{  
  avatar: string; // URL of the author’s avatar  
  full_name: string; // Full name of the author  
  bio: string; // A short biography  
}  
```  

---

### 📚 **Main Content Section**  
The **Main Content Section** renders the primary article body and tags, with support for dynamic headings. It provides a clean, user-friendly layout for reading content.  

#### **Features:**  
- **Dynamic Headings:** Automatically assigns IDs to `<h2>` elements in the article.  
- **Interactive Tags:** Tags are rendered as clickable buttons.  
- **Report Button:** Allows users to report content issues.  

#### **Props:**  
- **`article` (Object):** Contains article data, including text and metadata.  
- **`tags` (Array):** List of associated tags for the article.  

### 🔄 **Related Articles Carousel**  
The **Related Articles Carousel** is a dynamic and responsive component that displays related articles fetched from an API. It adjusts to different screen sizes, providing a smooth browsing experience.  

#### **Features:**  
- **Dynamic Slides:** Automatically adjusts the number of visible articles based on screen size.  
- **Interactive Controls:** Includes next/previous buttons and clickable slide indicators.  
- **API Integration:** Fetches related articles dynamically using Axios.  

#### **API Requirements:**  
- **Endpoint:** `/api/related`  
- **Query Parameters:**  
  ```json  
  {  
    "entity_type": "blog",  
    "entity_slug": "example-slug",  
    "domain": "blog,section,course,word",  
    "take": 6  
  }  
  ```  

#### **Code Example:**  
```vue  
<template>  
  <related-articles />  
</template>  
```  

---

## **🚀 Quick Start**  

### **1️⃣ Install Dependencies:**  
```bash  
npm install  
```  

### **2️⃣ Run Development Server:**  
```bash  
npm run dev  
```  

### **3️⃣ Build for Production:**  
```bash  
npm run build  
```  

---

## **🎨 Customization**  

- **Style Adjustments:** Modify `_colors.scss` and `_mixin.scss` for theme customization.  
- **API Integration:** Update the API endpoint in `related-articles`.  
