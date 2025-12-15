# 📝 Instructions for Adding New Content

## Overview
This English Learning Reference Guide consists of JSON data files and an interactive HTML interface. When you add new words, idioms, phrasal verbs, or grammar rules to the JSON files, the `index.html` will **automatically** display them when you refresh the page in your browser.

---

## 🗂️ File Structure

```
english-level/
├── index.html                          # Interactive web interface (auto-updates)
├── ENGLISH_REFERENCE_GUIDE.md         # Markdown reference guide
├── INSTRUCTIONS.md                     # This file
└── json/
    ├── Idioms.json                    # All idioms
    ├── PhrasalVerb.json              # All phrasal verbs
    ├── Rules.json                     # All grammar rules
    └── Words.json                     # All vocabulary words
```

---

## 📚 How to Add New Content

### 1. Adding a New **Vocabulary Word** (Words.json)

Open `json/Words.json` and add a new entry inside the `"words"` array:

```json
{
  "words": [
    // ...existing words...
    {
      "word": "example",
      "ipa": "/ɪɡˈzæmpəl/",
      "meaning_en": "a thing characteristic of its kind",
      "meaning_es": "ejemplo; muestra",
      "emoji": "📝✨",
      "origin_en": "From Latin 'exemplum', meaning 'sample'.",
      "origin_es": "Del latín 'exemplum', que significa 'muestra'.",
      "examples": [
        "This is a good example.",
        "Can you give me an example?"
      ],
      "note": "Optional note or warning"
    }
  ]
}
```

**Required Fields:**
- `word` - The vocabulary word
- `ipa` - Pronunciation in IPA format
- `meaning_en` - English meaning
- `meaning_es` - Spanish meaning
- `emoji` - Related emojis (visual aid)
- `origin_en` - English etymology
- `origin_es` - Spanish etymology
- `examples` - Array of example sentences

**Optional Fields:**
- `note` - Warning or special note (displayed in red)

---

### 2. Adding a New **Idiom** (Idioms.json)

Open `json/Idioms.json` and add a new entry inside the `"idioms"` array:

```json
{
  "idioms": [
    // ...existing idioms...
    {
      "expression": "Break the ice",
      "ipa": "/breɪk ðə aɪs/",
      "meaning_en": "To initiate conversation in a social setting.",
      "meaning_es": "Romper el hielo; iniciar una conversación.",
      "emoji": "🧊💬",
      "origin_en": "From ships breaking ice to create a path.",
      "origin_es": "De barcos rompiendo hielo para crear un camino.",
      "examples": [
        "He told a joke to break the ice.",
        "The game helped break the ice at the party."
      ],
      "note": "Optional note"
    }
  ]
}
```

**Required Fields:**
- `expression` - The idiom phrase
- `ipa` - Pronunciation
- `meaning_en` - English meaning
- `meaning_es` - Spanish meaning
- `emoji` - Related emojis
- `origin_en` - English origin story
- `origin_es` - Spanish origin story
- `examples` - Array of examples

**Optional Fields:**
- `note` - Special note or warning

---

### 3. Adding a New **Phrasal Verb** (PhrasalVerb.json)

Open `json/PhrasalVerb.json` and add a new entry inside the `"phrasal_verbs"` array:

```json
{
  "phrasal_verbs": [
    // ...existing phrasal verbs...
    {
      "expression": "Look up",
      "ipa": "/lʊk ʌp/",
      "meaning_en": "To search for information.",
      "meaning_es": "Buscar información.",
      "emoji": "🔍📖",
      "origin_en": "From the action of looking upward in a reference book.",
      "origin_es": "De la acción de mirar hacia arriba en un libro.",
      "examples": [
        "Look up the word in the dictionary.",
        "I'll look it up online."
      ]
    }
  ]
}
```

**Note:** `meaning_en` and `meaning_es` can be **strings** OR **arrays**:

```json
{
  "expression": "Turn on",
  "meaning_en": [
    "To activate a device.",
    "To excite or interest someone."
  ],
  "meaning_es": [
    "Encender un dispositivo.",
    "Emocionar o interesar a alguien."
  ]
  // ...rest of fields
}
```

**Required Fields:**
- `expression` - The phrasal verb
- `ipa` - Pronunciation
- `meaning_en` - English meaning (string or array)
- `meaning_es` - Spanish meaning (string or array)
- `emoji` - Related emojis
- `origin_en` - English origin
- `origin_es` - Spanish origin
- `examples` - Array of examples

---

### 4. Adding a New **Grammar Rule** (Rules.json)

Open `json/Rules.json` and add a new entry inside the `"rules"` array:

```json
{
  "rules": [
    // ...existing rules...
    {
      "rule_name": "Simple Past Tense",
      "emoji": "⏰📅",
      "structure": "Subject + verb-ed / irregular verb",
      "explanation_en": "Used for completed actions in the past.",
      "explanation_es": "Se usa para acciones completadas en el pasado.",
      "examples": [
        "I walked to school yesterday.",
        "She ate breakfast at 8 AM."
      ]
    }
  ]
}
```

