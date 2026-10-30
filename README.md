# Phishing Awareness Training Module

A self-paced, terminal-based course that teaches users to recognize and avoid phishing, social engineering, and related security threats. It includes instructional modules, real-world examples, a knowledge quiz, progress tracking, and a completion certificate.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Course Structure](#course-structure)
- [Completion Criteria](#completion-criteria)
- [Project Structure](#project-structure)
- [Customization](#customization)
- [Known Limitations](#known-limitations)
- [Disclaimer](#disclaimer)

---

## Overview

Phishing remains one of the most common routes into organizations and personal accounts. This module is designed for individuals and teams who need a structured, hands-on introduction to the topic. It runs entirely in the terminal, requires no external dependencies, and can be completed in a single session.

## Key Features

- **Attack taxonomy:** Email, spear, vishing (voice), smishing (SMS), clone phishing, and whaling
- **Indicator reference:** Red flags for emails and websites, alongside signs of legitimate communication
- **Social engineering coverage:** Authority, urgency, baiting, pretexting, quid pro quo, and tailgating, each with an example and a recommended defense
- **Worked examples:** An annotated phishing email and a legitimate counterpart
- **Best-practice guidance:** Password hygiene, email, web, mobile, and workplace security
- **Assessment:** Six scenario-based questions with explanations for every answer
- **Progress tracking:** Section-level completion status and current quiz score
- **Certificate generation:** A text-format certificate saved to disk upon successful completion

## Requirements

| Requirement | Details |
|---|---|
| Python | 3.7 or later |
| Dependencies | None (standard library only) |
| Terminal | Any terminal with ANSI color support. Windows Terminal or PowerShell on Windows 10 and later is recommended. |

## Installation

No installation step is required beyond obtaining the script.

```bash
git clone <repository-url>
cd <repository-directory>
```

Alternatively, download `phishing_training.py` directly and place it in any working directory.

## Usage

Start the program from a terminal:

```bash
# Linux / macOS
python3 phishing_training.py

# Windows
python phishing_training.py
```

The main menu presents the following options:

| Option | Description |
|---|---|
| 1 | Overview: what phishing is and why it is effective |
| 2 | Types of phishing attacks |
| 3 | Email red flags and indicators of legitimacy |
| 4 | Fake website indicators and a pre-submission checklist |
| 5 | Social engineering tactics and defenses |
| 6 | Real-world examples |
| 7 | Best practices and tips |
| 8 | Interactive quiz |
| 9 | View progress |
| 10 | Generate certificate |
| 0 | Exit |

Each instructional section pauses until the user presses Enter, allowing the material to be read at an individual pace.

## Course Structure

The course contains seven instructional sections (options 1 through 7) and one assessment (option 8). Completing a section marks it as done in the progress view.

| Section | Tracked for progress |
|---|---|
| Overview | Yes |
| Types of Attacks | Yes |
| Email Red Flags | Yes |
| Website Red Flags | Yes |
| Social Engineering | Yes |
| Real-World Examples | Yes |
| Best Practices | Yes |
| Quiz | Scored separately |

## Completion Criteria

A certificate is issued only when both conditions are met:

1. At least **6 of the 7** instructional sections have been completed.
2. The quiz score is at least **80%** (5 of 6 questions correct).

When both conditions are satisfied, option 10 displays the certificate and saves it as a text file:

```
phishing_certificate_YYYYMMDD_HHMMSS.txt
```

The file is written to the directory from which the script was launched.

> **Note:** The certificate is a local record of course completion. It is not an accredited or industry-recognized credential.

## Project Structure

```
.
├── phishing_training.py   # Application source (single file)
└── README.md              # Documentation
```

### Code Organization

| Component | Responsibility |
|---|---|
| `Colors` | ANSI escape sequences for terminal formatting |
| `AttackType` | Enumeration of phishing attack categories |
| `PhishingIndicators` | Reference dictionaries for red flags, legitimate signs, and social engineering tactics |
| `QuizQuestion` | Encapsulates a single question, input validation, and feedback |
| `PhishingTrainingModule` | Controls the menu, instructional content, quiz, progress, and certificate |

## Customization

| Task | Location |
|---|---|
| Add or edit quiz questions | `_create_quiz_questions()`. The `correct` field is the 1-based index of the right answer. |
| Change the pass threshold | `run_quiz()` and `generate_certificate()` |
| Change the section requirement for certification | `generate_certificate()` |
| Change the total section count | `show_progress()` |
| Edit instructional content | `PhishingIndicators` class and the corresponding `show_*` methods |

When adding quiz questions, update any threshold logic that depends on the total count.

## Known Limitations

- **Session-scoped progress:** Progress is held in memory and is not persisted. The course must be completed within a single run of the program.
- **Certificate layout:** The certificate border uses fixed-width padding. Modifying the text inside the box may misalign the right edge.
- **Progress accounting:** The quiz is tracked as a separate flag and is not included in the seven-section count.
- **Output location:** Certificates are written to the current working directory rather than a dedicated folder.
- **Platform dependency:** Screen clearing uses `clear` on Linux and macOS and `cls` on Windows, through `os.system`.

## Disclaimer

This software is provided for security awareness education. All example emails, domain names, and phone numbers are illustrative and do not represent real organizations or accounts. Users should always verify unexpected requests through official, independently located channels rather than using contact details supplied in the message itself.
