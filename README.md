# Jokes API

This project provides a simple Jokes API built using **Node.js**, **Express.js**, and **body-parser**. The API allows users to manage a collection of jokes, including operations such as retrieving, adding, updating, and deleting jokes. It also includes filtering options and supports different HTTP methods like GET, POST, PUT, PATCH, and DELETE.

---

## Features
- **Get a random joke:** Retrieve a random joke from the collection.
- **Get a specific joke:** Fetch a joke by its unique ID.
- **Filter jokes by type:** Get jokes filtered by their type.
- **Add a new joke:** Create a new joke and add it to the collection.
- **Update a joke (full):** Replace an existing joke with new data.
- **Update a joke (partial):** Modify specific fields of an existing joke.
- **Delete a specific joke:** Remove a joke by its ID.
- **Delete all jokes:** Clear the entire joke collection using a master key.

---

## Prerequisites
To run this project, you need to have:
- **Node.js** installed (v12+ recommended)
- **npm** or **yarn** installed

---

## Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Install dependencies:
   ```bash
   npm install
   ```
---

## Usage
1. Start the server:
   ```bash
   node app.js
   ```

2. The API will be available at:
   ```
   http://localhost:3000
   ```

---

## Endpoints
### 1. **GET /random**
Retrieve a random joke.

**Response Example:**
```json
{
  "id": 5,
  "jokeText": "Why do we never tell secrets on a farm? Because the potatoes have eyes and the corn has ears.",
  "jokeType": "Wordplay"
}
```

---

### 2. **GET /jokes/:id**
Retrieve a specific joke by ID.

**Parameters:**
- `id` (URL Parameter): The ID of the joke.

**Response Example:**
```json
{
  "id": 2,
  "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
  "jokeType": "Puns"
}
```

---

### 3. **GET /filter**
Retrieve jokes filtered by type.

**Query Parameters:**
- `type` (optional): Filter jokes by a specific type (e.g., "Puns", "Science").

**Response Example:**
```json
[
  {
    "id": 8,
    "jokeText": "Parallel lines have so much in common. It's a shame they'll never meet.",
    "jokeType": "Math"
  }
]
```

---

### 4. **POST /jokes**
Add a new joke to the collection.

**Request Body Example:**
```json
{
  "type": "Movies",
  "text": "Why can't you give Elsa a balloon? Because she will let it go."
}
```

**Response Example:**
```json
{
  "id": 101,
  "jokeType": "Movies",
  "jokeText": "Why can't you give Elsa a balloon? Because she will let it go."
}
```

---

### 5. **PUT /jokes/:id**
Replace a joke with new data.

**Parameters:**
- `id` (URL Parameter): The ID of the joke to update.

**Request Body Example:**
```json
{
  "type": "Puns",
  "text": "Why don't some couples go to the gym? Because some relationships don't work out."
}
```

**Response Example:**
```json
{
  "id": 3,
  "jokeType": "Puns",
  "jokeText": "Why don't some couples go to the gym? Because some relationships don't work out."
}
```

---

### 6. **PATCH /jokes/:id**
Update specific fields of a joke.

**Parameters:**
- `id` (URL Parameter): The ID of the joke to update.

**Request Body Example:**
```json
{
  "text": "Why don't skeletons fight each other? They don't have the guts."
}
```

**Response Example:**
```json
{
  "id": 3,
  "jokeType": "Puns",
  "jokeText": "Why don't skeletons fight each other? They don't have the guts."
}
```

---

### 7. **DELETE /jokes/:id**
Delete a specific joke by ID.

**Parameters:**
- `id` (URL Parameter): The ID of the joke to delete.

**Response Example:**
- **Success:** HTTP 200 OK
- **Error:** HTTP 404 Not Found
  ```json
  {
    "error": "Joke id: 99 not found."
  }
  ```

---

### 8. **DELETE /all**
Clear all jokes (requires the master key).

**Query Parameters:**
- `key` (required): The master key to authorize the action.

**Response Example:**
- **Success:** HTTP 200 OK
- **Error:** HTTP 404 Not Found
  ```json
  {
    "error": "masterKey incorrect."
  }
  ```

---


## Example Collection of Jokes
The API is pre-loaded with 100+ jokes of various types, such as:
- Science
- Wordplay
- Puns
- Movies
- Food
- Math
- Sports

---

## Dependencies
- **Express.js:** Web framework for building the API.
- **body-parser:** Middleware for parsing request bodies.
