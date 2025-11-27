# Flashcard French Learning App (Flashy)

A simple Python-based flashcard application built using **Tkinter** and **pandas** for learning French vocabulary.  
The app shows a French word, flips automatically to reveal its English meaning, and allows you to mark words as “known,” removing them from the learning list and saving your progress.

---

## Features

### • Flashcard System  
- Displays a French word on the front side.  
- Automatically flips to show the English meaning after 3 seconds.  
- Uses front and back image cards for a clean UI.

### • Track Your Progress  
- Words marked as **known** are permanently removed from the study list.  
- Remaining words are saved to `data/words_to_learn.csv`, so you resume exactly where you left off.

### • Randomized Learning  
- Each card is selected randomly from the remaining words.

### • Persistent Storage  
- On first run, the app loads words from `data/french_words.csv`.  
- After you start marking words as known, the updated list is saved to `data/words_to_learn.csv`.  
- The app always loads your saved `words_to_learn.csv` if it exists.

---

## Project Structure

```
project/
│── main.py
│
│── data/
│   ├── french_words.csv         # Original full vocabulary list
│   └── words_to_learn.csv       # Auto-generated learning progress file
│
│── images/
│   ├── card_front.png
│   ├── card_back.png
│   ├── right.png
│   └── wrong.png
│
│── README.md
```

---

## How It Works

### 1. Loading Data  
The app checks for an existing progress file:
```python
data = pandas.read_csv("data/words_to_learn.csv")
```
If not found, it loads the original dataset:
```python
original_data = pandas.read_csv("data/french_words.csv")
```

### 2. Showing a New Card  
- Picks a random word from the remaining list (`to_learn`).  
- Shows the **French** word first.  
- Starts a 3-second timer to flip the card.

### 3. Card Flip  
- Front → “French”  
- Back → “English”

### 4. Mark as Known  
When ✓ button is clicked:  
- The selected card is removed from `to_learn`.  
- Remaining list is saved to `data/words_to_learn.csv`.  
- The next card is immediately shown.

---

## Buttons & UI Components

### ✓ Known Button (`right.png`)
Removes the current card from the learning list and shows a new one.

### ✗ Skip Button (`wrong.png`)
Skips the current card and shows another randomly chosen one.

### Canvas & Images  
- `card_front.png` displays the French side.  
- `card_back.png` displays the English side.  
- Tkinter Canvas is used for smooth image and text rendering.

---

## Requirements

Install necessary packages:
```
pip install pandas
```
Tkinter is included with Python by default.

---

## How to Run

1. Ensure this folder structure exists:
```
main.py
data/
images/
```

2. Run the app:
```
python main.py
```

3. The learning session begins immediately:
   - French word appears  
   - Flips after 3 seconds  
   - Click ✓ to mark as known  
   - Click ✗ to skip  

---

## Data Format

### `french_words.csv` structure:
```
French,English
bonjour,hello
merci,thank you
...
```

### `words_to_learn.csv`
Generated automatically with the **same column format** and updated as you progress.

---

## Purpose of the Project

To help learners **practice French vocabulary** with an interactive flashcard system that:
- visually engages the user  
- flips cards automatically  
- tracks learning progress  
- saves progress between sessions  

This project demonstrates practical use of:
- Tkinter GUI  
- pandas file handling  
- randomization  
- state management  
- real-time UI updates  

---

## License
This project is open for educational and personal use.
