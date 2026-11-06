# Problem-Solving Coach: Specification

*Status: built and on GitHub. Updated November 5, 2026 to match the tool as built.*

- **Repository:** lufox2021/problem-solving-tool (branch `main`)
- **Live tool:** https://lufox2021.github.io/problem-solving-tool/ (once GitHub Pages is on: Settings → Pages → deploy from `main`, `/ (root)`)
- **First-release snapshot:** branch `Version-11052026`

## 1. Purpose

A student tool that teaches Tad Fox's eight-step method for solving chemistry problems (from the "Solving Chemistry Problems" slides):

1. Tell yourself you can do this. Relax.
2. Read the problem several times, slowly. Find the desired answer and its units. Don't start solving yet.
3. Write in English what the answer should look like, including units.
4. Draw a picture to clarify the problem.
5. Write in English the information you have. Label the picture with it.
6. Write in English the relationships between the key factors.
7. Write in English a plan for solving the problem, step by step.
8. Put in numbers and solve.

The tool builds the method into the screen layout. Steps 1–7 are an ungraded workspace. **Only the final answer is graded.** The design handles general chemistry problems beyond the first unit.

## 2. Delivery and working rules

- **One page.** The tool is a single self-contained web page (`index.html`) on GitHub Pages. Students open a link and install nothing.
- **Working rules.** Design is discussed before building. Changes are developed and tested locally, then pushed to GitHub only when the instructor says so.
- **Unit engine.** The Factor-Label Workbench unit engine is **copied into this page**, not linked, so the tool works on its own. A fix made in one copy has to be repeated in the other.

## 3. Choosing a problem

- **Problem type buttons** sit at the top of the Solve tab: All, Measurement & units, Measurement & density, Percent & composition, Atoms & scale, Moles & molar mass, Solutions, Stoichiometry, Gases, Challenge.
  - Each button shows how many problems it has.
  - The buttons come from the `topic` column. A new topic gets its own button automatically, after the standard ones.
- **The problem list** below the buttons shows only the chosen type.
- **Random problem** opens a random problem of the chosen type, never the one already on screen.
- **Remembered choice:** the tool remembers each student's chosen type and last problem.

## 4. Student flow

**The problem card** at the top shows the setup text and, under it, the **question(s)**: one question, or parts a, b, c. **Pin** keeps the card on screen while the student scrolls.

| Step | Workspace | Graded? |
|---|---|---|
| 1. Relax | "I can do this." button, plus a confidence rating from 1 to 5 | No |
| 2. Read | Highlighter on the setup **and** the questions: **blue** for what's asked, **orange** for what's given. Tap or drag across words; eraser; clear. | No |
| 3. Desired answer | Free-text box | No |
| 4. Picture | Drawing pad (section 6) | No |
| 5. What I know | Free-text list, one fact per line. Each line becomes a label chip that can be dragged onto the drawing. | No |
| 6. Relationships | Free-text box | No |
| 7. Plan | Free-text box | No |
| 8. Solve | Calculation lines (section 5), then the final answer(s) | **Final answer only** |

### Unlocking Step 8

Step 8 stays locked, with a "Don't start solving yet!" message listing what's missing, until Steps 2–7 are done:
- **Step 2:** at least one blue and one orange highlight
- **Step 4:** at least one mark on the drawing pad
- **Steps 3, 5, 6 and 7:** at least 3 words each

Step 1 is optional.

## 5. Step 8: calculation lines

Step 8 is a series of lines of two kinds:

- **Factor-label line** (the Workbench approach)
  - The student enters a starting quantity, adds conversion factors with units on top and bottom (each factor can be squared or cubed), and sets goal units.
  - **Check units** tests whether the units cancel to the goal.
  - If they don't, it says which units are left on top or bottom. If they do, the number boxes unlock.
- **Formula line**
  - Arithmetic with units carried along, for steps a conversion chain can't do: subtraction, sums, rearranged formulas.
  - Supports `+ − × ÷ ^`, parentheses, `pi`, and the functions `sqrt( )`, `cbrt( )`, `ln( )`, `log( )`, `exp( )`.
  - Roots work on quantities with units, e.g. `cbrt(8.0 cm^3)` = 2 cm.
  - A **Show result in** box converts the result to other units.
  - Units that cancel physically (m³/L, mol/mol) simplify to a plain number.

