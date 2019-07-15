# clean-code-ml lesson plan

Target audience:
- Data scientists / data science enthusiasts

Pre-requisites for attendees:
- Some basic experience with Python, Jupyter notebook, `scikit-learn`, and `pandas`

### Session outline
- Temperature check
- Act 1: Why do we need clean code? (A: change and complexity)
    - Demo: pain of refactoring when code is dirty
    - 2 hats: data scientist (exploration) and software dev (production-ready and extensible codebase)
- Interlude: Context on titanic dataset and notebook
    - What the Jupyter notebook does
    - Show data and dataframe
- Act 2: What are code smells? (go through list of What does bad code / clean code look like?)
    - Explicitly call out code smells by name
- Act 3: How do we clean up code in an existing data science / ml codebase?
    - go through refactoring process below
    - Hands-on exercise in refactoring titanic notebook)
- Technical crash course (before hands-on exercise):
    - How to get set up (Docker, run tests, IDE configuration)
    - How to write unit tests (Python syntax + arrange act assert)
    - how to write a unit test with dataframes
    - how to refactor 1 thing (use add_derived_title as demo)

### Refactoring process (for an existing notebook)

- [How to refactor a Jupyter notebook](https://david-tan-2.gitbook.io/clean-code-ml/how-to-refactor-a-jupyter-notebook)

### Code smells

- General [code smells](https://david-tan-2.gitbook.io/clean-code-ml/code-smells)

- Code smells specific to this notebook:
    - too many comments
    - bad variable names
        - train_df and test_df could be better named (without type information)
        - combine
    - too many print statements
        - df.info(), df.head(), df.describe(), etc. - is there any other way that we can get feedback on the data?
    - no tests for data transformations (e.g. cell 17 onwards)
    - cell 18, 19 (mutation to `dataset` outside of a function)
    - duplication in model training code. Can extract to a function.
    - duplication in EDA code. Can extract to a function.
    - duplication in how test_df and train_df are joined. Why not just join it once, and use the combined df for all data transformations?

### Bonus
- Set up CI pipeline on CircleCI (run unit tests + run jupyter notebook and ensure no errors)

### Changelog
- [titanic-exercise-0](https://github.com/davified/clean-code-ml/blob/master/notebooks/titanic-exercise-0.ipynb): Original notebook
- [titanic-exercise-1](https://github.com/davified/clean-code-ml/blob/master/notebooks/titanic-exercise-1.ipynb): Removed most print statements
    - Participants should use this notebook to list code smells
- [titanic-exercise-2](https://github.com/davified/clean-code-ml/blob/master/notebooks/titanic-exercise-2.ipynb): Add exercises for refactoring
    - Participants should refactor this notebook
- [titanic-exercise-solution](https://github.com/davified/clean-code-ml/blob/master/notebooks/titanic-exercise-solution.ipynb): Final state of notebook after refactoring
- [final code](https://github.com/davified/clean-code-ml/blob/master/src/train.py): Move code from jupyter notebook to plain Python file/module.

### Note to self (david)
- Set up split screen to reduce toggling
- Write session plan (with time) on the wall and track progress as we go
- Create a google doc and share bit.ly link with class