Lecture and lab notebooks, numbered to match the schedule in the main README.

A note on notebooks and git: a `.ipynb` file stores its outputs, so two people who
run the same notebook produce different files, and diffs are unreadable. Before
committing, **Kernel → Restart and Clear Output**. If this becomes tedious, install
[`nbstripout`](https://github.com/kynan/nbstripout) once and it happens automatically:

```bash
pip install nbstripout
nbstripout --install
```
