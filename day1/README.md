# 📅 Day 01 — Setup + Python Basics

> **Aaj ka goal:** Python install/setup check karna, Git repo banana, aur Python ke basic building blocks (variables, data types, input/output, operators, f-strings) samajhna — DevOps ke examples ke saath.

⏱️ **Time plan:** Theory 40 min → Examples 60 min → Practice 80 min → Git push 10 min

---

## 📚 Aaj kya-kya padhenge (Index)

1. Python kya hai? DevOps me kyun?
2. Setup on Linux Mint (Python, pip, venv, Git)
3. Repo setup (`30-day-of-python`)
4. Pehla program + Python kaise chalta hai
5. Comments, Indentation, PEP8
6. Variables
7. Data Types
8. Type Conversion (Casting)
9. Input / Output
10. Operators
11. Strings (basic) + f-strings
12. Truthy / Falsy
13. DevOps flavour examples
14. Common Errors
15. Practice Questions (60+)
16. Cheat Sheet + Checklist + Git push

---

## 1️⃣ Python kya hai? DevOps me kyun?

**Definition:** Python ek **high-level, interpreted, dynamically-typed, general-purpose** programming language hai.

| Term | Matlab | Analogy |
|------|--------|---------|
| High-level | Insaan ki bhasha ke kareeb, machine details chhupi hui | Car chalana — engine ke andar ka kaam nahi dekhna |
| Interpreted | Code line-by-line chalta hai, compile step alag nahi | Live translator jo ek-ek line bolta jata hai |
| Dynamically-typed | Variable ka type khud decide hota hai | Dabba jisme kuch bhi rakh sakte ho, label khud lag jata hai |
| General-purpose | Web, AI, automation, scripts — sab | Swiss army knife |

### DevOps me Python kyun?
- **Automation:** repetitive kaam (backup, cleanup, deploy) script se.
- **Glue language:** Bash, APIs, cloud, tools — sabko jodta hai.
- **Libraries:** `boto3` (AWS), `docker`, `kubernetes`, `paramiko` (SSH), `requests` (API).
- **Readable:** Team me koi bhi padh sakta hai.
- **Tools khud Python me bane hain:** Ansible, many AWS CLI parts, Salt, etc.

### Bash vs Python (kab kya?)
| Bash | Python |
|------|--------|
| 5-10 line ka chhota system kaam | Logic, loops, data, error handling zyada |
| Commands chain karna | API, JSON, cloud SDK |
| Complex data (JSON/dict) mushkil | Easy |

---

## 2️⃣ Setup on Linux Mint

### 2.1 Python version check

```bash
python3 --version
```
**Line-by-line:**
- `python3` → Python interpreter ko call karta hai (Linux par `python` ki jagah `python3` safe hai).
- `--version` → sirf version dikhao, program mat chalao.
- **Expected output:** `Python 3.10.x` ya usse upar.

### 2.2 pip check/install

```bash
pip3 --version
sudo apt update
sudo apt install python3-pip python3-venv -y
```
**Line-by-line:**
- `pip3 --version` → pip (Python ka package installer, mobile ke Play Store jaisa) hai ya nahi.
- `sudo apt update` → Mint ki package list refresh karo (menu card update).
- `sudo apt install python3-pip python3-venv -y` → pip aur venv install karo. `-y` = har sawal par "yes".

### 2.3 Virtual Environment (venv) — **bahut zaroori**

**Definition:** venv ek **alag, isolated Python environment** hai jisme project ke packages alag rehte hain.

**Analogy:** Har project ke liye **alag tiffin box**. Agar sab ek hi dabbe me daloge to daal-sabzi-meetha sab mix ho jayega (version conflict).

```bash
cd ~/30-day-of-python
python3 -m venv venv
source venv/bin/activate
```
**Line-by-line:**
- `cd ~/30-day-of-python` → repo folder me jao (`~` = home folder).
- `python3 -m venv venv` → `-m` matlab "module chalao"; `venv` module se `venv` naam ka folder banao (andar alag Python copy).
- `source venv/bin/activate` → environment ON karo. Terminal me `(venv)` dikhega.

