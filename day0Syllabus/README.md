# 🐍 30 Days of Python — for DevOps (Advanced Track)

> Goal: 30 din me Python ko **DevOps engineer ki nazar se** seekhna — sirf syntax nahi, balki real automation: files, logs, servers, APIs, AWS, Docker, Kubernetes, testing, CI/CD.

---

## 📌 Pehle ek honest baat (realistic expectation)

- 30 din me tum **"working fluency"** le sakte ho — matlab scripts likhna, tools banana, automation karna.
- **"Expert/Senior level"** 30 din me nahi hota. Wo 1-2 saal ke real kaam se aata hai.
- Agar daily **2.5–3.5 ghante** + **khud code likhoge (copy-paste nahi)** to 30 din ke baad tum ye kar paoge:
  - System health-check, log analyzer, backup scripts
  - AWS (boto3) se resources audit/cleanup
  - Docker/K8s ko Python se control
  - CLI tools + FastAPI webhook + tests + CI
  - 4 mini projects + 1 capstone GitHub par
- Ye resume me **real proof** banega, "Python seekha" likhne se zyada.

---

## 🎯 Is course ke baad tum kya bana paoge

| # | Output | Skill |
|---|--------|-------|
| 1 | Log Analyzer | file handling, regex, collections |
| 2 | System Health CLI | psutil, argparse, subprocess |
| 3 | AWS Resource Auditor | boto3, JSON, reports |
| 4 | Docker/K8s Helper Scripts | docker SDK, kubernetes client |
| 5 | Capstone: DevOps Toolkit | CLI + API + tests + Docker + CI |

---

## 🧰 Tools (sab free)

- OS: Linux Mint XFCE
- Python 3.10+ (`python3 --version`)
- Git + GitHub account
- Editor: VS Code ya Geany/Vim (jo comfortable ho)
- Terminal: XFCE Terminal
- AWS Free Tier account (Week 3 se)
- Docker (Week 3 se)

---

## 📁 Repo Structure

```
30-day-of-python/
├── README.md              ← ye syllabus file
├── day-01/
│   ├── README.md          ← theory + practice questions
│   ├── q01.py
│   ├── q02.py
│   └── ...
├── day-02/
│   ├── README.md
│   └── ...
├── ...
├── projects/
│   ├── log-analyzer/
│   ├── health-check-cli/
│   ├── aws-auditor/
│   └── devops-toolkit/
└── .gitignore
```

---

## ⏰ Daily Routine (roz same format)

| Time | Kaam |
|------|------|
| 30 min | README ka theory padhna (samajh ke, ratta nahi) |
| 60 min | Examples khud type karke run karna |
| 60–90 min | Practice questions solve karna (`.py` files me) |
| 15 min | Git commit + push + 3 line notes: "aaj kya seekha / kahan atka" |

### Golden Rules
1. **Khud likho.** AI se code mat banwao. Atak jao to error padho, phir pucho.
2. Har question ki alag file: `q01.py`, `q02.py`.
3. Roz commit. Message format: `day-05: file handling done`.
4. Jo samajh na aaye usko "Doubts" section me likho, kal solve karo.
5. Har 7th day = revision + mini project. Skip mat karna.

---

## 🗓️ 30-Day Syllabus (Day-wise)

### 🟢 WEEK 1 — Python Foundations (DevOps flavour ke saath)

| Day | Topic | Kya seekhenge |
|-----|-------|---------------|
| **1** | Setup + Basics | Python kya hai, Linux Mint setup, venv, pip, Git repo, variables, data types, type conversion, input/output, operators, f-strings |
| **2** | Control Flow + Functions basics | if/elif/else, for/while, break/continue, range, enumerate, functions, return, default args |
| **3** | Data Structures | list, tuple, set, dict deep dive, slicing, methods, comprehensions, nested data (JSON jaisa) |
| **4** | Advanced Functions | `*args/**kwargs`, lambda, map/filter/sorted, scope (LEGB), closures, decorators, generators |
| **5** | Files + Paths | open/read/write, `with`, `pathlib`, `os`, `shutil`, CSV, JSON, YAML |
| **6** | Errors + Logging | try/except/finally, custom exceptions, `logging` module, log levels, log to file |
| **7** | OOP + Revision + **Mini Project 1** | class, object, `__init__`, inheritance, dunder methods, dataclass → **Log Analyzer v1** |

### 🔵 WEEK 2 — System Automation

