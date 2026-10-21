# rest-api-assignment

A small REST API for creating, reading, updating, and deleting users, built with Node.js and Express. It started from a course template, and I implemented the user endpoints.

## What it does

Users are kept in memory. Each one has an `id`, a `name`, and an `email`, and the server makes the `id` with `crypto.randomUUID()`.

| Method | Route | What it does |
| --- | --- | --- |
| `POST` | `/users` | Creates a user from `{ "name", "email" }`. Returns `201` with the user, or `400` if a field is missing |
| `GET` | `/users/:id` | Returns the user, or `404` |
| `PUT` | `/users/:id` | Replaces the name and email. Returns the user, `400` if a field is missing, or `404` |
| `DELETE` | `/users/:id` | Deletes the user and returns `204`, or `404` |
| `GET` | `/` | Returns `Hello World!` (from the template) |

## Tech stack

Node.js, Express, Jest and Supertest for tests, GitHub Actions for CI.

## How to run it

You need Node.js and npm.

```sh
npm install
npm start
```

The server listens on `http://localhost:3000`.

```sh
curl -X POST -H "Content-Type: application/json" -d '{"name":"Ada","email":"ada@example.com"}' http://localhost:3000/users
```

## Tests

```sh
npm test
```

This runs 7 Jest tests in `tests/users.test.js` against the routes above. The test file and the GitHub Actions workflow came with the template.

## Limitations

Data is stored in memory, so every user is gone when the server stops.
