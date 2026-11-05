# Problem-Solving Coach

An interactive tool that teaches general chemistry students an eight-step method for solving word problems:

1. Tell yourself that you can do this. Relax.
2. Read through the problem several times, slowly.
3. Write in English what the answer should look like, including units.
4. Draw a picture to clarify the problem.
5. Write down in English the information that you have. Label the picture with it.
6. Write down in English the relationships between the key factors.
7. Write down in English a plan for solving the problem.
8. Put in numbers and solve.

**Live tool:** https://lufox2021.github.io/problem-solving-tool/

Students open the link in a browser. Nothing to install.

## What students do

- **Choosing a problem:** students pick a problem type from the buttons at the top (Measurement & units, Measurement & density, Percent & composition, Atoms & scale, Moles & molar mass, Solutions, Stoichiometry, Gases, Challenge), or click **All**. **Random problem** opens a random problem of the chosen type.
- **Step 2:** highlight the problem: blue for what's asked, orange for what's given.
- **Steps 3, 5, 6, 7:** write in plain English.
- **Step 4:** draw on the drawing pad. Tools: pen, line, arrow, box, oval, text, fill (colors and patterns), move, erase. Each fact from Step 5 becomes a label that can be dragged onto the drawing.
- **Step 8:** stays locked until Steps 2–7 are done. Students build the calculation from factor-label lines (units must cancel before numbers unlock) and formula lines (arithmetic with units, including `sqrt( )` and `cbrt( )`).
- **Grading:** only the final answer is graded.
  - Correct if within 5% of the key after unit conversion. A problem can set its own tolerance.
  - Missing or wrong units count as a failed attempt.
  - A hint is offered after 2 failed attempts; the worked solution after 5, or after a correct answer.
- **Saving:** work is saved in the student's browser. An optional **Export PDF** button produces a page for Blackboard.

## Adding or changing problems

The problems live in `problems.json`. To change them:

1. Open `spreadsheets/problems-master.xlsx`, which holds every current problem, and add or edit rows. The **Column guide** sheet explains each column. `spreadsheets/problem-template.xlsx` is a smaller starter file.
2. Open the live tool and go to the **Instructor** tab. Upload the spreadsheet, fix anything it flags, then click **Convert to JSON** and **Download problems.json**.
3. In this repository on GitHub, choose **Add file → Upload files**. Upload the new `problems.json`, which replaces the old one, and commit.
4. Within a minute or two, the live tool shows the new problems to every student.

Keep `problems-master.xlsx` up to date as well, so it stays the master copy.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole tool, as one page |
| `problems.json` | The problem set the tool loads (51 problems) |
| `spreadsheets/problems-master.xlsx` | Editable master copy of all problems |
| `spreadsheets/problem-template.xlsx` | Starter template with three example problems |

## Credits

- The unit engine is copied from the Factor-Label Workbench (lufox2021/Factor-Label-Workbench). Temperature (K) and molarity (M, mM) units were added here.
- The full problem set is also built into `index.html`, so the page works even where `problems.json` can't be loaded. On GitHub Pages, `problems.json` is read first and takes priority.
- Problems DENS-001, ROD-001 and NEON-001 come from the instructor's "Solving Chemistry Problems" slides.
- Problems whose IDs start with MEAS-1, PCT-1, CUM- and CHAL- are original problems written for this tool. They test the same skills as typical first-chapter textbook problems but use their own settings, numbers and solutions.
- Problems whose IDs start with MEAS-00, MOLE-, SOLN-, STOI- and GAS- are adapted from OpenStax, *Chemistry 2e*, by Paul Flowers, Klaus Theopold, Richard Langley and William R. Robinson. https://openstax.org/books/chemistry-2e
  - The current web edition is licensed CC BY-NC-SA 4.0; the 2019 edition is CC BY 4.0.
  - The problems were reworded and the answers recalculated.
  - Each worked solution ends with a credit line naming the source exercise.

## Notes

- **No °C yet.** Temperatures in °C are not yet supported in calculations. Students convert to kelvin first.
- **Counts are plain numbers.** Unitless answers, such as counts and fractions, are entered without units.
