# FullStackOpen-Dairy

Personal learning diary for [Full Stack Open](https://fullstackopen.com/en/). I’m “making learning visible” with daily TIL notes and Mermaid diagrams for exercises.

## Structure

- `part0/` – Fundamentals of Web Apps  
  - `0.4-new-note-sequence.md`  
  - `0.5-spa-load-diagram.md`  
  - `0.6-spa-new-note-sequence.md`
- `notes/` – Daily TIL (Today I Learned) entries, e.g. `2025-09-30.md`
- Future parts mirror the course’s suggested layout:
  ```
  part1/
    courseinfo/
    unicafe/
    anecdotes/
  part2/
    courseinfo/
    phonebook/
    countries/
  ```
  (Matches the course’s recommended submission structure.)

## My study routine (TL;DR)

1. Read the lesson with DevTools open and verify behaviors yourself.  
2. Capture 3–6 bullets in a TIL note; add a Mermaid diagram when relevant.  
3. Commit immediately with a descriptive `docs(...)` message.  
4. Next session, answer yesterday’s self-quiz from memory (retrieval), then continue (spaced review).

### TIL template (`notes/YYYY-MM-DD.md`)
```md
# TIL – YYYY-MM-DD (Part X)
## Takeaways
- …
## Teach-back (in my own words)
…
## Self-quiz (answer tomorrow from memory)
1) …
2) …
3) …
```

## Diagrams on GitHub

GitHub renders Mermaid inside fenced code blocks labeled `mermaid`. No images needed — just keep diagrams as Markdown.

## Commit messages

Using Conventional Commits keeps history tidy for a diary repo:
- `docs(part0): add 0.4 new note sequence diagram`
- `docs(notes): TIL on HTTP redirects and status codes`
- `chore(repo): add notes/ template`

## Progress

- [x] Part 0 (0.1–0.6)
- [ ] Part 1 – Introduction to React
- [ ] Part 2 – Communicating with server
- [ ] Part 3 – Programming a server with Node/Express
