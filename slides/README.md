Put lecture slides here as **PDF**, one file per lecture, named
`01-intro.pdf`, `02-....pdf`, and so on.

Commit the PDF, not the Keynote/PowerPoint/`.tex` source, unless you want students
to have the source. If you write slides in Beamer or Quarto, keep the source in a
separate private repo and commit only the compiled output here — otherwise the
history fills with binary build artefacts.

Git handles PDFs by storing a full new copy on every commit. If you re-export slides
often, the repository will grow. For a one-semester course this does not matter; if
you reuse the repo for years, start a fresh one each year (`econ-xxx-2027`).