**Using results:** each line's result can be named and used in later lines by typing the name in braces, e.g. `{liquid mass} / 91.1 mL`. **Use my last result** copies the last line's result into the answer box.

Significant figures are not enforced or graded anywhere.

## 6. Drawing pad (Step 4)

- **Tools:** Pen, Line, Arrow, Box, Oval, Text, Fill, Move, Erase. Plus Thin/Thick, Undo and Clear.
- **Colors:** dark ink, blue, orange, red, green, and three greys (light, medium, dark).
- **Fill tool**
  - The student clicks the line(s) around an area (selected lines glow blue), then clicks a color or a pattern.
  - Every area those lines close off is filled. Gaps of a few pixels between line ends are bridged.
  - Patterns: solid (partly see-through), diagonal lines, crosshatch, dots, horizontal lines, vertical lines, bricks.
  - With lines selected, clicking a color fills right away using the current pattern. For a patterned fill, students pick the pattern first.
  - Fills sit under the lines and labels. They can be moved, erased and undone.
- **Labels from Step 5:** drag a chip onto the drawing, or tap it to place it.
- **Input:** works with a mouse, a finger or a stylus.
- **Background image:** an optional image per problem (`background_image` column). It works only once the tool is on GitHub, with the image file in the repository.

## 7. Grading the final answer

- **What's graded:** each numeric part is graded on its own. Ungraded parts take a written response that is saved and shown in the PDF.
- **Units**
  - Answers that need units must have them. Missing or wrong units count as a failed attempt.
  - Equivalent units are converted before comparing, e.g. g/cm³ for g/mL, kPa for Pa, ug or mg for µg.
  - Unitless answers (counts, fractions, ratios) must be plain numbers. A trailing % is accepted and converted (99.996% → 0.99996).
- **Tolerance**
  - The default is within 5% of the key.
  - A part can set a different percentage, or an absolute tolerance (`abs:x`) for answers near 1 or 0 and for counts. For example, `abs:0.5` makes 26 correct and 25 wrong.
- **Alternate answers:** a part can list other accepted answers.
- **Number formats:** `0.0000370`, `3.70e-5`, `3.70 x 10^-5`, `3.70×10⁻⁵`.

**Attempts:**
- Unlimited.
- After **2** failed attempts, the hint is offered.
- After **5** failed attempts, **or** a correct answer, the instructor's solution is offered.
- Ungraded parts offer the instructor's answer once the student has written at least 3 words.

## 8. Saving and exporting

- **Saving:** each student's work is saved in their own browser: highlights, text, drawing, calculation lines, attempts. It persists across visits on that device. **Start over** clears it after a second click to confirm.
- **Export PDF** (optional button):
  - Contains the problem and questions, all step entries, the drawing, the calculation lines, final answers, results and attempts.
  - Has a name line at the top, for uploading to Blackboard.

## 9. Problem data

### Where the problems come from

1. **On GitHub,** the tool reads `problems.json` from the repository. Replacing that file updates every student's problems.
2. **Built-in copy:** the full problem set is also built into `index.html`. It's used when `problems.json` can't be loaded, such as in the claude.ai prototype.
3. **Uploads:** problems uploaded in the Instructor tab are saved in that browser only, and they override problems with the same ID. **Remove uploaded problems** clears them.

The spreadsheet is never read by the tool directly. It's the source the instructor edits.

### Instructor tab

- **Download template**, as .xlsx (with a Column guide sheet) or .csv.
- **Upload a spreadsheet** (.xlsx, .csv or tab-delimited .txt). Every row is checked, and errors are listed by row number:
  - missing required fields
  - units the engine doesn't recognize
  - a bad tolerance
  - duplicate parts
  - alternate answers missing units
- **Convert to JSON**, then **Download problems.json**, **Copy JSON**, or **Try these problems in the Solve tab**.
- **Load a problems.json** to test it. **Remove uploaded problems.**

### Updating the problems students see

1. Edit `spreadsheets/problems-master.xlsx`.
2. In the Instructor tab: upload it, fix any flagged rows, click **Convert to JSON**, then **Download problems.json**.
3. On GitHub: **Add file → Upload files**, upload `problems.json` to replace the old one, and commit.

### Spreadsheet columns (one row per answer part)