**Note:** `structure` can be a **string** OR an **object**:

**String Example:**
```json
{
  "structure": "have / has + past participle"
}
```

**Object Example:**
```json
{
  "structure": {
    "affirmative": "I will go",
    "negative": "I won't go",
    "question": "Will I go?"
  }
}
```

**Required Fields:**
- `rule_name` - Name of the grammar rule
- `emoji` - Related emojis

**At least one of these:**
- `structure` - Grammar structure (string or object)
- `explanation_en` - English explanation
- `meaning_en` - English meaning

**Optional Fields:**
- `explanation_es` - Spanish explanation
- `meaning_es` - Spanish meaning
- `examples` - Array of example sentences

---

## 🔄 How the System Works

### Automatic Updates
1. **Edit JSON file** → Add your new word/idiom/rule
2. **Save the file** → Make sure JSON syntax is valid
3. **Refresh browser** → Open `index.html` and press F5
4. **See new content** → Your addition appears automatically!

### Why It Works
The `index.html` file uses JavaScript to:
- Load all 4 JSON files when the page loads
- Parse the data automatically
- Render all items dynamically
- Update the search index
- Update the statistics

**You never need to edit `index.html` manually!**

---

## ✅ JSON Syntax Rules

### Important Rules to Follow:

1. **Use commas between items** (but NOT after the last item):
   ```json
   {
     "words": [
       { "word": "first" },   ← comma here
       { "word": "second" },  ← comma here
       { "word": "third" }    ← NO comma here (last item)
     ]
   }
   ```

2. **Always use double quotes** for strings:
   ```json
   "word": "example"     ✅ Correct
   'word': 'example'     ❌ Wrong
   word: "example"       ❌ Wrong
   ```

3. **Arrays use square brackets** `[]`:
   ```json
   "examples": [
     "First example",
     "Second example"
   ]
   ```

4. **Objects use curly braces** `{}`:
   ```json
   {
     "word": "test",
     "ipa": "/test/"
   }
   ```

5. **Escape special characters**:
   ```json
   "meaning_en": "It's a test"           ❌ Wrong
   "meaning_en": "It's a test"           ✅ Correct
   "origin_en": "From \"example\""       ✅ Correct (escaped quotes)
   ```

---

## 🛠️ Validation Tools

### Online JSON Validators
Before saving, validate your JSON to avoid errors:

- **JSONLint**: https://jsonlint.com/
- **JSON Formatter**: https://jsonformatter.org/
- **Code Beautify**: https://codebeautify.org/jsonvalidator

### Common Errors

❌ **Missing comma:**
```json
{
  "word": "test"
  "ipa": "/test/"  ← Error: missing comma after "test"
}
```

✅ **Fixed:**
```json
{
  "word": "test",
  "ipa": "/test/"
}
```

❌ **Extra comma:**
```json
{
  "words": [
    { "word": "test" },  ← Error: comma after last item
  ]
}
```

✅ **Fixed:**
```json
{
  "words": [
    { "word": "test" }
  ]
}
```

---

## 📋 Quick Reference Template

### Copy-Paste Templates

**Vocabulary Word:**
```json
{
  "word": "",
  "ipa": "//",
  "meaning_en": "",
  "meaning_es": "",
  "emoji": "",
  "origin_en": "",
  "origin_es": "",
  "examples": [
    ""
  ]
}
```

**Idiom:**
```json
{
  "expression": "",
  "ipa": "//",
  "meaning_en": "",
  "meaning_es": "",
  "emoji": "",
  "origin_en": "",
  "origin_es": "",
  "examples": [
    ""
  ]
}
```

**Phrasal Verb:**
```json
{
  "expression": "",
  "ipa": "//",
  "meaning_en": "",
  "meaning_es": "",
  "emoji": "",
  "origin_en": "",
  "origin_es": "",
  "examples": [
    ""
  ]
}
```

**Grammar Rule:**
```json
{
  "rule_name": "",
  "emoji": "",
  "structure": "",
  "explanation_en": "",
  "explanation_es": "",
  "examples": [
    ""
  ]
}
```

---

## 🎯 Step-by-Step Example

### Example: Adding the word "accomplish"

**Step 1:** Open `json/Words.json`

**Step 2:** Find the last word entry (before the closing `]`)

**Step 3:** Add a comma after the last entry

**Step 4:** Paste this new entry:

```json
    ,
    {
      "word": "accomplish",
      "ipa": "/əˈkʌmplɪʃ/",
      "meaning_en": "to succeed in doing or completing something",
      "meaning_es": "lograr; completar algo exitosamente",
      "emoji": "✅🎯",
      "origin_en": "From Latin 'ad-' (to) + 'complere' (fill up, complete).",
      "origin_es": "Del latín 'ad-' (a) + 'complere' (completar).",
      "examples": [
        "She accomplished all her goals.",
        "We accomplished the project on time."
      ]
    }
```

