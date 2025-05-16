# 🕹️ Survive Game

_A simple Android survival game built around a national ID-based pathfinding mechanic._

---

## 🎮 Gameplay Overview

Survive Game challenges players to reach their destination city by decoding their 9-digit national ID number into directional moves.

### 🔢 How it Works:
1. **Input**: User enters a valid 9-digit ID.
2. **Direction Mapping**:  
   Each digit is transformed using:  
   `digit % 4` → direction  
   - `0` = Left  
   - `1` = Right  
   - `2` = Up  
   - `3` = Down  
3. **Action**: Player must tap the on-screen arrows in the correct order based on the calculated directions.
4. **Result**:
   - ✅ All correct → Toast: **"Survived in [City]"**
   - ❌ Mistake made → Toast: **"You Failed"**

---

## 🏙️ City Selection Logic

The city is chosen based on the **8th digit** of the entered ID.

- A list of cities is fetched from:  
  [https://pastebin.com/raw/T67TVJG9](https://pastebin.com/raw/T67TVJG9)
- The 8th digit (index 7) is used to index the city list:
  ```java
  state = data.split(",")[Integer.parseInt(id.charAt(7) + "")];
  ```

### Example:
- **Input ID**: `111111111`  
- **Calculated moves**: `1 1 1 1 1 1 1 1 1` → must press right 9 times  
- **City Index**: 8th digit is `1` → Second city in list = `Texas`  
- **Toast Output**:  
  `Survived in Texas`

---

## 🐛 Bug Fixes

### ✅ Toast Display Duration
**Before:**
```java
Toast.makeText(this, "Survived in " + state, 1).show();
```
**After:**
```java
Toast.makeText(this, "Survived in " + state, Toast.LENGTH_LONG).show();
```

### ✅ Corrupted URL Fix
**Problem**: Hidden zero-width characters in URL  
**Before (broken):**
```
https://pastebin.com/raw/%E2%80%8C%E2%80%8C%E2%80%8CT67TVJG9
```
**Fixed:**
```
https://pastebin.com/raw/T67TVJG9
```

> ✏️ The correct URL was manually typed and saved in `strings.xml` to avoid invisible characters.

---

## 🛠️ Project Notes

- Decompiled the APK using Java decompilation tools
- Retrieved key source files, including Activities and drawable resources
- Manually reconstructed the project in Android Studio
- Fixed logic and UI-related issues
- Rebuilt and validated the app behavior using example IDs

---

## ▶️ How to Run

1. Open the project in **Android Studio**
2. Run on a physical Android device or emulator
3. Enter any **9-digit ID** (e.g., `111111111`)
4. Follow the arrow directions shown based on your ID
5. View result in a toast message




---

## 📸 Video

https://github.com/user-attachments/assets/74d56a33-03ec-4cd4-9921-3104a72221e0

---