| Day | Topic | Kya seekhenge |
|-----|-------|---------------|
| **8** | `os`, `sys`, `subprocess` | shell commands Python se chalana, stdout/stderr, return code, exit codes |
| **9** | CLI Tools | `argparse`, `click`, env variables, `.env`, config files |
| **10** | Regex + Log Parsing | `re` module, groups, findall, nginx/ssh log parsing, `collections.Counter` |
| **11** | Config Formats + Templating | JSON/YAML/TOML, `PyYAML`, Jinja2 templates (nginx.conf, docker-compose generate) |
| **12** | Time + Scheduling | `datetime`, timezone, timedelta, `time.sleep`, cron vs Python scheduler, backup rotation |
| **13** | Networking Basics | `socket`, `ipaddress`, port check, DNS lookup, `requests` intro, health-check |
| **14** | Revision + **Mini Project 2** | **System Health Check CLI** (psutil + argparse + logging) |

### 🟠 WEEK 3 — Cloud & DevOps Tools

| Day | Topic | Kya seekhenge |
|-----|-------|---------------|
| **15** | REST APIs | `requests` deep dive, auth headers, retries, timeouts, GitHub API |
| **16** | AWS boto3 — Part 1 | session, S3 (upload/download/list), EC2 (list/start/stop) |
| **17** | AWS boto3 — Part 2 | IAM basics, CloudWatch, pagination, tagging, Lambda intro |
| **18** | Docker with Python | Docker SDK, containers/images list, run, logs, cleanup |
| **19** | SSH + Remote Automation | `paramiko`, run commands on servers, file transfer, Ansible + Python overview |
| **20** | Kubernetes with Python | `kubernetes` client, pods/deployments list, logs, scale |
| **21** | Revision + **Mini Project 3** | **AWS Resource Auditor** (unused EBS, untagged EC2, report in JSON/CSV) |

### 🔴 WEEK 4 — Advanced & Production Style

| Day | Topic | Kya seekhenge |
|-----|-------|---------------|
| **22** | Testing | `pytest`, fixtures, parametrize, mocking (`unittest.mock`), `moto` for AWS mock |
| **23** | Concurrency | threading, multiprocessing, `concurrent.futures`, `asyncio` basics |
| **24** | FastAPI for DevOps | health endpoint, webhook receiver, Pydantic, background tasks |
| **25** | Monitoring | `psutil`, Prometheus client, custom exporter, alert script (Slack/Email) |
| **26** | Code Quality + CI | type hints, `ruff`, `black`, pre-commit, GitHub Actions for Python |
| **27** | Packaging + Dockerizing | `pyproject.toml`, entry points, build CLI package, Dockerfile for Python app |
| **28** | Security + Best Practices | secrets handling, `.env`, no hardcoded keys, input validation, design patterns (basic) |
| **29** | **Capstone — Build** | DevOps Toolkit: CLI + modules + tests |
| **30** | **Capstone — Ship** | Docker + CI + README + LinkedIn post + resume bullets |

---

## ✅ Progress Tracker

- [ ] Day 01 — Setup + Basics
- [ ] Day 02 — Control Flow + Functions
- [ ] Day 03 — Data Structures
- [ ] Day 04 — Advanced Functions
- [ ] Day 05 — Files + Paths
- [ ] Day 06 — Errors + Logging
- [ ] Day 07 — OOP + Mini Project 1
- [ ] Day 08 — os/sys/subprocess
- [ ] Day 09 — CLI Tools
- [ ] Day 10 — Regex + Log Parsing
- [ ] Day 11 — Config + Templating
- [ ] Day 12 — Time + Scheduling
- [ ] Day 13 — Networking
- [ ] Day 14 — Mini Project 2
- [ ] Day 15 — REST APIs
- [ ] Day 16 — boto3 Part 1
- [ ] Day 17 — boto3 Part 2
- [ ] Day 18 — Docker SDK
- [ ] Day 19 — SSH Automation
- [ ] Day 20 — Kubernetes Client
- [ ] Day 21 — Mini Project 3
- [ ] Day 22 — Testing
- [ ] Day 23 — Concurrency
- [ ] Day 24 — FastAPI
- [ ] Day 25 — Monitoring
- [ ] Day 26 — Code Quality + CI
- [ ] Day 27 — Packaging + Docker
- [ ] Day 28 — Security
- [ ] Day 29 — Capstone Build
- [ ] Day 30 — Capstone Ship

---

## 🧭 Roadmap ka logic (kyun ye order?)

Analogy: **Ghar banane jaisa**
- Week 1 = **neev (foundation)** — bina iske sab girega.
- Week 2 = **deewarein aur wiring** — system ke saath kaam karna.
- Week 3 = **furniture aur appliances** — AWS, Docker, K8s (asli DevOps).
- Week 4 = **polish + safety** — testing, CI, security, packaging.

---

## 🔗 Helpful References

- Python docs: https://docs.python.org/3/
- roadmap.sh/python
- Real Python (tutorials)
- boto3 docs: https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

---

## 📝 Author

Harsh Yadav — BCA 3rd Year | Aspiring DevOps Engineer