```bash
pip install requests
pip list
pip freeze > requirements.txt
deactivate
```
**Line-by-line:**
- `pip install requests` → `requests` library sirf is venv me install.
- `pip list` → installed packages ki list.
- `pip freeze > requirements.txt` → exact versions file me save (`>` = output ko file me daalo).
- `deactivate` → venv se bahar.

> ⚠️ `venv/` folder ko Git me push **mat** karna. `.gitignore` me daalna (Section 3).

### 2.4 Git setup

```bash
sudo apt install git -y
git config --global user.name "Harsh Yadav"
git config --global user.email "your-email@example.com"
git --version
```
**Line-by-line:**
- `apt install git` → Git install.
- `git config --global user.name` → commits me tumhara naam.
- `git config --global user.email` → commits me email (GitHub wala email use karo).
- `git --version` → check.

---

## 3️⃣ Repo Setup

### GitHub par
1. GitHub → **New repository** → naam: `30-day-of-python` → Public → Create.

### Local terminal me

```bash
mkdir -p ~/30-day-of-python/day-01
cd ~/30-day-of-python
git init
```
**Line-by-line:**
- `mkdir -p` → folder banao; `-p` matlab parent bhi ban jaye, already ho to error nahi.
- `git init` → is folder me Git tracking shuru.

`.gitignore` file banao:

```bash
cat > .gitignore << 'EOF'
venv/
__pycache__/
*.pyc
.env
.vscode/
EOF
```
**Line-by-line:**
- `cat > .gitignore << 'EOF' ... EOF` → jo bhi EOF tak likha hai, wo `.gitignore` file me ja jayega.
- `venv/` → virtual env push nahi hoga.
- `__pycache__/`, `*.pyc` → Python ki auto-generated cache files.
- `.env` → **secrets kabhi push nahi karte**.

Pehla push:

```bash
git add .
git commit -m "day-00: repo setup"
git branch -M main
git remote add origin https://github.com/<tumhara-username>/30-day-of-python.git
git push -u origin main
```
**Line-by-line:**
- `git add .` → sab changes staging me (parcel me saaman rakhna).
- `git commit -m "..."` → parcel seal + label (snapshot save).
- `git branch -M main` → branch ka naam `main` kar do.
- `git remote add origin <url>` → GitHub repo ka address "origin" naam se yaad rakho.
- `git push -u origin main` → local commits GitHub par bhejo; `-u` se aage sirf `git push` chalega.

> GitHub password ki jagah **Personal Access Token (PAT)** ya SSH key lagti hai. Agar atko to bolo, alag se setup guide dunga.

---

## 4️⃣ Pehla Program + Python kaise chalta hai

`day-01/q01.py`:

```python
print("Hello, DevOps World!")
```

Run:
```bash
python3 day-01/q01.py
```
**Line-by-line:**
- `print(...)` → built-in function, screen par text dikhata hai.
- `"Hello..."` → string (text), quotes me.
- Run command: `python3` interpreter, uske baad file ka path.

### Python code kaise chalta hai? (flow)

```
.py file → Interpreter padhta hai → Bytecode (.pyc) → Python Virtual Machine chalata hai → Output
```
**Analogy:** Tum Hindi me likhte ho, interpreter usko "beech ki bhasha" (bytecode) me badalta hai, aur PVM (machine ka translator) ek-ek step chalata hai.

### Interactive mode (REPL)
```bash
python3
>>> 2 + 3
5
>>> print("hi")
hi
>>> exit()
```
Chhote experiments ke liye best (calculator jaisa).

---

## 5️⃣ Comments, Indentation, PEP8

### Comments
```python
# Ye single-line comment hai (Python ignore karta hai)

"""
Ye multi-line string hai,
aksar docstring/multi-line comment ki tarah use hota hai.
"""
```

### Indentation (Python ki jaan)
Python me `{ }` nahi hote, **spaces** se block banta hai.

