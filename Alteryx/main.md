# Alteryx Designer – Complete Study Notes

> **Goal:** Alteryx Designer Core Certification via the DataCamp Alteryx Fundamentals Track **Exam:** Free · Online · Open-book · 80 questions · 2.5 hours · Pass/Fail · Retake after 7 days · Expires in 2 years

---

## Table of Contents

- [[#Track Overview]]
- [[#1 – Introduction to Alteryx Designer]]
- [[#2 – Data Preparation in Alteryx]]
- [[#3 – Data Transformation in Alteryx]]
- [[#4 – Data Manipulation in Alteryx]]
- [[#5 – Case Study – Analyzing Sales Data]]
- [[#Core Exam Blueprint]]
- [[#Tool Reference by Category]]
- [[#Formulas & Expressions Cheat Sheet]]
- [[#Data Types Reference]]
- [[#Exam Tips & Strategy]]

---

## Track Overview

The **Alteryx Fundamentals** track on DataCamp was built _in partnership with Alteryx_ and maps directly to the official certification exam content. It consists of five modules:

|#|Course|Duration|Key Focus|
|---|---|---|---|
|1|Introduction to Alteryx Designer|2 h|UI, workflows, basic tools|
|2|Data Preparation in Alteryx|3 h|Cleaning, filtering, formulas, sampling|
|3|Data Transformation in Alteryx|2 h|Formula tool, logic, Crosstab, Transpose|
|4|Data Manipulation in Alteryx|3 h|Unions, joins, parsing, performance|
|5|Case Study: Analyzing Sales Data|2 h|End-to-end retail analytics project|

The certification itself has **four micro-credentials**: General Knowledge, Data Preparation, Data Manipulation, and Data Transformation.

---

## 1 – Introduction to Alteryx Designer

### 1.1 What Is Alteryx Designer?

Alteryx Designer Desktop is a **low-code / no-code** data analytics and automation platform. It uses a **drag-and-drop** interface to build visual **workflows** — sequences of connected tools that process data, similar to a recipe.

Key strengths:

- Automates repetitive data tasks (ETL without code)
- Processes large datasets quickly
- Used across industries: healthcare, retail, finance, consulting
- Common roles: Data Analysts, BI Consultants, Business Users
- Complements visualization tools like Tableau and Power BI

### 1.2 The Alteryx Designer Interface

|Component|Description|
|---|---|
|**Tool Palette**|Contains all available tools organized by category; each category has a specific color and shape|
|**Workflow Canvas**|The main workspace where tools are connected to build workflows|
|**Configuration Window**|Shows settings for the selected tool or connection|
|**Results Window**|Displays data at each tool step after running the workflow (limited to 1 MB per anchor for most tools)|
|**Output Window**|Shows workflow run status, logs, and links to output files|

### 1.3 Workflow Basics

- A **workflow** is a series of connected tools that process data — saved as a `.yxmd` file
- Workflow analogy: **Recipe** → Collect ingredients (input) → Mix & alter (prepare) → Bake & serve (output)
- Tools are connected via **anchors** (input/output connectors on each tool)
- Run a workflow by clicking the **Run** button or pressing `Ctrl + R`
- An **asterisk (*)** next to the name means unsaved changes

**Three types of Alteryx assets:**

1. **Workflow** (`.yxmd`) — a series of connected tools performing data tasks
2. **Analytic App** (`.yxwz`) — a workflow with a UI for end-user input before running
3. **Macro** (`.yxmc`) — a reusable mini-workflow embedded inside other workflows

### 1.4 Tool Palette Categories (Color-Coded)

|Category|Color|Purpose|
|---|---|---|
|**In/Out**|Grey|Input and output data|
|**Preparation**|Blue|Clean, filter, sort, select data|
|**Join**|Orange/Yellow|Combine multiple data streams|
|**Parse**|Teal/Green|Split and restructure text fields|
|**Transform**|Red|Reshape, summarize, pivot data|
|**Reporting**|Teal|Build reports and presentation outputs|
|**Documentation**|Tan/Brown|Annotate and organize workflows|
|**Spatial**|Blue|Geospatial analysis tools|
|**Interface**|Purple|Build apps and macros|

> [!tip] Every tool has a **One Tool Example** — right-click any tool → _Open Example_ to see a sample workflow.

### 1.5 Core In/Out Tools

|Tool|What It Does|
|---|---|
|**Input Data**|Brings data into the workflow from files (CSV, XLSX, JSON, XML, TXT, etc.) or databases|
|**Output Data**|Writes workflow results to files or databases; configure overwrite/append, file format, naming|
|**Text Input**|Manually create data directly inside the workflow (small reference tables, constants)|
|**Browse**|Displays the full data profile: data type, record count, data quality stats (up to 300 MB)|

### 1.6 Basic Preparation Tools (Intro Level)

|Tool|What It Does|
|---|---|
|**Select**|Include/exclude columns, reorder them, rename, change data type/size|
|**Sort**|Arrange records in ascending or descending order by one or more fields|
|**Sample**|Extract a subset: first N records, last N, N%, random sample, or first N per group|
|**Unique**|Separates unique records from duplicates based on specified fields; outputs two streams: `U` (unique) and `D` (duplicates)|
|**Summarize**|Aggregates data: Sum, Count, Avg, Min, Max, Concatenate, Group By, and more|
|**Comment**|Adds annotation text boxes to the canvas for documentation|

---

## 2 – Data Preparation in Alteryx

### 2.1 Why Data Preparation Matters

Data preparation (cleaning, transforming, organizing) typically consumes **60–80%** of an analyst's time. Clean data leads to accurate analytics and better decisions.

### 2.2 Recognizing Dirty Data

Common issues to watch for:

- **Missing values** — nulls, blanks, `N/A`
- **Duplicate records** — repeated rows
- **Incorrect data types** — numbers stored as strings, dates as text
- **Inconsistent formatting** — mixed case, trailing spaces, different date formats
- **Unnecessary columns** — irrelevant fields adding noise
- **Outliers / invalid entries** — typos, impossible values

### 2.3 Data Types in Alteryx

|Type|Description|Examples|
|---|---|---|
|**Bool**|True / False|`True`, `False`|
|**Byte**|Small integer (0–255)|`1`, `255`|
|**Int16**|16-bit integer|`-32,768` to `32,767`|
|**Int32**|32-bit integer|Up to ~2.1 billion|
|**Int64**|64-bit integer|Very large integers|
|**Fixed Decimal**|Exact decimal (specify precision)|`1234.56`|
|**Float**|Single-precision decimal|`3.14`|
|**Double**|Double-precision decimal (most common numeric)|`3.14159265`|
|**String**|Text of variable length|`"Hello World"`|
|**WString**|Wide string (Unicode)|International characters|
|**V_String**|Variable-length string|Adjusts dynamically|
|**V_WString**|Variable-length wide string|Unicode + dynamic|
|**Date**|Date only|`2025-01-15`|
|**Time**|Time only|`14:30:00`|
|**DateTime**|Date and time combined|`2025-01-15 14:30:00`|
|**Spatial Object**|Geographic data|Points, polygons, lines|

> [!important] Choosing the **correct data type** is critical: it affects storage, processing speed, and which operations/formulas you can use. The Select tool is the main place to change data types.

### 2.4 The Data Cleansing Tool

The **Data Cleansing** tool (Preparation category) fixes common issues in one step:

- Replace nulls with blanks (strings) or zeros (numerics)
- Remove leading/trailing whitespace
- Remove tabs, line breaks, duplicate whitespace
- Modify case (Upper, Lower, Title Case)
- Remove all whitespace
- Remove letters / numbers / punctuation

### 2.5 The Filter Tool

Filters create **two output streams**: records that match (`True`) and records that don't (`False`).

**Three filter modes:**

1. **Basic Filter** — simple field = value condition
2. **Custom Filter** — write your own expression using Alteryx formula syntax
3. **Chained Filters** — connect multiple Filter tools in sequence for layered conditions

**Key expression operators:**

- `=`, `!=`, `>`, `<`, `>=`, `<=`
- `AND`, `OR` — combine conditions
- `IN (...)` — check membership
- `LIKE` — pattern matching

> [!note] `AND` requires **all** conditions to be true; `OR` requires **at least one** to be true.

### 2.6 The Select Records Tool

- Retrieves records by **row number** or **range**
- Syntax examples: `1`, `3-7`, `10+` (row 10 onward), `-5` (last 5)
- Useful for quickly grabbing specific subsets

### 2.7 Writing Expressions & Formulas (Preparation Level)

**Syntax rules:**

- Field names are enclosed in square brackets: `[FieldName]`
- String literals use double quotes: `"text"`
- Functions are case-sensitive
- Expressions return a value for each record

**Common string formulas:**

|Function|Description|Example|
|---|---|---|
|`Left(String, n)`|First n characters|`Left([Name], 3)`|
|`Right(String, n)`|Last n characters|`Right([Code], 2)`|
|`Substring(String, start, length)`|Extract portion|`Substring([Phone], 1, 3)`|
|`Length(String)`|Character count|`Length([Name])`|
|`FindString(String, target)`|Position of target (0-based)|`FindString([Email], "@")`|
|`Contains(String, target)`|True/False if contains|`Contains([City], "New")`|
|`Trim(String)`|Remove leading/trailing spaces|`Trim([Name])`|
|`TrimLeft / TrimRight`|One-sided trim||
|`Uppercase(String)`|Convert to uppercase|`Uppercase([Name])`|
|`Lowercase(String)`|Convert to lowercase||
|`TitleCase(String)`|Title case||
|`Replace(String, find, replace)`|Find and replace text|`Replace([Phone], "-", "")`|
|`PadLeft(String, len, char)`|Pad from left|`PadLeft([ID], 5, "0")`|
|`PadRight(String, len, char)`|Pad from right||

**Length-based vs Position-based:**

- **Length-based**: `Left()`, `Right()` — you specify _how many_ characters
- **Position-based**: `Substring()`, `FindString()` — you specify _where_ to start

### 2.8 Sampling Data

The **Sample** tool modes:

- **First N records** / **Last N records**
- **Skip first N records**
- **First N% of records**
- **1 in every N records**
- **Random N records** (with optional seed)
- **First N per group** (by a specified column)

### 2.9 The Summarize Tool (Detail)

**Actions available:**

|Category|Actions|
|---|---|
|**Group By**|Groups records by one or more fields (like SQL `GROUP BY`)|
|**Numeric**|Sum, Count, Count Non-Null, Count Null, Count Distinct, Min, Max, Average, Median, Mode, Standard Deviation, Variance, Percentile|
|**String**|First, Last, Concatenate (with separator), Longest, Shortest, Mode|
|**Spatial**|Combine, Create Convex Hull, Create Bounding Rectangle|

> [!tip] Group By fields go first, then aggregation actions. You can apply multiple actions to the same field.

---

## 3 – Data Transformation in Alteryx

### 3.1 The Formula Tool (Advanced)

The **Formula Tool** (Transform category, red) is one of the most powerful tools in Alteryx. It lets you:

- **Create new columns** — select `+ Add Column` and name it
- **Update existing columns** — select the column from the dropdown
- **Chain multiple expressions** — add multiple formulas in one tool
- Use the full **Alteryx function library** (accessible via the function panel)

### 3.2 Mathematical Functions

|Function|Description|
|---|---|
|`ABS(x)`|Absolute value|
|`CEIL(x)`|Round up to nearest integer|
|`FLOOR(x)`|Round down to nearest integer|
|`ROUND(x, d)`|Round to `d` decimal places|
|`MOD(x, y)`|Remainder of x ÷ y|
|`POW(x, y)`|x raised to power y|
|`SQRT(x)`|Square root|
|`LOG(x)`|Natural logarithm|
|`LOG10(x)`|Base-10 logarithm|
|`RAND()`|Random number between 0 and 1|
|`MIN(a, b)`|Smaller of two values|
|`MAX(a, b)`|Larger of two values|

### 3.3 Conditional Statements

**IF / ELSEIF / ELSE / ENDIF:**

```
IF [Score] >= 90 THEN "A"
ELSEIF [Score] >= 80 THEN "B"
ELSEIF [Score] >= 70 THEN "C"
ELSE "F"
ENDIF
```

**IIF (Inline IF):**

```
IIF([Status] = "Active", 1, 0)
```

- Syntax: `IIF(condition, true_value, false_value)`
- Simpler than `IF` for binary conditions

**Switch:**

```
Switch([Region],
  "Default",
  "N", "North",
  "S", "South",
  "E", "East",
  "W", "West"
)
```

### 3.4 Null Handling

|Function|Description|
|---|---|
|`IsNull([Field])`|Returns True if null|
|`IsEmpty([Field])`|Returns True if empty string|
|`IF IsNull([Field]) THEN "N/A" ELSE [Field] ENDIF`|Replace null|
|`IIF(IsNull([Field]), 0, [Field])`|Replace null with 0|

### 3.5 Type Conversion Functions

|Function|Description|
|---|---|
|`ToNumber(String)`|Convert string to number|
|`ToString(Number, decimals)`|Convert number to string|
|`ToNumber(ToString([Field]))`|Chain conversions|
|`DateTimeParse(String, format)`|Parse string to DateTime|
|`DateTimeFormat(DateTime, format)`|Format DateTime to string|

### 3.6 The Transpose Tool

**Purpose:** Pivots data from **wide to long** (columns become rows).

**Configuration:**

1. **Key Columns** — columns that stay fixed (identifiers)
2. **Data Columns** — columns to be unpivoted into rows

**Example:**

_Before (wide):_

|Student|Math|English|Science|
|---|---|---|---|
|Alice|90|85|92|

_After Transpose (long):_

|Student|Name|Value|
|---|---|---|
|Alice|Math|90|
|Alice|English|85|
|Alice|Science|92|

- **Name** column contains the old column headers
- **Value** column contains the data values
- Data becomes **thinner and longer**
- You **cannot aggregate** during Transpose

### 3.7 The Cross Tab Tool

**Purpose:** Pivots data from **long to wide** (rows become columns) — the **inverse** of Transpose.

**Configuration:**

1. **Group Data by These Values** — row identifiers (like Group By)
2. **Column Headers** — the field whose values become new column names
3. **Values for New Columns** — the field with data to fill the new columns
4. **Aggregation Method** — Sum, Count, Avg, Min, Max, Concatenate, etc.

**Example:**

_Before (long):_

|Student|Subject|Score|
|---|---|---|
|Alice|Math|90|
|Alice|English|85|

_After Cross Tab (wide):_

|Student|Math|English|
|---|---|---|
|Alice|90|85|

- Data becomes **shorter and wider**
- You **can aggregate** during Cross Tab

> [!important] **Transpose + Cross Tab in tandem:** Use Transpose to reshape data long, manipulate it, then Cross Tab to reshape back wide. This is a common pattern tested on the exam.

### 3.8 The Count Records Tool

- Returns a single record with the total number of input records
- Simple but useful for validation and documentation

---

## 4 – Data Manipulation in Alteryx

### 4.1 The Union Tool

**Purpose:** Combines **two or more** data streams **vertically** (stacking rows on top of each other).

**Configuration options:**

- **Auto Config by Name** — matches columns with the same name (most common)
- **Auto Config by Position** — matches columns by order (left to right)
- **Manually Configure** — map columns yourself

**Key considerations:**

- Columns that don't match produce nulls or get dropped depending on config
- Data types should be compatible
- If field names differ but represent the same thing, use manual configuration

### 4.2 The Append Fields Tool

**Purpose:** Performs a **Cartesian join** (cross join) — joins every row from one input to every row of another.

- If source has 100 rows and target has 10 rows → result has **1,000 rows**
- Use cautiously — can create very large datasets
- Common use case: appending a single summary row (e.g., total) to every detail row

### 4.3 The Join Tool (Detail)

**Purpose:** Combines **two** data streams **horizontally** based on matching fields (like SQL JOIN).

**Three output anchors:**

1. **J (Join)** — records that match in **both** inputs (Inner Join)
2. **L (Left)** — records from the **left** input with **no match** in the right
3. **R (Right)** — records from the **right** input with **no match** in the left

**Join types you can achieve:**

|Type|How|
|---|---|
|**Inner Join**|Use the `J` output only|
|**Left Outer Join**|Use `J` + `L` outputs (Union them)|
|**Right Outer Join**|Use `J` + `R` outputs (Union them)|
|**Full Outer Join**|Use `J` + `L` + `R` outputs (Union all three)|

**Join methods:**

- **By Specific Field** — join on matching column values (most common)
- **By Record Position** — join on row number order

**Troubleshooting joins:**

- **Duplicate rows** — if the join key isn't unique, you get a Cartesian product for those rows
- **Data type mismatch** — strings can only join strings; numerics only join numerics
- **Mismatched field names** — rename fields in the Select tool before joining
- **Null values** — nulls never match other nulls in a join

### 4.4 The Find Replace Tool

**Purpose:** Searches for values in one field and replaces them with values from another dataset (like VLOOKUP in Excel).

- **Find** input (F anchor) — the lookup table with find/replace pairs
- **Original** input — the data to search within
- **Find Field** and **Replace Field** are configured separately
- Can append additional fields from the lookup table
- Supports exact match or contains match

### 4.5 Parsing Data

#### Text to Columns Tool

- Splits a single column into **multiple columns** or **rows** based on a delimiter
- Delimiters: comma, space, tab, pipe `|`, custom character, fixed width
- Choose split to **Columns** (horizontal) or **Rows** (vertical)
- Specify number of columns or let Alteryx auto-detect

#### DateTime Tool

- Converts between **String** and **Date/DateTime** formats
- Two modes:
    1. **String → Date/DateTime** — specify the format of the input string
    2. **Date/DateTime → String** — choose the desired output format
- Standard ISO format: `yyyy-MM-dd HH:mm:ss`

**Common format specifiers:**

|Specifier|Meaning|Example|
|---|---|---|
|`%Y`|4-digit year|`2025`|
|`%y`|2-digit year|`25`|
|`%m`|Month (01–12)|`03`|
|`%d`|Day (01–31)|`15`|
|`%H`|Hour 24h (00–23)|`14`|
|`%I`|Hour 12h (01–12)|`02`|
|`%M`|Minute (00–59)|`30`|
|`%S`|Second (00–59)|`00`|
|`%p`|AM/PM|`PM`|

**DateTimeParse examples:**

```
DateTimeParse([DateStr], "%m/%d/%Y")     → parses "03/15/2025"
DateTimeParse([DateStr], "%d-%b-%Y")     → parses "15-Mar-2025"
```

**DateTimeFormat examples:**

```
DateTimeFormat([Date], "%Y-%m-%d")       → "2025-03-15"
DateTimeFormat([Date], "%B %d, %Y")      → "March 15, 2025"
```

**DateTimeDiff and DateTimeAdd:**

```
DateTimeDiff([EndDate], [StartDate], "days")   → number of days between
DateTimeAdd([Date], 30, "days")                → adds 30 days
```

#### RegEx Tool (Regular Expressions)

- Three modes: **Parse**, **Match**, **Replace**
- Powerful for complex string extraction/manipulation
- Common patterns:
    - `\d` = digit, `\w` = word character, `\s` = whitespace
    - `+` = one or more, `*` = zero or more, `?` = optional
    - `()` = capture group
    - `.` = any character

### 4.6 Performance Optimization

**Common bottlenecks:**

- Large data volumes
- Tool-specific inefficiencies
- Workflow design issues
- Resource (memory/CPU) limitations

**Optimization techniques:**

|Technique|Description|
|---|---|
|**Browse sparingly**|Remove unnecessary Browse tools — they consume memory|
|**Disable tool containers**|Temporarily disable sections you don't need|
|**Select early**|Drop unused columns as early as possible to reduce data volume|
|**Filter early**|Reduce rows before heavy processing|
|**Cache and run**|Cache data at checkpoints so you don't re-process|
|**Performance profiling**|Use the Performance Profiling option to identify slow tools|
|**Sort wisely**|Sorting is expensive; only sort when necessary|
|**Use the right data types**|Smaller types (Int16 vs Int64) use less memory|
|**Limit output**|Only output what's needed|
|**Avoid unnecessary joins**|Each join multiplies potential rows|

---

## 5 – Case Study – Analyzing Sales Data

This final module applies all skills in a **retail analytics scenario** for a fictional department store.

### Skills Reviewed

- Importing data from multiple sources
- Combining data (joins, unions)
- Cleaning and parsing (dates, text)
- Transforming data (Pivot, Cross Tab, Transpose)
- Calculating metrics (formulas, summarize)
- Documenting workflow with Comments and Tool Containers
- Outputting final results

> [!tip] This case study is the best pre-exam practice — it covers every major topic.

---

## Core Exam Blueprint

|Domain|% of Exam|Topics|
|---|---|---|
|**I. General Designer Knowledge & Optimization**|**13%**|Search & resources, UI navigation, native file formats (`.yxmd`, `.yxdb`), sharing/exporting workflows, optimization & documentation|
|**II. Input/Output Data & Preparation**|**36%**|Read/write data, data types, Data Cleansing tool, building formulas (conditionals, references), Filter, Select, Select Records, Sort, Unique, Sample|
|**III. Blend Data & Parse**|**26%**|Unions, Joins, Appends, Find & Replace, string-to-date conversions, Text to Columns, troubleshooting (duplicates, type mismatches, mismatched fields)|
|**IV. Transform Data**|**25%**|Summarize tool, Transpose tool, Cross Tab tool, using Transpose + Cross Tab in tandem|

---

## Tool Reference by Category

### In/Out Tools (on the exam)

|Tool|Icon Color|Purpose|
|---|---|---|
|Input Data|Grey|Read from files / databases|
|Output Data|Grey|Write results to files / databases|
|Text Input|Grey|Manually enter data|
|Browse|Grey|View data and profile|

### Preparation Tools (on the exam)

|Tool|Purpose|
|---|---|
|Data Cleansing|One-step fix: nulls, whitespace, case|
|Filter|Split data into True / False streams by condition|
|Formula|Create/update fields with expressions|
|Multi-Field Formula|Apply same formula across multiple fields|
|Multi-Row Formula|Reference values from other rows|
|Select|Choose columns, rename, retype, reorder|
|Select Records|Pick specific rows by number/range|
|Sort|Order data by one or more fields|
|Sample|Subset data (first N, random, %, etc.)|
|Unique|Separate unique from duplicate records|
|Record ID|Add sequential unique ID column|

### Join Tools (on the exam)

|Tool|Purpose|
|---|---|
|Join|Combine two streams by matching fields (Inner + Left + Right outputs)|
|Union|Stack multiple streams vertically|
|Append Fields|Cartesian (cross) join|
|Find Replace|Lookup and replace values from a reference table|

### Parse Tools (on the exam)

|Tool|Purpose|
|---|---|
|Text to Columns|Split one field into multiple by delimiter|
|DateTime|Convert between string and date/time formats|
|RegEx|Parse, match, or replace using regular expressions|

### Transform Tools (on the exam)

|Tool|Purpose|
|---|---|
|Summarize|Aggregate: Group By + Sum/Count/Avg/etc.|
|Cross Tab|Pivot long → wide (with aggregation)|
|Transpose|Pivot wide → long (no aggregation)|
|Count Records|Count total rows|

### Documentation Tools (on the exam)

|Tool|Purpose|
|---|---|
|Comment|Add text annotations to the canvas|
|Tool Container|Group and organize tools; can be disabled/collapsed|
|Explorer Box|Add a help box for Analytic Apps|

---

## Formulas & Expressions Cheat Sheet

### String Functions

```
Left([Field], n)               → first n characters
Right([Field], n)              → last n characters
Substring([Field], start, len) → extract from position
Length([Field])                 → character count
FindString([Field], "target")  → position (0-based, -1 if not found)
Contains([Field], "text")      → True/False
Replace([Field], "old", "new") → find and replace
Trim([Field])                  → remove leading/trailing spaces
Uppercase([Field])             → ALL CAPS
Lowercase([Field])             → all lower
TitleCase([Field])             → Title Case
PadLeft([Field], len, "0")     → left-pad with zeros
PadRight([Field], len, " ")    → right-pad with spaces
REGEX_Replace([Field], pattern, replacement)
REGEX_Match([Field], pattern)
```

### Numeric Functions

```
ABS(x)            CEIL(x)           FLOOR(x)
ROUND(x, d)       MOD(x, y)         POW(x, y)
SQRT(x)           LOG(x)            LOG10(x)
RAND()            MIN(a, b)         MAX(a, b)
```

### Conditional Logic

```
IF [X] > 10 THEN "High" ELSEIF [X] > 5 THEN "Med" ELSE "Low" ENDIF
IIF([X] > 0, "Positive", "Non-positive")
Switch([Field], "default", "val1", "result1", "val2", "result2")
```

### Null & Empty Checks

```
IsNull([Field])          → True if null
IsEmpty([Field])         → True if empty string ""
IIF(IsNull([Field]), 0, [Field])
```

### Date & Time Functions

```
DateTimeParse([Str], "%m/%d/%Y")       → String to Date
DateTimeFormat([Date], "%Y-%m-%d")     → Date to String
DateTimeDiff([End], [Start], "days")   → Difference
DateTimeAdd([Date], 7, "days")         → Add time
DateTimeDay([Date])                    → Extract day
DateTimeMonth([Date])                  → Extract month
DateTimeYear([Date])                   → Extract year
DateTimeNow()                          → Current DateTime
DateTimeToday()                        → Current Date
DateTimeFirstOfMonth()                 → First of current month
```

### Conversion Functions

```
ToNumber([StringField])
ToString([NumField])
ToString([NumField], 2)      → "123.45" (2 decimals)
BoolToInt([BoolField])
```

---

## Data Types Reference

### Numeric Hierarchy (smallest → largest)

```
Byte → Int16 → Int32 → Int64 → Float → Double → FixedDecimal
```

### String Types

```
String         → Fixed length (truncates if over)
WString        → Fixed length Unicode
V_String       → Variable length (adapts)
V_WString      → Variable length Unicode
```

### When to Use What

|Scenario|Recommended Type|
|---|---|
|Whole numbers (small)|Int16 or Int32|
|Large integers|Int64|
|Currency / precise decimals|FixedDecimal|
|General decimals|Double|
|Text (known max length)|String or V_String|
|Text (international chars)|WString or V_WString|
|Date only|Date|
|Date + Time|DateTime|
|Yes/No flags|Bool|

> [!warning] **Joining rules:** Strings can only join to strings. Numerics can only join to numerics. Use Select or Formula to convert before joining.

---

## Exam Tips & Strategy

### Before the Exam

- [x] Complete all 5 DataCamp courses
- [x] Take the **Alteryx Practice Exam** (15 questions with explanations)
- [x] Review the **official Exam Prep Guide** from Alteryx Community
- [x] Practice with **Weekly Challenges** on the Alteryx Community
- [x] Have resources ready: Help Documentation, Community, One Tool Examples, these notes

### During the Exam (2.5 hours, 80 questions)

- **~75 seconds** per 1-point question
- **~4 minutes** per practical application question (3 points)
- Read every question carefully — **details matter**
- Use the **Bookmark** feature for questions you want to revisit
- **Answer every question** — partial credit is given for matching and multiple-response
- Use `See All Questions` to check for unanswered questions before submitting
- It's **open book** — have Alteryx Designer open alongside the exam

### Practical Application Questions

- You'll need to **download a dataset**, build a workflow in Designer, and find the answer
- Common patterns: filter + join + summarize → what's the result?
- Have a **clean workspace** ready in Designer before starting
- Remember to check **record count** and **field values** in the Results window

### Key Concepts That Are Frequently Tested

1. **Data types** and when to use each
2. **Join outputs** — which records go to J, L, R
3. **Union vs Join** — vertical stacking vs horizontal matching
4. **Filter expressions** — AND vs OR logic
5. **Transpose vs Cross Tab** — which direction (long ↔ wide)
6. **Summarize** — Group By mechanics, aggregation methods
7. **Formula syntax** — especially conditionals (`IF/ELSEIF`, `IIF`)
8. **DateTime conversions** — format specifiers, parse vs format
9. **Text to Columns** — delimiter options, split to rows vs columns
10. **Performance optimization** — what speeds up workflows
11. **Workflow documentation** — Comment tool, Tool Container
12. **Native file formats** — `.yxmd` (workflow), `.yxdb` (database), `.yxwz` (app), `.yxmc` (macro)

---

## Alteryx File Formats

|Extension|Type|
|---|---|
|`.yxmd`|Standard Workflow|
|`.yxmc`|Macro|
|`.yxwz`|Analytic App|
|`.yxdb`|Alteryx Database (native format, fastest I/O)|
|`.yxft`|Field Type File|
|`.bak`|Workflow Backup|

---

## Quick Comparison Table

|Feature|Transpose|Cross Tab|
|---|---|---|
|Direction|Wide → Long|Long → Wide|
|Rows change|More rows|Fewer rows|
|Columns change|Fewer columns|More columns|
|Aggregation|❌ No|✅ Yes|
|Key columns|Stay as-is|Used for Group By|

|Feature|Union|Join|
|---|---|---|
|Direction|Vertical (stack)|Horizontal (merge)|
|Inputs|2+ streams|Exactly 2 streams|
|Match by|Column name/position|Field values|
|Result|All rows combined|Matched + unmatched|

|Feature|Join|Append Fields|
|---|---|---|
|Type|Equi-join (matching)|Cartesian (cross)|
|Row count|≤ sum of inputs|Product of inputs|
|Use case|Matching on key|Broadcast a value|

---

## Additional Resources

- **Alteryx Community:** community.alteryx.com — Weekly Challenges, forums, Tool Mastery blogs
- **Help Documentation:** help.alteryx.com — full tool reference and configuration guides
- **One Tool Examples:** right-click any tool in Designer → Open Example
- **Practice Exam:** available via Alteryx Community Certification Resources
- **DataCamp Track:** datacamp.com/tracks/alteryx-fundamentals

---

> [!success] **You've got this!** The exam is free, open-book, and you can retake it after 7 days. Focus on understanding the tools, practice with real data, and keep these notes handy during the exam. Good luck! 🎯