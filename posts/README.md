# ✅ Your Guide: How to Add a New Blog Post

This guide explains the simple, two-step process for adding a new blog post to the website.

---

## Step 1: Create the Post Content File

First, you need to create the file that will hold the actual content of your article.

1.  **Define your "slug":** Think of a short, URL-friendly name for your post. This is your post's **slug**. It should be all lowercase, with words separated by hyphens.
    *   *Example:* For a post titled "My Trip to Ella Rock", a good slug would be `my-trip-to-ella-rock`.

2.  **Navigate to the content folder:** Go into the `/posts/post-content/` directory.

3.  **Create the content file:** Create a new HTML file named after your slug.
    *   *Example:* `my-trip-to-ella-rock.html`.

4.  **Write the article:** Open the new file and write your article using standard HTML tags. You can use the existing posts as a template.
    *   Use `<h2>` or `<h3>` for subheadings.
    *   Use `<p>` for paragraphs.
    *   Use `<ul>` and `<li>` for bulleted lists.
    *   Use `<blockquote>` for quoted text.
    *   Use `<img>` to embed images within the post.

---

## Step 2: Update the `posts.json` Database File

Next, you need to tell the website that your new post exists by adding its details to the main list.

1.  **Open the database file:** Open the `/posts/posts.json` file located in this directory.

2.  You will see an array of post objects, starting with `[` and ending with `]`. Each post is enclosed in `{...}`.

3.  **Copy an existing post block:** To create a new entry, copy an entire existing post object (from the opening `{` to the closing `}`), including the comma after it.

4.  **Paste the new block:** Paste your copied block at the **very top** of the list, right after the opening `[` bracket. This ensures the newest post always appears first on the blog page.

5.  **Modify the details** of the block you just pasted:
    *   **`"slug"`**: The slug you decided on in Step 1. **This must match the filename exactly** (without the `.html` extension).
        *   *Example:* `"my-trip-to-ella-rock"`
    *   **`"title"`**: The full, human-readable title of your blog post.
        *   *Example:* `"My Awesome Trip to Ella Rock"`
    *   **`"date"`**: The publication date you want to display.
        *   *Example:* `"October 27, 2023"`
    *   **`"author"`**: Your name or the company name.
        *   *Example:* `"Vanowarna Aerials"`
    *   **`"summary"`**: A short, one- or two-sentence description that will appear on the main blog page under the title.
    *   **`"thumbnailUrl"`**: A direct link to a cover image for your post. You can use a service like Unsplash or upload your own image to your GitHub repository and use its "raw" link.

---

And that's it! 🚀

Once you save both the new content file and the updated `posts.json` file, your website's blog will be automatically updated with the new post.

---

### Prompt

```
You are an expert, full-stack web content processor for a static website. Your task is to take a single piece of raw blog content and generate a complete, multi-part output containing everything needed to publish it. This includes the filename, the formatted HTML content, and the final JSON metadata object.

### PARAMETERS
- Default Author: [Vanowarna Aerials]
- Today's Date: [October 27, 2023]

### TASK
Analyze the raw blog content provided below. Then, generate a single, structured response containing the three parts as specified in the "Output Structure and Rules" section.

### OUTPUT STRUCTURE AND RULES

The final output must contain the following three sections, clearly separated by Markdown headers.

---
#### 1. FILENAME (for /posts/post-content/ folder)
*   **Rule:** Generate a "slug" from the main post title. Convert the title to all lowercase, replace spaces and special characters with hyphens (`-`), and append `.html` to the end.

---
#### 2. HTML CONTENT (to paste into the new file)
*   **Rule:** Convert the raw text into clean, semantic HTML. Use `<h2>` for main section titles, `<p>` for paragraphs, `<ul>`/`<ol>` for lists, and `<blockquote>` for quotes.
*   **NEW LINKING RULE:** Proactively identify text that implies a hyperlink (e.g., "visit the official CAASL website", "check out our Instagram", "find stock photos on Unsplash") and given links. Use your knowledge base to find the most appropriate URL and create a complete `<a>` tag with a valid `href`. If links are in citation format, add sources at the bottom as an ordered list. For all external links, include `target="_blank"` to open them in a new tab. If a suitable URL cannot be determined, do not create a link.
*   **Constraint:** The output must NOT include `<html>`, `<head>`, or `<body>` tags. It should only be the body content.

---
#### 3. JSON OBJECT (to add to /posts/posts.json file)
*   **Rule:** Generate a single, valid JSON object with the following key-value pairs.
*   **Constraint:** Do not wrap the JSON in backticks or any explanatory text. It must be a raw JSON object, ready to be copied.

*   **JSON Key Rules:**
    *   `"slug"`: The slug generated for the filename (without the `.html` extension). **This must match the filename's base name exactly.**
    *   `"title"`: The full title extracted from the raw content.
    *   `"date"`: Use the "Today's Date" parameter from above.
    *   `"author"`: Use the "Default Author" parameter from above.
    *   `"summary"`: Create a concise, one-to-two-sentence summary of the entire blog post, suitable for a preview card.
    *   `"thumbnailUrl"`: First, generate a descriptive search query based on the post's content. Then, create a placeholder URL in the format `https://images.unsplash.com/photo-ABC?description=[your-search-query]`.

---

### RAW BLOG CONTENT TO PROCESS:
[PASTE YOUR RAW BLOG CONTENT HERE]
```