```python
if True:
    print("andar hai")   # 4 spaces
print("bahar hai")
```
- Standard: **4 spaces** (tab aur space mix mat karo).
- Galat indentation → `IndentationError`.

**Analogy:** Book me paragraph ka gap — gap se hi pata chalta hai kaunsi line kis block ki hai.

### PEP8 (style guide) — basics
| Cheez | Rule | Example |
|-------|------|---------|
| Variable/function | `snake_case` | `server_name` |
| Constant | `UPPER_CASE` | `MAX_RETRIES` |
| Class | `PascalCase` | `ServerMonitor` |
| Line length | ~79-88 chars | — |
| Operators ke aas-paas | space | `a = b + c` |

---

## 6️⃣ Variables

**Definition:** Variable ek **naam (label)** hai jo memory me rakhi value ko point karta hai.

**Analogy:** Variable = **dabba par likha label**. `name = "Harsh"` matlab "Harsh" wale dabbe par `name` ka sticker laga.

```python
server_name = "web-01"
port = 8080
cpu_usage = 73.5
is_running = True
```

### Rules
- Letters, digits, underscore (`_`) allowed. **Digit se shuru nahi.**
- Space nahi, special chars (`-`, `@`, `$`) nahi.
- Case-sensitive: `Name` aur `name` alag.
- Keywords nahi: `if`, `for`, `class`, `def`, `True`, `None` etc.

```python
user1 = "ok"      # ✅
_temp = 5         # ✅
1user = "bad"     # ❌ SyntaxError
my-var = 3        # ❌ SyntaxError
class = "x"       # ❌ keyword
```

Keywords dekhne ke liye:
```python
import keyword
print(keyword.kwlist)
```

### Multiple assignment
```python
a, b, c = 1, 2, 3          # alag-alag values
x = y = z = 0              # sab ko same value
a, b = b, a                # swap (Python ka magic!)
```

### Constants (convention)
Python me real constant nahi hota, par convention:
```python
MAX_RETRIES = 3
DEFAULT_PORT = 22
```

### `id()` aur memory idea
```python
a = 10
b = a
print(id(a), id(b))   # same address — dono ek hi object ko point kar rahe
```

### `del`
```python
x = 5
del x     # variable hata diya
```

---

## 7️⃣ Data Types

### Core types (aaj ke)

| Type | Naam | Example | DevOps use |
|------|------|---------|------------|
| `int` | Integer | `22`, `-5` | port, count |
| `float` | Decimal | `73.5` | CPU %, latency |
| `str` | String | `"nginx"` | hostname, path |
| `bool` | Boolean | `True/False` | service up/down |
| `NoneType` | None | `None` | "koi value nahi" |
| `complex` | Complex | `2+3j` | (kam use, bas jaan lo) |

(`list`, `tuple`, `set`, `dict` → **Day 3** me deep.)

```python
port = 8080
cpu = 73.5
service = "nginx"
running = True
backup_path = None

print(type(port))        # <class 'int'>
print(type(cpu))         # <class 'float'>
print(type(service))     # <class 'str'>
print(type(running))     # <class 'bool'>
print(type(backup_path)) # <class 'NoneType'>
```
**Line-by-line:** `type(x)` batata hai x kis type ka hai.

### `isinstance()`
```python
print(isinstance(port, int))     # True
print(isinstance(cpu, (int, float)))  # True — tuple me kisi ek se match
```

### Dynamic typing
```python
x = 10        # int
x = "ten"     # ab str — allowed
```
Python me type change ho sakta hai. **Faida:** flexible. **Nuksan:** bugs chhup sakte hain (isliye Day 26 me type hints seekhenge).

### Numbers ki details
```python
big = 1_000_000          # underscore se padhna aasan
print(10 / 3)            # 3.3333333333333335
print(0.1 + 0.2)         # 0.30000000000000004  (float precision issue)
print(round(0.1 + 0.2, 2))  # 0.3
```
**Yaad rakho:** float exact nahi hote (computer binary me store karta hai).