**Step 5:** Save the file

**Step 6:** Open `index.html` in your browser (or refresh if already open)

**Step 7:** Verify:
- The word count increased by 1
- "accomplish" appears in the Vocabulary section
- Search for "accomplish" works correctly

---

## 🔍 Finding IPA Pronunciations

### Useful Resources:
- **Cambridge Dictionary**: https://dictionary.cambridge.org/
- **Merriam-Webster**: https://www.merriam-webster.com/
- **Oxford Learner's Dictionaries**: https://www.oxfordlearnersdictionaries.com/
- **IPA Phonetic Transcription**: https://tophonetics.com/

---

## 🎨 Choosing Emojis

### Tips:
- Use **2-4 emojis** that represent the word/phrase
- Make them visually memorable
- Combine related concepts

### Examples:
- **"fasten"** → 🔒👕 (lock + clothing)
- **"stick to your guns"** → 💪🔫 (strength + guns)
- **"wash up"** → 🧼👐🍽️ (soap + hands + dishes)

### Emoji Resources:
- **Emojipedia**: https://emojipedia.org/
- **Get Emoji**: https://getemoji.com/

---

## 💡 Best Practices

1. **Be Consistent**: Follow the same format as existing entries
2. **Validate JSON**: Always check your JSON syntax before saving
3. **Test Immediately**: Refresh the browser after each addition
4. **Backup Files**: Keep copies of your JSON files before major changes
5. **One at a Time**: Add and test one entry at a time to catch errors easily
6. **Complete Information**: Fill in all required fields for best results
7. **Use Examples**: Always include 1-3 clear example sentences
8. **Check Pronunciation**: Verify IPA notation is correct
9. **Meaningful Emojis**: Choose emojis that aid memory retention

---

## 🐛 Troubleshooting

### Problem: New content doesn't appear

**Solution:**
1. Check browser console (F12) for JavaScript errors
2. Validate JSON syntax at https://jsonlint.com/
3. Clear browser cache (Ctrl+Shift+Delete)
4. Hard refresh the page (Ctrl+F5)

### Problem: Page shows "Error loading data"

**Solution:**
1. Check that all JSON files are in the `json/` folder
2. Verify file names are exactly: `Rules.json`, `Idioms.json`, `PhrasalVerb.json`, `Words.json`
3. Open browser console (F12) to see specific error message
4. Fix JSON syntax errors

### Problem: Search doesn't find new entries

**Solution:**
1. Refresh the page (the search index rebuilds on load)
2. Make sure you're searching for text that exists in the entry
3. Try searching for just one word from the entry

---

## 📞 Quick Help

### Before Adding Content:
✅ Have all information ready (word, meaning, IPA, origin, examples)  
✅ Choose appropriate emojis  
✅ Write clear example sentences  
✅ Decide which category it belongs to  

### While Adding Content:
✅ Copy a template from this file  
✅ Fill in all required fields  
✅ Add comma before your new entry (if not the first item)  
✅ Remove comma from your entry if it's the last item  
✅ Save the file  

### After Adding Content:
✅ Validate JSON syntax  
✅ Refresh browser  
✅ Search for your new entry  
✅ Check that it displays correctly  
✅ Verify example sentences appear  

---

## 📚 Summary

### The Complete Workflow:

```
1. Choose category (Word/Idiom/Phrasal Verb/Rule)
        ↓
2. Open corresponding JSON file
        ↓
3. Copy template from this guide
        ↓
4. Fill in all information
        ↓
5. Add to JSON array (with proper commas)
        ↓
6. Save file
        ↓
7. Validate JSON syntax
        ↓
8. Refresh index.html in browser
        ↓
9. Test search and display
        ↓
10. Done! ✅
```

---

## 🎓 Example Session

**Task:** Add the phrasal verb "figure out"

```json
{
  "phrasal_verbs": [
    // ...existing entries...
    ,
    {
      "expression": "Figure out",
      "ipa": "/ˈfɪɡjər aʊt/",
      "meaning_en": "To understand or solve something.",
      "meaning_es": "Descifrar; resolver algo.",
      "emoji": "🧠💡",
      "origin_en": "From 'figure' (calculate) + 'out' (completely).",
      "origin_es": "De 'figure' (calcular) + 'out' (completamente).",
      "examples": [
        "I need to figure out this problem.",
        "Can you figure out how to fix it?"
      ]
    }
  ]
}
```

**Result:** After saving and refreshing, "figure out" appears in the Phrasal Verbs section and is searchable!

---

**Last Updated:** December 12, 2025  
**Version:** 1.0  
**Compatible with:** index.html (current version)