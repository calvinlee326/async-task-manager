
# Async Task Manager (Using FastAPI and Heroku)

This is an asynchronous task manager built with FastAPI and deployed on Heroku. It allows users to create and track long-running tasks that are processed asynchronously in the background using `BackgroundTasks` and `asyncio`.

## Features

- Asynchronous task management using `asyncio` and FastAPI's `BackgroundTasks`.
- Deploys on Heroku using `uvicorn` as the ASGI server.
- Real-time API documentation and interactive testing through FastAPI's Swagger UI.

## Technologies Used

- **FastAPI**: Web framework for building APIs.
- **Uvicorn**: ASGI server to run FastAPI.
- **Python**: Programming language for writing the application.
- **Heroku**: Cloud platform for deployment.

## Getting Started

### Prerequisites

Ensure that you have the following installed on your local development machine:

- Python 3.x
- FastAPI
- Uvicorn
- Git
- Heroku CLI (for deployment)

### Setup Instructions

1. **Clone the Repository**

   First, clone the repository to your local machine using Git:

   ```bash
   git clone https://github.com/yourusername/async-task-manager.git
   cd async-task-manager
   ```

2. **Create and Activate Virtual Environment**

   Create a Python virtual environment and activate it:

   ```bash
   python -m venv venv
   source venv/bin/activate  # For Mac/Linux
   venv\Scripts\activate  # For Windows
   ```

3. **Install Dependencies**

   Install all the dependencies listed in the `requirements.txt` file:

   ```bash
   pip install -r requirements.txt
   ```

4. **Run the Development Server**

   Start the Uvicorn development server locally:

   ```bash
   uvicorn app:app --reload
   ```

   Open your browser and visit:

   ```
   http://localhost:8000
   ```

   You should see a JSON message returned by the FastAPI application.

5. **Access Swagger Documentation**

   To explore and test the API using FastAPI's Swagger documentation, open your browser and visit:

   ```
   http://localhost:8000/docs
   ```

### Deployment to Heroku

1. **Login to Heroku**

   Make sure you have Heroku CLI installed. Then, login to Heroku:

   ```bash
   heroku login
   ```

2. **Create a Heroku App**

   Create a new Heroku app using the following command:

   ```bash
   heroku create your-app-name
   ```

3. **Deploy the App**

   Push the code to Heroku and deploy the FastAPI app:

   ```bash
   git push heroku main
   ```

4. **Visit the Live App**

   Once the deployment is successful, you can open the live application using:

   ```bash
   heroku open
   ```

   Your app should now be live on the web!

### Live Application

The live application is available at:
![Screenshot 2024-09-13 at 3 14 30 PM](https://github.com/user-attachments/assets/ea67956a-88c4-4e60-87f6-9a45c3ae4f9b)

[https://async-task-4e020a9578b4.herokuapp.com/docs](https://async-task-4e020a9578b4.herokuapp.com/docs)

### Project Structure

```
async-task-manager/
├── app.py
├── task_manager/
│   ├── __init__.py
│   └── background_tasks.py
├── venv/
├── requirements.txt
├── Procfile
├── README.md
└── runtime.txt (optional)
```

## How to Use

### 1. Access the App

Once the app is deployed, you can access it at the following URL:

```
https://async-task-4e020a9578b4.herokuapp.com/
```

### 2. Use FastAPI Swagger Documentation

FastAPI provides an interactive API documentation (Swagger UI) that allows you to test and call the API.

- To access the documentation, visit the following URL:
  ```
  https://async-task-4e020a9578b4.herokuapp.com/docs
  ```

- This will open an interactive interface where you can view and test all available API endpoints.

### 3. Test API Endpoints

The application provides multiple API endpoints for interacting with the system. Below are examples:

#### POST `/run-task/`

This endpoint creates and runs a long-running task in the background. You can submit data to trigger the task.

- **URL**: `/run-task/`
- **Method**: `POST`
- **Parameters**: Submit `JSON` data in the request body
  - Example data:
    ```json
    {
      "task_data": "example_task_data"
    }
    ```
- **Response**: Upon success, you will receive a message indicating the task is running in the background:
  ```json
  {
    "message": "Task is running in the background"
  }
  ```

#### GET `/status/{task_id}` (Optional)

This endpoint is used to check the status of a running task if task status tracking is implemented.

- **URL**: `/status/{task_id}`
- **Method**: `GET`
- **Parameters**: 
  - `task_id`: The unique ID of the task created previously
- **Response**: You will receive the current status of the task, for example:
  ```json
  {
    "task_id": "12345",
    "status": "in_progress"
  }
  ```

### 4. Test API Requests

You can use tools like `curl` or Postman to test the API.

- **Using `curl` to test the API**:
  ```bash
  curl -X POST https://async-task-4e020a9578b4.herokuapp.com/run-task/ -H "Content-Type: application/json" -d '{"task_data": "example_task_data"}'
  ```

- **Using Postman to test the API**:
  1. Open Postman and create a new request.
  2. Set the request method to `POST` and enter the API URL `https://async-task-4e020a9578b4.herokuapp.com/run-task/`.
  3. In the Body section, select `raw` and choose `JSON` format, then enter the data:
     ```json
     {
       "task_data": "example_task_data"
     }
     ```
  4. Send the request and check the response.

## Future Improvements

- Task status tracking (e.g., `pending`, `in_progress`, `completed`).
- Integration with databases for task persistence.
- WebSocket integration for real-time task progress updates.

## License

This project is open-source and available under the [MIT License](LICENSE).
