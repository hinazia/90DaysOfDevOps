- Write in your notes: Why should you never print secrets in CI logs?
  Because they are sensitive credentials and should not be available to everyone for malicious activities.

- A **file** is just something that exists on the runner's disk during that one job — the moment the job finishes,
  the runner (a temporary VM) is destroyed, and everything on it, including your file, disappears.

- An **Artifact** is that file deliberately saved outside the runner, onto GitHub's own storage, before the runner gets wiped. 
  That's the entire purpose of upload-artifact — it's the bridge that lets a file survive past the runner's lifetime.

Two things this enables:

- Passing files between jobs — job A's runner and job B's runner are two completely separate machines. 
- Job B can't see job A's disk at all. Upload in job A, download in job B — that's the only way to move a file across jobs.