### Boolean
```python
print(True + True)   # 2 (True = 1, False = 0)
```

### None
```python
result = None
print(result is None)   # True
```

---

## 8️⃣ Type Conversion (Casting)

```python
int("25")        # 25
int(3.9)         # 3   (decimal kat jata hai, round nahi)
float("2.5")     # 2.5
str(100)         # "100"
bool(0)          # False
bool("hello")    # True
int("abc")       # ❌ ValueError
```

### Implicit vs Explicit
```python
print(5 + 2.0)        # 7.0  — Python khud int→float (implicit)
print(int("5") + 2)   # 7    — tumne khud convert kiya (explicit)
```

### Common galti
```python
age = input("Age: ")    # input hamesha str deta hai!
print(age + 1)          # ❌ TypeError
print(int(age) + 1)     # ✅
```

---

## 9️⃣ Input / Output

### `print()` ki power

```python
print("a", "b", "c")                 # a b c
print("a", "b", "c", sep="-")        # a-b-c
print("Loading", end="...")          # newline nahi aayega
print("done")                        # Loading...done
```
**Line-by-line:**
- `sep` → items ke beech kya lagana (default space).
- `end` → print ke baad kya (default `\n` = new line).

### Escape characters
| Code | Matlab |
|------|--------|
| `\n` | new line |
| `\t` | tab |
| `\\` | ek backslash |
| `\"` | double quote |

```python
print("Line1\nLine2")
print("Name\tPort")
print("Path: C:\\Users")
print(r"C:\new\folder")    # r = raw string, escape ignore
```

### `input()`
```python
name = input("Tumhara naam? ")
print("Namaste,", name)
```
- `input("prompt")` user se text leta hai, **hamesha `str`** return karta hai.

### Multi-line string
```python
banner = """
=====================
   DEVOPS TOOL v1.0
=====================
"""
print(banner)
```

---

## 🔟 Operators

### 10.1 Arithmetic
| Op | Naam | Example | Result |
|----|------|---------|--------|
| `+` | add | `7 + 2` | 9 |
| `-` | subtract | `7 - 2` | 5 |
| `*` | multiply | `7 * 2` | 14 |
| `/` | divide (float) | `7 / 2` | 3.5 |
| `//` | floor divide | `7 // 2` | 3 |
| `%` | modulus (remainder) | `7 % 2` | 1 |
| `**` | power | `7 ** 2` | 49 |

DevOps use: `%` → even/odd, "har 5th retry par kuch karo". `//` → seconds ko minutes me.

```python
seconds = 3725
minutes = seconds // 60      # 62
rem = seconds % 60           # 5
print(f"{minutes} min {rem} sec")
```

### 10.2 Comparison (result hamesha `bool`)
`==`, `!=`, `>`, `<`, `>=`, `<=`

```python
cpu = 85
print(cpu > 80)      # True
print(cpu == 100)    # False
```
> `=` assignment hai, `==` comparison. Dono me confuse mat hona.

### 10.3 Logical
| Op | Matlab |
|----|--------|
| `and` | dono True ho tabhi True |
| `or` | koi ek True ho to True |
| `not` | ulta |

```python
cpu, mem = 85, 60
print(cpu > 80 and mem > 80)   # False
print(cpu > 80 or mem > 80)    # True
print(not (cpu > 80))          # False
```
**Analogy:** `and` = "chai AND biscuit dono chahiye"; `or` = "chai YA coffee, kuch bhi chalega".

### 10.4 Assignment
`=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`

```python
count = 0
count += 1     # count = count + 1
count *= 5     # 5
```

### 10.5 Membership
```python
print("ng" in "nginx")          # True
print("x" not in "nginx")       # False
```

### 10.6 Identity
```python
a = None
print(a is None)        # True (None check ke liye hamesha `is`)
print(a is not None)    # False
```
> `==` value compare karta hai, `is` same object compare karta hai.

