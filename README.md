# 💡 Utility Billing System (C)

A console-based utility billing system written in C that calculates water/electricity bills for **Residential** and **Commercial** customers. The program features a simple login system, tiered billing rates, penalty computation for late payments, and a basic cash payment processor.

---

## 📋 Features

- **User Login** – Simple credential check before accessing the system
- **Rate Class Selection** – Choose between Residential or Commercial billing
- **Tiered Billing Rates** – Bill is calculated based on units consumed using progressive rate tiers
- **Tax & FCDA Computation** – Automatically computes Franchise Tax and FCDA adjustments
- **Due Date Penalty** – Adds a 10% surcharge for payments made after the due date
- **Cash Payment Handler** – Accepts cash input and returns change or prompts for more cash if insufficient

---

## 🛠️ How to Compile & Run

Make sure you have GCC installed.

```bash
gcc billing.c -o billing
./billing
```

> On Windows, use `billing.exe` after compiling with MinGW.

---

## 🔐 Login Credentials

| Field    | Value     |
|----------|-----------|
| Username | *(any name except `anonymous`)* |
| Password | `12345`   |

---

## 🏠 Residential Billing Rates

| Units Consumed (m³) | Rate per m³ | FCDA   | Tax  |
|---------------------|-------------|--------|------|
| ≤ 20                | ₱12.60      | 1.0%   | 2.0% |
| 21 – 30             | ₱13.75      | 2.0%   | 2.0% |
| 31 – 40             | ₱14.95      | 3.0%   | 2.0% |
| 41 – 50             | ₱16.30      | 3.0%   | 2.0% |
| > 50                | ₱17.95      | 10.0%  | 2.0% |

- **Penalty (after due date):** 10% of the total bill

---

## 🏢 Commercial Billing Rates

| Units Consumed (m³) | Formula                       |
|---------------------|-------------------------------|
| ≤ 50                | `units × ₱12.60`              |
| ≤ 100               | `₱25 + (units − 5) × ₱3`     |
| ≤ 150               | `₱50 + (units − 10) × ₱5`    |
| ≤ 200               | `₱75 + (units − 15) × ₱7`    |
| > 200               | `₱150 + (units − 20) × ₱9`   |

- **Late payment rate:** Total bill × 2.5

---

## 📁 Project Structure

```
billing-system/
│
└── billing.c       # Main source file (login, residential, commercial logic)
```

---

## ⚠️ Known Limitations

- Login credentials are hardcoded (not secure for production use)
- Customer details (name, address, billing month) are hardcoded — not entered dynamically
- Uses `goto` statements (not recommended in modern C; consider refactoring with loops)
- No file I/O — billing records are not saved between sessions
- Password stored and compared as a plain integer

---

## 🚀 Possible Improvements

- Dynamic customer data input (name, address, billing month)
- Secure password handling
- File-based record keeping (save/load billing history)
- Replace `goto` with proper loop structures
- Input validation for non-numeric entries

---

## 👨‍💻 Author

Developed as a beginner C programming project to practice conditionals, functions, and switch-case logic.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
