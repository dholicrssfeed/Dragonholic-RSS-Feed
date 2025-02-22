# Guide for Updating Novel/Translator Mappings

This guide explains which elements need to be updated whenever a new novel or translator is added. Please update the following sections in `dh_mappings.py` accordingly.

---

## 1. Translator to Novel Mapping

- **File:** `dh_mappings.py`
- **Variable:** `TRANSLATOR_NOVEL_MAP`
- **Instructions:**  
  - Add the translator's name as a new key if it doesn't already exist.
  - Under that key, list all the novel titles (as strings) for that translator.

**Example:**

```python
TRANSLATOR_NOVEL_MAP = {
    "Existing Translator": [
        "Existing Novel Title"
    ],
    "New Translator": [
        "New Novel Title 1",
        "New Novel Title 2"
    ]
}
```

---

## 2. Discord Role ID Mapping

- **File:** `dh_mappings.py`
- **Variable:** `DISCORD_ROLE_ID_MAP`
- **Instructions:**  
  - Add or update the Discord role ID corresponding to the translator.
  - Make sure each role ID is formatted as a string (for example: `"<@&123456789012345678>"`).

**Example:**

```python
DISCORD_ROLE_ID_MAP = {
    "Existing Translator": "<@&ExistingRoleID>",
    "New Translator": "<@&NewRoleID>"
}
```

---

## 3. Novel URL Overrides

- **File:** `dh_mappings.py`
- **Variable:** `NOVEL_URL_OVERRIDES`
- **Instructions:**  
  - If the default URL generated by the slug function isn’t correct, add an override entry here.
  - The key should be the exact novel title and the value is the correct URL.

**Example:**

```python
NOVEL_URL_OVERRIDES = {
    "Help others? It’s better to help yourself": "https://dragonholic.com/novel/helping-others-its-better-to-help-yourself/",
    "New Novel Title": "https://dragonholic.com/novel/new-novel-title/"
}
```

---

## 4. Featured Image URLs

- **File:** `dh_mappings.py`
- **Function:** `get_featured_image(title)`
- **Instructions:**  
  - Update or add a new `if` statement for the new novel so that it returns the correct image URL.
  - Skip this step if there are is no featured image for the novel.

**Example:**

```python
def get_featured_image(title):
    if "New Novel Title" in title:
        return "https://dragonholic.com/wp-content/uploads/2024/new-novel-cover.jpg"
    # ... existing conditions ...
    return ""
```

---

## 5. NSFW Novel List

- **File:** `dh_mappings.py`
- **Function:** `get_nsfw_novels()`
- **Instructions:**  
  - If the new novel is considered NSFW, add its title (exactly as it appears in `TRANSLATOR_NOVEL_MAP`) to the list returned by this function.

**Example:**

```python
def get_nsfw_novels():
    return [
        "Bondage and Marriage",
        "Clap",
        "Double Junk",
        "My Bloody Valentine",
        # ... existing NSFW novels ...
        "New NSFW Novel Title"  # Add here if applicable
    ]
```

---

## Summary Checklist

When adding a new novel or translator, please ensure you update the following:

1. **TRANSLATOR_NOVEL_MAP:**  
   - Add the translator and/or new novel titles.
2. **DISCORD_ROLE_ID_MAP:**  
   - Add the corresponding Discord role ID for the new translator.
3. **NOVEL_URL_OVERRIDES:**  
   - Provide a URL override if the slug generation doesn’t produce the correct URL.
4. **get_featured_image():**  
   - Map the new novel to its featured image URL.
5. **get_nsfw_novels():**  
   - If the novel is NSFW, include it in this list.

Following these steps will ensure that your RSS feed generation and related mappings remain consistent and up to date.

*Happy coding!*
