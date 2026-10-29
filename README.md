# Plan-It!

Plan-It! is a collaborative event-planning web application that helps groups find a time when everyone is available. Users can maintain personal calendars, invite friends or groups to events, import an NUSMods timetable, and choose event times through availability suggestions or polls.

Built as a two-person NUS Orbital project.

## Highlights

- **Personal and shared calendars** — Create, edit, delete, and view personal, friend, and group events in weekly or monthly calendar views.
- **NUSMods timetable import** — Import an NUSMods timetable to automatically add recurring class events.
- **Friends and groups** — Send friend requests, create groups, and organise events with selected friends or entire groups.
- **Availability suggestions** — Combines attendees’ schedules and finds the free intervals within a selected time range.
- **Scheduling polls** — Let attendees vote on proposed times; the event creator can finalise the highest-voted option, with the earliest time used as a tiebreaker.
- **Flexible scheduling** — Supports event priority labels (`compulsory`, `flexible`, and `optional`) and weekly, monthly, or annual recurrence.

## Tech stack

| Area | Technologies |
| --- | --- |
| Frontend | React, TypeScript, CSS |
| Backend and database | Supabase, PostgreSQL, Row Level Security |
| Calendar | Schedule-X |
| External data | NUSMods API |
| Tooling and deployment | Node.js, GitHub, Vercel |

## How it works

Plan-It! models users, events, friendships, groups, event attendees, and group membership as relational data in PostgreSQL. Supabase authentication and Row Level Security policies ensure that users can access only the data needed for their own events, groups, and invitations.

For an undecided event, Plan-It! retrieves the combined schedules of its attendees, sorts the occupied time intervals, and computes the gaps between them. This produces the proposed time slots in which everyone is free. Events marked as flexible or optional are surfaced as soft conflicts so that attendees can still consider those slots.

## Getting started

### Prerequisites

- Node.js and npm
- A Supabase project

### Installation

1. Clone the repository.

   ```bash
   git clone https://github.com/shana-nadia/<repository-name>.git
   cd <repository-name>
   ```

2. Install dependencies.

   ```bash
   npm install
   ```

3. Create a `.env` file in the project root and add your Supabase project credentials.

   ```env
   REACT_APP_SUPABASE_URL=your_supabase_project_url
   REACT_APP_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

4. Start the development server.

   ```bash
   npm start
   ```

## Notes

- Never commit `.env` files or real credentials. Keep `.env` in `.gitignore` and use your own Supabase project for local development.
- The NUSMods importer was built around the academic-term configuration used during the project. It may require an update before importing a current timetable.

## Future improvements

- Make the NUSMods importer automatically determine the current academic year and semester.
- Add notifications and reminders for upcoming events and invitations.
- Improve availability suggestions with user-configurable working hours and preferred event durations.
