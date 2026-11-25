# Notesfy – full-stack notes app

Backend (Node + Express + MongoDB) and frontend (React) in one project.
The frontend is already built and served by the backend, so you only need this:

## Run (3 steps)
```bash
cd backend
cp .env.example .env        # then open .env and paste your MongoDB URL after  mongourl=
npm install
npm start                   # open http://localhost:8080
```
That's it – register an account and start writing notes.

## Features
Register/login (JWT) · rich-text editor (headings, bold/italic/underline/strike, highlight, colour, lists, checklists, tables, quote, link, code) · public & private notes · Explore page for public notes (with view counts) · tags + filter chips · search (Ctrl/⌘+K) · sort · grid/list view · pin · trash & restore · calendar with reminder dates · dark mode · mobile layout.

## API (all under /api)
| Method | Path | Auth | |
|---|---|---|---|
| POST | /user/register, /user/login | – | login returns `{token, name}` |
| GET | /notes/public | – | all public notes |
| GET | /notes/:id | optional | public: anyone, private: owner |
| GET/POST | /notes | yes | my notes / create |
| PUT | /notes/:id | yes | edit |
| DELETE | /notes/:id | yes | move to trash |
| PATCH | /notes/:id/restore | yes | restore |
| DELETE | /notes/:id/purge | yes | delete forever |

Send the token as the `Authorization` header (no "Bearer" prefix), same as your original code.

## Optional: edit the frontend
```bash
cd frontend && npm install
npm run dev      # http://localhost:5173 (talks to backend on :8080)
npm run build    # rebuilds into backend/public
```

## Notes
- Set `JWT_SECRET` in `.env` before deploying anywhere public.
- Logged-out visitors can read **public** notes; private notes are only returned to their owner.