### 10.7 Operator precedence (kaun pehle?)
Upar se neeche (high → low):
1. `()`
2. `**`
3. `*  /  //  %`
4. `+  -`
5. Comparison (`<`, `==`, ...)
6. `not` → `and` → `or`

```python
print(2 + 3 * 4)       # 14
print((2 + 3) * 4)     # 20
print(2 ** 3 ** 2)     # 512 (right to left)
```

### 10.8 Bitwise (jaan lo, advanced baad me)
`&`, `|`, `^`, `~`, `<<`, `>>` — permissions aur IP/subnet maths me kaam aate hain.

---

## 1️⃣1️⃣ Strings (basic) + f-strings

```python
s = "  Nginx Server  "
print(len(s))            # length
print(s.strip())         # "Nginx Server"   (aas-paas ke space hatao)
print(s.upper())         # "  NGINX SERVER  "
print(s.lower())
print(s.title())
print(s.replace("Nginx", "Apache"))
print("a,b,c".split(","))        # ['a', 'b', 'c']
print("-".join(["a", "b", "c"])) # a-b-c
print("nginx".startswith("ng"))  # True
print("nginx".endswith("x"))     # True
print("nginx".find("g"))         # 1  (nahi mila to -1)
print("nginx".count("n"))        # 2
```

### Indexing + slicing (intro)
```python
word = "devops"
print(word[0])      # d
print(word[-1])     # s
print(word[0:3])    # dev   (end index include nahi)
print(word[::-1])   # spoved (reverse)
```
```
 d  e  v  o  p  s
 0  1  2  3  4  5
-6 -5 -4 -3 -2 -1
```

### Strings immutable hoti hain
```python
w = "devops"
w[0] = "D"      # ❌ TypeError
w = "D" + w[1:] # ✅ naya string banao
```

### f-string (formatting ka best tareeka)
```python
host = "web-01"
cpu = 73.456
print(f"Host: {host}, CPU: {cpu:.1f}%")     # Host: web-01, CPU: 73.5%
print(f"{5 * 4}")                            # 20 — expression bhi chalta hai
print(f"{host!r}")                           # 'web-01'
print(f"{1234567:,}")                        # 1,234,567
print(f"{host:>10}|{host:<10}|{host:^10}|")   # alignment
print(f"{cpu=}")                             # cpu=73.456 (debug trick)
```
**Line-by-line:**
- `f"..."` → f-string; `{}` ke andar Python code chalta hai.
- `:.1f` → 1 decimal place.
- `:>10` right align, `:<10` left, `:^10` center (width 10).

---

## 1️⃣2️⃣ Truthy / Falsy

**Falsy values:** `False`, `None`, `0`, `0.0`, `""`, `[]`, `{}`, `()`, `set()`
Baaki sab **Truthy**.

```python
print(bool(""))        # False
print(bool("0"))       # True  (non-empty string!)
print(bool(0))         # False
print(bool([]))        # False
```
Use: `if username:` → "username khali nahi hai to".

---

## 1️⃣3️⃣ DevOps Flavour Examples

### Example 1: Server info card
```python
hostname = "prod-web-01"
ip = "10.0.1.15"
port = 443
cpu = 67.8
is_up = True

print("=" * 30)
print(f"Host   : {hostname}")
print(f"IP     : {ip}:{port}")
print(f"CPU    : {cpu:.1f}%")
print(f"Status : {'UP' if is_up else 'DOWN'}")
print("=" * 30)
```
(`'UP' if is_up else 'DOWN'` = ternary, Day 2 me detail.)

### Example 2: Disk usage percent
```python
total_gb = 500
used_gb = 365
percent = (used_gb / total_gb) * 100
print(f"Disk used: {percent:.2f}%")
print("Alert!" if percent > 80 else "OK")
```

### Example 3: Seconds → uptime
```python
uptime = 987654
days = uptime // 86400
hours = (uptime % 86400) // 3600
minutes = (uptime % 3600) // 60
print(f"{days}d {hours}h {minutes}m")
```

