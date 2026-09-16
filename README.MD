# Password Strength Checker

A browser-based tool that demonstrates why weak passwords are dangerous by actually simulating real attack techniques — dictionary attacks and brute-force attacks — against a password you enter, using SHA-256 hashing.

## Overview & Objectives

Most password strength checkers just show a "weak/strong" label based on rules. This project goes a step further: it **simulates real attacks** (dictionary lookup and brute-force guessing) against the password's SHA-256 hash, right in the browser, and shows how fast a weak password actually falls — making the risk visible and concrete instead of abstract.

**Objectives:**
- Score password strength based on length and character variety
- Simulate a dictionary attack using a common-password wordlist
- Simulate a brute-force attack for short passwords
- Visually demonstrate, via a live "attack log," how quickly weak passwords are cracked

## Features

- **Real-time strength meter** — scores a password as it's typed (length + uppercase/lowercase/numbers/symbols)
- **Dictionary attack simulation** — checks the password's SHA-256 hash against a wordlist of common passwords
- **Brute-force attack simulation** — attempts to crack short passwords (length ≤ 5) character by character
- **Live attack log** — a terminal-style output panel showing each attempt in real time
- **Custom SHA-256 implementation** — hashing done in pure JavaScript, no external crypto library
- **Hacker/terminal-themed UI** — dark theme with monospace styling for a security-tool feel

## Technologies Used

- **HTML5** — structure
- **CSS3** — terminal/dark theme styling
- **JavaScript (vanilla)** — scoring logic, custom SHA-256 hashing, dictionary and brute-force simulation
- No frameworks, no backend, no external libraries — runs entirely client-side in the browser

## Installation / Setup Instructions

No installation needed:

1. Clone or download this repository
   ```
   git clone https://github.com/am-cybersec/Password-Strength-Checker.git
   ```
2. Open `password_strength_analyzer.html` directly in any modern browser (Chrome, Edge, Firefox)

That's it — everything runs client-side.

## Usage

1. Open the tool in your browser
2. Type a password into the input field
3. Watch the strength meter update in real time
4. Click the analyze/attack button to run the dictionary and brute-force simulations
5. Watch the attack log panel show each attempt and whether/how fast the password was "cracked"

*(Add 2–3 screenshots here: the main UI, a weak password being cracked, and a strong password surviving both attacks.)*

## System Workflow / Architecture

```
User enters password
        ↓
SHA-256 hash generated (custom JS implementation)
        ↓
Strength score calculated (length + character variety)
        ↓
Dictionary Attack Simulation
   → hash compared against common-password wordlist
   → if match found → cracked, attempt logged
        ↓
Brute-Force Attack Simulation (if password length ≤ 5)
   → generates and hashes character combinations
   → compares against target hash
   → if match found → cracked, attempt logged
        ↓
Result displayed: strength rating + attack outcome + live log
```

## Testing & Results

| Password Tested | Length | Dictionary Attack | Brute-Force Attack | Result |
|---|---|---|---|---|
| `admin` | 5 | Cracked instantly | — | Weak |
| `x9k2` | 4 | Not found | Cracked in a few ms | Weak |
| `P@ssw0rd` | 8 | Not found | Not attempted (length > 5) | Medium |
| `T9!kLmz#4qP` | 11 | Not found | Not attempted (length > 5) | Strong |

## Challenges & Future Improvements

**Challenges faced:**
- Implementing SHA-256 hashing manually in JavaScript without relying on any external crypto library
- Keeping the brute-force simulation realistic while still fast enough to run smoothly in-browser (limited to short passwords)

**Future improvements:**
- Expand the dictionary wordlist for a more realistic simulation
- Extend brute-force simulation to longer passwords using Web Workers (to avoid freezing the UI)
- Add password-improvement suggestions based on which attack succeeded
- Add an entropy-based scoring option alongside the rule-based scorer

## Conclusion

This project demonstrates, hands-on, why password strength rules exist — by actually attacking the password instead of just scoring it. It reinforced practical skills in JavaScript, cryptographic hashing, and understanding common password-cracking techniques from an attacker's perspective.

## References

- OWASP Password Storage Cheat Sheet
- NIST Digital Identity Guidelines (SP 800-63B) — password policy recommendations
- SHA-256 (Secure Hash Algorithm 2) specification

## Author

Areeba Minahil — Cybersecurity Intern, Zynvex Solutions
