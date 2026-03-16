<<<<<<< HEAD
# Fix Suggestions

Two bugs identified in the game and their recommended fixes.

---

## Bug 1: Normal and Hard difficulty ranges are swapped

**File:** `app.py` — `get_range_for_difficulty()` (lines 7–10)

**Problem:** Normal returns a range of 1–100 and Hard returns 1–50. Since a larger range is harder, these are backwards from a UX perspective.

**Current code:**
```python
if difficulty == "Normal":
    return 1, 100
if difficulty == "Hard":
    return 1, 50
```

**Fix:** Swap the return values so Hard has the larger range.
```python
if difficulty == "Normal":
    return 1, 50
if difficulty == "Hard":
    return 1, 100
```

---

## Bug 2: Off-by-one error in "Attempts left" display

**File:** `app.py` — session state initialization (line 96) and info display (line 111)

**Problem:** `attempts` is initialized to `1` before any guess is made, so the displayed attempts left is already decremented on a fresh game:

- Sidebar shows: `Attempts allowed: 8`
- Main area shows: `Attempts left: 7` (before any guess)

**Current code:**
```python
if "attempts" not in st.session_state:
    st.session_state.attempts = 1
```

**Fix:** Initialize `attempts` to `0`. The submit handler already increments before processing, so this correctly reflects no attempts used on a fresh game.
```python
if "attempts" not in st.session_state:
    st.session_state.attempts = 0
```

> The `New Game` button (line 136) already resets to `0`, so this change makes initialization consistent with reset behaviour.

---

## Summary

| # | File | Line | Issue | Fix |
|---|------|------|-------|-----|
| 1 | `app.py` | 8–10 | Normal/Hard ranges swapped | Swap return values |
| 2 | `app.py` | 96 | `attempts` starts at 1, not 0 | Change initial value to `0` |
=======
# Fix Suggestions

Two bugs identified in the game and their recommended fixes.

---

## Bug 1: Normal and Hard difficulty ranges are swapped

**File:** `app.py` — `get_range_for_difficulty()` (lines 7–10)

**Problem:** Normal returns a range of 1–100 and Hard returns 1–50. Since a larger range is harder, these are backwards from a UX perspective.

**Current code:**
```python
if difficulty == "Normal":
    return 1, 100
if difficulty == "Hard":
    return 1, 50
```

**Fix:** Swap the return values so Hard has the larger range.
```python
if difficulty == "Normal":
    return 1, 50
if difficulty == "Hard":
    return 1, 100
```

---

## Bug 2: Off-by-one error in "Attempts left" display

**File:** `app.py` — session state initialization (line 96) and info display (line 111)

**Problem:** `attempts` is initialized to `1` before any guess is made, so the displayed attempts left is already decremented on a fresh game:

- Sidebar shows: `Attempts allowed: 8`
- Main area shows: `Attempts left: 7` (before any guess)

**Current code:**
```python
if "attempts" not in st.session_state:
    st.session_state.attempts = 1
```

**Fix:** Initialize `attempts` to `0`. The submit handler already increments before processing, so this correctly reflects no attempts used on a fresh game.
```python
if "attempts" not in st.session_state:
    st.session_state.attempts = 0
```

> The `New Game` button (line 136) already resets to `0`, so this change makes initialization consistent with reset behaviour.

---

## Summary

| # | File | Line | Issue | Fix |
|---|------|------|-------|-----|
| 1 | `app.py` | 8–10 | Normal/Hard ranges swapped | Swap return values |
| 2 | `app.py` | 96 | `attempts` starts at 1, not 0 | Change initial value to `0` |
>>>>>>> d7c4556e83b6dc6728177e81deb8bf6a200c20fa