### Example 4: Port check logic (bina network)
```python
port = 22
is_ssh = port == 22
is_web = port in (80, 443)
print(is_ssh, is_web)
```

### Example 5: Build version string
```python
major, minor, patch = 1, 4, 2
version = f"v{major}.{minor}.{patch}"
print(version)
```

---

## 1️⃣4️⃣ Common Errors (Isse seekho, darro mat)

| Error | Kab aata hai | Fix |
|-------|--------------|-----|
| `SyntaxError` | quotes/bracket band nahi kiya, galat syntax | line dhyan se dekho |
| `IndentationError` | spaces galat | 4 spaces use karo |
| `NameError` | variable define hi nahi kiya / spelling galat | naam check |
| `TypeError` | `"5" + 5` jaisa mix | type convert |
| `ValueError` | `int("abc")` | sahi value do |
| `ZeroDivisionError` | `5 / 0` | divisor check |

**Traceback padhna sikho:** error ke **aakhri line** se shuru karo — wahi batata hai kya galat hai, upar ki lines batati hain kahan.

---

# 🧪 15️⃣ PRACTICE QUESTIONS

> Har question ka alag file banao: `q01.py`, `q02.py` ... Khud likho. Atko to error padho, 10 min try karo, tab pucho.

## 🟢 Level 1 — Warm-up (Output / Basic)

1. `Hello, DevOps World!` print karo.
2. Apna naam, college, aur goal 3 alag lines me print karo.
3. Teen variables (`name`, `age`, `city`) banao aur f-string se ek sentence print karo.
4. Ek variable `x = 10` banao. `type(x)` print karo. Phir `x = "ten"` karke dobara type print karo.
5. `a = 15`, `b = 4` lekar saare 7 arithmetic operators ke result print karo.
6. `print()` ke `sep` use karke `2026-10-23` format me date print karo (`2026`, `10`, `23` alag items).
7. `print()` ke `end` use karke `Loading...Done` ek hi line me print karo (do print calls se).
8. Ek multi-line banner (triple quotes) print karo jisme tumhara naam ho.
9. Escape characters use karke ye print karo:
   ```
   Name    Port
   nginx   80
   ssh     22
   ```
10. Raw string use karke `C:\new\test` print karo.
11. `input()` se naam lo aur `Namaste, <naam>!` print karo.
12. `input()` se do numbers lo aur unka sum print karo (**dhyan:** type convert).
13. `a, b = 5, 10` ko **bina third variable** ke swap karo aur print karo.
14. `x = y = z = 100` karke teeno ka `id()` print karo. Kya same hai?
15. `keyword.kwlist` print karo aur total kitne keywords hain `len()` se nikalo.

## 🟡 Level 2 — Concepts Pakki Karo

16. Celsius → Fahrenheit converter (`F = C × 9/5 + 32`), user se input lo.
17. Fahrenheit → Celsius converter.
18. Do numbers lo aur `+ - * / // % **` sab ka result ek table jaisa print karo.
19. User se radius lo, circle ka area aur circumference nikalo (`pi = 3.14159`, 2 decimal tak).
20. User se length aur breadth lo, rectangle ka area aur perimeter print karo.
21. Seconds input lo aur `H:M:S` format me convert karo (e.g., `3725` → `1h 2m 5s`).
22. Bytes input lo aur MB, GB me convert karo (`1 MB = 1024*1024 bytes`), 3 decimals tak.
23. User se 3 subjects ke marks lo, total aur percentage print karo (2 decimals).
24. Simple interest nikalo: `SI = P*R*T/100`.
25. User se 2-digit number lo aur uske digits ka sum nikalo (`//` aur `%` se).
26. User se 3-digit number lo aur reverse print karo (string slicing **aur** maths dono se).
27. Check karo number even hai ya odd (sirf `%` aur comparison, `if` ke bina `True/False` print karo).
28. `5 + 3 * 2 ** 2 - 8 / 4` ka result **pehle haath se** nikalo, phir Python se verify karo.
29. Ek variable me `"  Nginx Web Server  "` rakho. `strip`, `upper`, `lower`, `title`, `replace("Web","App")` sab try karo.
30. String `"devops"` ke liye: pehla char, aakhri char, pehle 3 chars, reverse, har doosra char — slicing se print karo.

