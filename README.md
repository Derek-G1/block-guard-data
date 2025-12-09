# BlockGuard Community Spam Database

This repository hosts the **public spam phone number database** used by the BlockGuard Android app and other compatible clients.

The goal is to provide an **automatically updated, high-quality list of US spam / scam caller IDs**, in a simple text format that any app or script can consume.

---

## Data Source & Generation

The file [`spam_database.txt`](./spam_database.txt) is generated automatically by a backend script that:

1. Calls the **U.S. Federal Trade Commission (FTC) Do Not Call (DNC) complaints API** for the last _N_ days (currently 30).
2. Extracts the reported **company phone number** from each complaint.
3. Normalizes each phone number to **E.164 format**: `+1XXXXXXXXXX`.
4. Deduplicates and sorts all numbers.
5. Pushes the updated list to this repository’s `main` branch.

This process runs on a schedule (via `cron`) so the list is refreshed regularly with newly reported spam numbers.

> **Note:** This project is **not affiliated with or endorsed by the FTC**. The FTC DNC complaints API is used as a data source; interpretation and usage of that data are the responsibility of this project and its consumers.

---

## File Format

- File: [`spam_database.txt`](./spam_database.txt)
- Encoding: UTF-8
- One number **per line**
- Format: **E.164**, currently only US numbers:

```text
+12146942249
+19035467138
+18446756178
...
