# Aurora CS Course Scheduler (M1)

A React app that displays the Aurora CS Developer Track course catalog, tracks which courses a student has completed, and shows which courses are available or locked based on prerequisites.

**Course:** CSC3700, Advanced Web Application Development, Fall 2026
**Authors:** Johnny Christiansen & Jaedon Vaughn

## Tech Stack

- React + Vite
- Bootstrap
- React Router
- JSON Server (mock API for M1)

## Prerequisites

- [Node.js](https://nodejs.org/) v20.19+ (or v22.12+) and npm

## How to Run

1. **Clone the repo and install dependencies**

   ```bash
   git clone https://github.com/Jaedog117/CSC-3700
   cd CSC-3700
   npm install
   ```

2. **Create the `.env` file** in the project root (it is not committed to git).
   Copy the example file:

   ```bash
   # Windows (Command Prompt)
   copy .env.example .env

   # Mac / Linux / PowerShell
   cp .env.example .env
   ```

   The file should contain:

   ```
   VITE_API_BASE_URL=http://localhost:3333
   ```

3. **Start JSON Server** (in its own terminal; leave it running)

   ```bash
   npx json-server --watch db/db.json --port 3333
   ```

   The first time, npx may ask to install `json-server`. Type `y` to continue.
   Check it works: http://localhost:3333/courses should show all 10 courses.

4. **Start the React app** (in a second terminal)

   ```bash
   npm run dev
   ```

5. Open **http://localhost:5173** in your browser.

## Features

- Course catalog fetched from JSON Server with a custom `useFetch` hook
- Loading and error states
- Checkbox to mark courses Completed, enforced by prerequisites
- Unchecking a course automatically unchecks every course that depends on it
- Completed / Available / Locked status badges
- Filter: All Courses, Completed Only, Remaining
- Progress summary (completed, available, locked)
- Save button stores progress in localStorage and restores it on reload
- React Router navbar with Home (`/`) and About (`/about`) pages

## Project Structure

```
db/db.json              JSON Server data
src/components/         CourseCard, CourseList, NavBar, ProgressSummary
src/hooks/useFetch.js   Data fetching hook
src/pages/              HomePage, AboutPage
.env.example            Template for the .env file
.env                    API base URL (not committed)
```