## 🟠 Level 3 — DevOps Flavour

31. **Server card:** hostname, ip, port, cpu, mem, status variables lekar f-string se sundar card print karo (borders `=` se).
32. **Disk usage:** `total_gb` aur `used_gb` input lo, usage % nikalo. `> 80` ho to `True/False` print karo (`alert = percent > 80`).
33. **Uptime converter:** `uptime_seconds` input lo → `Xd Yh Zm Ws` format.
34. **Memory:** `total_ram_mb = 16384`, `used_ram_mb = 11500` → free MB, used %, free GB (2 decimals).
35. **Version string:** `major`, `minor`, `patch` input lo, `v1.4.2` format banao. Fir patch +1 karke naya version print karo.
36. **Port classifier:** port input lo. Variables banao: `is_ssh` (22), `is_web` (80 ya 443), `is_db` (3306 ya 5432). Teeno print karo (`in` operator).
37. **Log line:** `level="ERROR"`, `service="nginx"`, `msg="upstream timed out"` se f-string me log line banao:  
    `[ERROR] nginx: upstream timed out`
38. **Docker image name:** `registry`, `repo`, `tag` se `registry/repo:tag` string banao (f-string).
39. **S3 path builder:** `bucket="my-backups"`, `env="prod"`, `date="2026-10-23"` → `s3://my-backups/prod/2026-10-23/backup.tar.gz`.
40. **Cost estimator:** EC2 hourly price `0.0116` USD, hours/day `24`, days `30`, USD→INR `83` → monthly cost (USD aur INR dono, 2 decimals).
41. **Percentage bar:** `percent = 65` ke liye `[#############       ] 65%` jaisa bar print karo (hint: string `*` int, `20` characters total).
42. **Health summary:** `cpu=72`, `mem=64`, `disk=88`. Teeno ke liye alag bool `cpu_ok`, `mem_ok`, `disk_ok` (threshold: 80). Ek variable `all_ok` jo teeno `and` se check kare.
43. **Environment variable style name:** `"database url"` ko `DATABASE_URL` me convert karo (`upper`, `replace`).
44. **IP octet split:** `ip = "192.168.10.25"` ko `.split(".")` se todo, last octet print karo (string hi rakhna, int me convert karke `+1` bhi karo).
45. **File name parts:** `path = "/var/log/nginx/access.log"` — `split("/")` se last item (file name) nikalo, `.log` extension alag nikalo.

## 🔴 Level 4 — Think Karo (Output Prediction)

Bina run kiye output batao, phir run karke check karo.

46. `print(10 / 2)`
47. `print(10 // 3, 10 % 3, -10 // 3)`
48. `print(2 ** 3 ** 2)`
49. `print(0.1 + 0.2 == 0.3)`
50. `print(bool("False"), bool(""), bool(0.0), bool(" "))`
51. `print("5" + "5", "5" * 3)`
52. `print(int(7.9), int(-7.9), round(7.5), round(8.5))`
53. `print(not 0 or 1 and 0)`
54. `a = None; print(a == None, a is None, bool(a))`
55. `print("devops"[1:4], "devops"[::2], "devops"[-3:])`
56. `x = 5; x += 2; x *= 3; x //= 4; print(x)`
57. `print(f"{3.14159:.2f} | {1000000:,} | {'hi':^6}|")`
58. `print(type(5/1), type(5//1), type(True + 1))`

## 🐞 Level 5 — Debug Karo (Galti dhundho)

Har code me bug hai. Fix karke `.py` me save karo.

