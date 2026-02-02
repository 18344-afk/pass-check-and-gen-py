# Password Tool (Generator & Strength Analyzer)

A comprehensive Python utility designed to generate cryptographically secure passwords and analyze the strength of existing credentials. This project offers both a modern Graphical User Interface (GUI) and a lightweight Command Line Interface (CLI).

##  Features

### 1. Secure Password Generator
* **Cryptographically Secure:** Uses Python's `secrets` module (SystemRandom) rather than the standard pseudo-random number generator, making passwords suitable for security-sensitive applications.
* **Customizable Complexity:** Users can toggle Uppercase (A-Z), Lowercase (a-z), Digits (0-9), and Symbols (!@#$).
* **Smart Logic:** Ensures at least one character from every selected category is included in the final password.

### 2. Strength Checker
* **Pattern Analysis:** Evaluates passwords based on length and the presence of mixed character types using Regular Expressions (Regex).
* **Common Password Detection:** Checks against a blacklist of common weak passwords (e.g., "admin", "qwerty").
* **Scoring System:** Returns a rating of "Weak", "Medium", or "Strong" based on a cumulative score.

### 3. User Interface Options
* **GUI Mode:** Built with `tkinter` and `ttk`, featuring a tabbed layout, slider-based length selection, and one-click clipboard copying.
* **CLI Mode:** A simple interactive terminal menu for quick operations without launching a window.

##  Project Structure

| File | Description |
| :--- | :--- |
| `gui.py` | The main entry point for the Graphical User Interface. Handles window rendering, tabs, and user input events. |
| `main.py` | The entry point for the Command Line Interface. Provides a text-based menu loop. |
| `pass_gen.py` | The backend logic module for generating passwords. Handles character set building and randomization. |
| `pass_check.py` | The backend logic module for grading password strength. Contains the scoring algorithms and validation rules. |

##  Prerequisites

* **Python 3.6+**
* **Tkinter:** Usually included with standard Python installations.
    * *Linux Users:* If the GUI fails to launch, install via `sudo apt-get install python3-tk`.

##  Installation & Usage

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/yourusername/password-tool.git](https://github.com/yourusername/password-tool.git)
    cd password-tool
    ```

2.  **To Run the GUI (Recommended)**
    Launch the visual interface with tabs for generation and checking.
    ```bash
    python gui.py
    ```

3.  **To Run the CLI**
    Launch the text-based terminal menu.
    ```bash
    python main.py
    ```

## ⚙️ Technical Details

### Generation Logic
The generator builds a pool of allowed characters based on user selection. It forces the inclusion of at least one character from each selected set (e.g., ensuring a symbol exists if "Symbols" is checked) before filling the rest of the length randomly and shuffling the result.

### Scoring Logic
The strength checker starts with a score of 0.
* **+1 point** for length ≥ 8.
* **+2 points** for length ≥ 12.
* **+1 point each** for having Uppercase, Lowercase, Digits, or Symbols.
* **Fail Condition:** If the password is in the internal common password list, it is immediately flagged as "Very Weak".
