# Quiz API Documentation

This documentation provides an overview of the Quiz API endpoints.

## Base URL

The base URL for all API endpoints is `http://localhost:8000/`.

## API Endpoints

### Create a Quiz

Endpoint: `POST /quizzes/`

Create a new quiz by sending a POST request to this endpoint.

#### Request Body

- `question` (string, required): The text of the question.
- `options` (array, required): An array of answer options for the question.
- `rightAnswer` (integer, required): The index of the correct answer in the options array.
- `startDate` (string, required): The date and time when the quiz should start (format: "YYYY-MM-DDTHH:MM:SSZ").
- `endDate` (string, required): The date and time when the quiz should end (format: "YYYY-MM-DDTHH:MM:SSZ").

#### Response

- Status: 201 Created
- Body: "Quiz created successfully."

### Get Active Quiz

Endpoint: `GET /quizzes/active/`

Retrieve the active quiz, which is the quiz that is currently within its start and end time.

#### Response

- Status: 200 OK
- Body:
  - `id` (integer): The ID of the active quiz.
  - `question` (string): The text of the question.
  - `options` (array): An array of answer options for the question.
  - `rightAnswer` (integer): The index of the correct answer in the options array.
  - `startDate` (string): The date and time when the quiz should start.
  - `endDate` (string): The date and time when the quiz should end.
  - `status` (string): The status of the quiz (inactive, active, or finished).

### Get Quiz Result

Endpoint: `GET /quizzes/:id/result/`

Retrieve the result of a quiz by its ID.

#### URL Parameters

- `id` (integer, required): The ID of the quiz.

#### Response

- Status: 200 OK
- Body:
  - `rightAnswer` (integer): The index of the correct answer for the quiz.

### Get All Quizzes

Endpoint: `GET /quizzes/all/`

Retrieve all quizzes.

#### Response

- Status: 200 OK
- Body: An array of quizzes, where each quiz object has the following properties:
  - `id` (integer): The ID of the quiz.
  - `question` (string): The text of the question.
  - `options` (array): An array of answer options for the question.
  - `rightAnswer` (integer): The index of the correct answer in the options array.
  - `startDate` (string): The date and time when the quiz should start.
  - `endDate` (string): The date and time when the quiz should end.
  - `status` (string): The status of the quiz (inactive, active, or finished).

## Error Handling

The API implements error handling for all endpoints and returns appropriate error responses. Possible error responses include:

- 400 Bad Request: Invalid request data or missing required fields.
- 404 Not Found: The requested quiz or resource does not exist.
- 500 Internal Server Error: An unexpected error occurred on the server.

Please ensure that you provide valid request data and handle error responses accordingly.