59.
```python
name = input("Naam: ")
age = input("Umra: ")
print("Agle saal umra", age + 1)
```
60.
```python
1server = "web"
print(1server)
```
61.
```python
if True:
print("hello")
```
62.
```python
port = 8080
print("Port is " + port)
```
63.
```python
cpu = 80
if cpu = 80:
    print("high")
```
64.
```python
print(Hello World)
```
65.
```python
word = "devops"
word[0] = "D"
print(word)
```
66.
```python
total = 100
used = 25
print("Used percent:", used / totl * 100)
```

## 🏆 Level 6 — Challenge / Mini Tasks

**C1. Server Report Generator**
User se `hostname`, `cpu`, `mem`, `disk` lo. Ek formatted report print karo:
- Har metric ka status: `OK` (<70), `WARN` (70–85), `CRITICAL` (>85) — abhi `if` nahi aaya, to ternary / bool maths se banao: `"CRITICAL" if x > 85 else ("WARN" if x >= 70 else "OK")`.
- Last me overall: agar koi bhi CRITICAL to `ACTION NEEDED`.

**C2. Time Converter Tool**
User se `days`, `hours`, `minutes` lo → total seconds. Phir ulta: total seconds lo → `Xd Yh Zm Ws`.

**C3. Mini Billing Calculator**
Items ka price aur quantity input lo (3 items). Subtotal, GST 18%, discount 10% (subtotal par), final amount, sab 2 decimals me formatted receipt print karo (f-string alignment use karo).

**C4. Tumhara apna: "Python Ne Kya Sikhaya"**
Aaj ke 10 concepts ki list ek `.py` file me **comments** me likho (apne words me), aur har concept ka ek chhota code example likho.

---

## 📋 16️⃣ Cheat Sheet (Revise karne ke liye)

```python
# Variables
name = "x"; port = 80; cpu = 7.5; ok = True; nothing = None

# Types
type(x)  isinstance(x, int)

# Casting
int()  float()  str()  bool()

# I/O
print(a, b, sep="-", end="")
x = input("prompt: ")        # hamesha str

# Operators
+  -  *  /  //  %  **
==  !=  >  <  >=  <=
and  or  not
in  not in  is  is not
+=  -=  *=  /=

# Strings
s.strip() s.upper() s.lower() s.replace(a,b) s.split(",") ",".join(list)
s[0]  s[-1]  s[1:4]  s[::-1]
f"{var}"  f"{var:.2f}"  f"{var:,}"  f"{var:>10}"
```

---

## ✅ Aaj ka Checklist

- [ ] `python3 --version` aur `pip3 --version` check kiya
- [ ] venv banaya aur activate kiya
- [ ] Git config + repo setup + pehla push
- [ ] `.gitignore` banaya
- [ ] Variables, types, casting samjha
- [ ] `print()` ke `sep`, `end` + f-strings try kiye
- [ ] Sab operators run karke dekhe
- [ ] Kam se kam **Level 1 + Level 2 (30 questions)** solve kiye
- [ ] Level 3 se kam se kam **8** DevOps questions kiye
- [ ] Debug questions (59–66) fix kiye
- [ ] Git commit + push kiya

### Minimum target (agar time kam ho)
Q1–Q15, Q16–Q25, Q31–Q38, Q59–Q66.

---

## 🚀 Git Push (Aaj ke end me)

```bash
cd ~/30-day-of-python
git status
git add .
git commit -m "day-01: setup, variables, data types, operators, f-strings"
git push
```
**Line-by-line:**
- `git status` → kya badla hai dekho (push se pehle hamesha check).
- `git add .` → sab changes staging me.
- `git commit -m` → snapshot with message.
- `git push` → GitHub par upload.

---

## 📝 Meri Notes (Khud bharo)

- Aaj kya naya seekha:
- Kahan atka:
- Kal ke liye doubts:

---

## 🔜 Kal (Day 02) ka Preview

**Control Flow + Functions basics:** `if/elif/else`, `for`, `while`, `break/continue`, `range`, `enumerate`, functions, `return`, default arguments — aur DevOps examples (service status checker, retry loop, threshold alerts).