| Column | Required | Meaning |
|---|---|---|
| `problem_id` | Yes | Groups the parts of one problem, e.g. `DENS-001` |
| `topic` | First row | Problem type. Becomes a filter button. |
| `chapter` | No | Course chapter or unit |
| `problem_text` | First row | The setup. `^` for powers (`m^3`, `10^22`), `_` for subscripts (`H_2O`). Put the question in `part_prompt`, not here. |
| `part` | Yes | a, b, c… |
| `part_prompt` | Yes | The question for this part. Shown in the problem card under the setup. |
| `answer_type` | Yes | `numeric` or `ungraded` |
| `answer_value` | Numeric parts | The key value |
| `answer_units` | If it has units | e.g. `g/mL`, `kg/m^3`, `M`, `J/(mol K)`. Blank for unitless. |
| `tolerance` | No | Blank = 5%. Or `2%`, or `abs:0.00001`. |
| `alt_answers` | No | Other accepted answers, separated by semicolons |
| `hint` | Numeric parts | Offered after 2 failed attempts |
| `model_solution` | Numeric parts | Offered after 5 failed attempts or a correct answer. Alt+Enter starts a new line in a cell. |
| `background_image` | No | Image file for the drawing pad |

### Writing conventions

- **The question goes in `part_prompt`,** never only in `problem_text`. Otherwise the card shows a setup with no question.
- **State constants and data in the text:** atomic masses, Avogadro's number, R, non-metric conversions (lb, gal, in., mi), and T in K = T in °C + 273.15. Students are expected to know standard metric prefixes (pm, nm, mL ↔ cm³ and so on).
- **For unitless answers,** add "(Enter just the number.)" to the prompt. For percent answers, list the % form in `alt_answers`.
- **Avoid copyrighted text.** Problems from commercial textbooks are not copied. Use openly licensed sources with credit, or write original problems.

## 10. Current problem set (51 problems)

| Group | IDs | Problems | Source |
|---|---|---|---|
| Slide problems | DENS-001, ROD-001, NEON-001 | 3 | "Solving Chemistry Problems" slides (corrected) |
| Adapted from OpenStax | MEAS-001–004, MOLE-, SOLN-, STOI-, GAS- | 19 | OpenStax *Chemistry 2e* (CC BY-NC-SA 4.0), reworded and recalculated; each solution ends with a credit line |
| Original Chapter 1 | MEAS-101–110, PCT-101–103 | 13 | Written for this tool, on Chapter 1 problem types |
| Original cumulative & challenge | CUM-101–109, CHAL-101–107 | 16 | Written for this tool, on the skills in Chapter 1 cumulative and challenge problems |

All answer keys were checked by solving each problem a second time in the tool's own calculator.

## 11. Unit engine

- **Based on** the Factor-Label Workbench engine, with these additions:
  - temperature (**K**)
  - molarity (**M**, **mM**)
  - "J/(g K)" and "J/(mol K)" read as kelvin, not potassium
  - roots of quantities with units
- **Supported:**
  - metric prefixes on base units
  - lb, oz, gal, qt, in., ft, yd, mi
  - atm, torr, mmHg, Pa, bar
  - J, cal, Cal
  - counts (atoms, molecules, mol)
  - substance-tagged units (g NaCl)
- **Not yet supported:**
  - °C or °F inside calculations. Students convert to K first, so thermochemistry problems written in J/(g·°C) can't be graded yet.
  - A built-in periodic table or constants library. Problems state the values they need instead.

## 12. Not included (by decision)

- No grading of Steps 1–7
- No significant-figure enforcement or grading
- No "check your answer" step (Step 9)

## 13. Possible next steps

- °C support in calculations, which would open up thermochemistry problems
- A built-in periodic table and constants panel
- Problem sets for later chapters (bonding, thermochemistry, equilibrium, acids and bases)

## Appendix: corrections to the slides

- **Slide 27:** "192.7 g − 88.32 g = 104.38 g" should be 192.79 g − 88.32 g = 104.47 g. The final 1.15 g/mL is unchanged.
- **Slide 29:**
  - The mass per rod is 24.5 kg, not 25.4 kg.
  - The density in the header reads "7.930 kg/m³" and should be 7930 kg/m³.
  - "Step 7" appears twice; the blue "Number of cylinders × mass per cylinder" should be Step 6.
- **Typos:** slide 26, "I known" should be "I know"; slide 30, "faction" should be "fraction."
