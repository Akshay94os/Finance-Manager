# Finance-Manager

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-3.2%2B-green)](https://www.djangoproject.com/)
[![Version](https://img.shields.io/badge/Version-v1.0.0-blue)](https://github.com/Akshay94os/Finance-Manager/releases)

## Overview

Finance-Manager is a personal web-based application designed to help individuals track their income, manage expenses, and gain better control over their financial health. It provides a straightforward interface to log transactions, categorize spending, and visualize financial data, empowering users to make informed decisions about their money.

This application is ideal for anyone looking for a simple yet effective tool to monitor their personal finances without the complexity of enterprise solutions. It aims to provide clarity and insights into spending habits and income streams.

## Features

*   **User Authentication**: Secure user registration and login system.
*   **Income Tracking**: Record and manage all sources of income.
*   **Expense Tracking**: Log daily, weekly, or monthly expenses with ease.
*   **Categorization**: Assign categories to transactions (e.g., Food, Transport, Salary) for better organization and analysis.
*   **Budget Management**: Create and monitor budgets for different categories to control spending.
*   **Transaction History**: View a detailed list of all past income and expense transactions.
*   **Dashboard Overview (Planned)**: A summary dashboard to visualize financial trends and key metrics.

## Tech Stack

The Finance-Manager project is built using robust and widely-adopted web technologies:

*   **Backend**:
    *   **Python**: The core programming language.
    *   **Django**: A high-level Python web framework that encourages rapid development and clean, pragmatic design.
*   **Database**:
    *   **SQLite**: Default database for development and lightweight deployments. Configurable for PostgreSQL/MySQL for production.
*   **Frontend**:
    *   **HTML5**: For structuring web content.
    *   **CSS3**: For styling and responsive design.
    *   **JavaScript**: For interactive elements (minimal, as Django handles most logic).

## Architecture

The project follows Django's Model-View-Template (MVT) architectural pattern, which is a variation of MVC.

```
Finance-Manager/
├── FinanceManager/             # Django Project Configuration
│   ├── settings.py             # Global settings for the project
│   ├── urls.py                 # Project-wide URL routing
│   └── ...
├── fin_manager/                # Core Finance Management Application
│   ├── models.py               # Database models (Income, Expense, Category, Budget)
│   ├── views.py                # Business logic and data processing
│   ├── forms.py                # Forms for user input
│   ├── templates/              # HTML templates for rendering pages
│   ├── urls.py                 # App-specific URL routing
│   └── ...
├── manage.py                   # Django's command-line utility
└── db.sqlite3                  # Default SQLite database file
```

*   **`FinanceManager/`**: This directory contains the main project configuration, including global settings (`settings.py`), URL routing for the entire application (`urls.py`), and WSGI/ASGI configurations.
*   **`fin_manager/`**: This is the primary Django application responsible for all finance management functionalities. It defines the data structures (models), handles user requests and business logic (views), manages user input (forms), and renders the user interface (templates).
*   **`manage.py`**: A command-line utility that lets you interact with this Django project in various ways (e.g., running the development server, performing database migrations).

**Data Flow Overview**:
1.  A user's request comes in via the browser.
2.  The request is routed by `FinanceManager/urls.py` to the appropriate view in `fin_manager/views.py`.
3.  The view processes the request, interacting with models in `fin_manager/models.py` to fetch or store data in `db.sqlite3`.
4.  The view then renders an HTML template from `fin_manager/templates/`, populating it with data from the models.
5.  The rendered HTML is sent back to the user's browser.

## Getting Started

Follow these steps to get your local development environment up and running.

### Prerequisites

Before you begin, ensure you have the following installed on your system:

*   **Python**: Version 3.8 or higher.
    *   [Download Python](https://www.python.org/downloads/)
*   **pip**: Python package installer (usually comes with Python).
*   **Git**: For cloning the repository.
    *   [Download Git](https://git-scm.com/downloads)

### Installation

1.  **Clone the repository**:

    ```bash
    git clone https://github.com/Akshay94os/Finance-Manager.git
    cd Finance-Manager
    ```

2.  **Create and activate a virtual environment**:
    It's highly recommended to use a virtual environment to manage project dependencies.

    ```bash
    python -m venv venv
    # On Windows
    .\venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3.  **Install dependencies**:
    Install all required Python packages using `pip`.
    *(Note: A `requirements.txt` file is assumed for dependency management. If not present, create one with `Django` and other necessary packages.)*

    ```bash
    pip install Django # Or pip install -r requirements.txt if available
    ```

4.  **Apply database migrations**:
    This will create the necessary database tables for the application.

    ```bash
    python manage.py makemigrations fin_manager
    python manage.py migrate
    ```

5.  **Create a superuser (optional but recommended)**:
    This allows you to access the Django admin panel.

    ```bash
    python manage.py createsuperuser
    ```
    Follow the prompts to create your superuser account.

6.  **Run the development server**:

    ```bash
    python manage.py runserver
    ```
    The application will now be accessible in your web browser at `http://127.0.0.1:8000/`.

### Configuration

The main configuration file is `FinanceManager/settings.py`.

*   **`SECRET_KEY`**: For production environments, ensure this is a strong, unique, and securely managed key. It's recommended to use an environment variable for this.
*   **`DEBUG`**: Set to `False` in production for security and performance.
*   **`DATABASES`**: You can modify this section to connect to a different database (e.g., PostgreSQL, MySQL) instead of SQLite.
*   **Environment Variables**: For sensitive information like `SECRET_KEY`, consider using a `.env` file and a package like `python-dotenv`.

    Example `.env` (create this file in the project root if you use `python-dotenv`):
    ```
    SECRET_KEY='your_super_secret_key_here'
    DEBUG=True
    ```

## Usage

Once the server is running, open your web browser and navigate to `http://127.0.0.1:8000/`.

1.  **Register**: Click on the "Sign Up" or "Register" link to create a new user account.
2.  **Login**: Use your newly created credentials to log in.
3.  **Add Income**: Navigate to the income section and add your income sources with amounts and dates.
4.  **Add Expense**: Go to the expenses section to log your spending, assigning categories as needed.
5.  **View Transactions**: Explore your transaction history to see a detailed list of all financial activities.
6.  **Manage Budgets**: Set up budgets for different spending categories to help control your finances.

## Development

### Setting up Development Environment

The steps under "Installation" cover the basic setup for development. Ensure your virtual environment is active.

### Running Tests

To run the project's tests (if any are implemented in `fin_manager/tests.py`):

```bash
python manage.py test fin_manager
```

### Code Style Guidelines

*   Follow **PEP 8** for Python code style.
*   Use clear and descriptive variable and function names.
*   Add comments where complex logic is involved.

### Debugging Tips

*   When `DEBUG` is `True` in `settings.py`, Django provides detailed error pages in the browser.
*   Use `print()` statements in your views or models for quick debugging.
*   Utilize Python's `pdb` debugger for more in-depth debugging sessions.

## Deployment

Deploying a Django application involves several considerations for production readiness.

1.  **Environment Variables**: Ensure `SECRET_KEY` and other sensitive settings are loaded from environment variables.
2.  **Database**: Switch from SQLite to a production-grade database like PostgreSQL or MySQL.
3.  **Web Server**: Use a production-ready web server like Gunicorn or uWSGI to serve the Django application, typically behind a reverse proxy like Nginx or Apache.
4.  **Static Files**: Configure Django to serve static files efficiently, often by collecting them into a single directory (`python manage.py collectstatic`) and serving them directly via Nginx or a CDN.
5.  **Security**: Set `DEBUG = False` in `settings.py`, configure allowed hosts (`ALLOWED_HOSTS`), and ensure HTTPS is enforced.

**Example Gunicorn command (after installing `gunicorn`):**

```bash
gunicorn FinanceManager.wsgi:application --bind 0.0.0.0:8000
```

For cloud platforms like Heroku, AWS Elastic Beanstalk, or Google Cloud Run, refer to their specific Django deployment guides.

## API Documentation

This project is primarily a full-stack web application and does not currently expose a public RESTful API for external consumption. All interactions are handled through the web interface.

## Contributing

We welcome contributions to the Finance-Manager project! If you'd like to contribute, please follow these guidelines.

1.  **Fork the repository**: Start by forking the project to your GitHub account.
2.  **Clone your fork**:
    ```bash
    git clone https://github.com/YOUR_USERNAME/Finance-Manager.git
    cd Finance-Manager
    ```
3.  **Create a new branch**:
    ```bash
    git checkout -b feature/your-feature-name
    ```
4.  **Make your changes**: Implement your feature or fix the bug.
5.  **Write tests**: If applicable, add tests for your changes.
6.  **Commit your changes**:
    ```bash
    git commit -m "feat: Add new feature for X"
    ```
    (Please use conventional commit messages if possible.)
7.  **Push to your fork**:
    ```bash
    git push origin feature/your-feature-name
    ```
8.  **Create a Pull Request**: Go to the original repository on GitHub and open a new Pull Request from your forked branch.

### Code Review Guidelines

*   Ensure your code adheres to PEP 8 standards.
*   Provide clear and concise commit messages.
*   Explain the purpose of your changes in the pull request description.
*   Be open to feedback and suggestions during the review process.

## Troubleshooting

### Common Issues

*   **`ModuleNotFoundError: No module named 'Django'`**:
    *   **Solution**: Ensure your virtual environment is activated (`source venv/bin/activate`) and Django is installed (`pip install Django`).
*   **`django.db.utils.OperationalError: no such table: fin_manager_income`**:
    *   **Solution**: You likely haven't run migrations. Execute `python manage.py makemigrations fin_manager` followed by `python manage.py migrate`.
*   **`DisallowedHost at /`**:
    *   **Solution**: When `DEBUG` is `False`, you must set `ALLOWED_HOSTS` in `FinanceManager/settings.py` to include your domain or IP address. For development, `ALLOWED_HOSTS = ['127.0.0.1', 'localhost']` is common.
*   **`SECRET_KEY` warning**:
    *   **Solution**: Ensure your `SECRET_KEY` is set in `settings.py` (or via environment variables) and is a long, random string.

### Where to Get Help

If you encounter issues not covered here, please open an issue on the [GitHub Issues page](https://github.com/Akshay94os/Finance-Manager/issues).

## Roadmap

*   **Data Visualization**: Implement charts and graphs to visualize income vs. expenses, spending by category, and financial trends.
*   **Recurring Transactions**: Add functionality to manage recurring income and expenses automatically.
*   **Reporting**: Generate custom financial reports.
*   **User Profiles**: Enhance user profile management.
*   **Mobile Responsiveness**: Improve the UI/UX for mobile devices.

## License & Credits

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

### Contributors

*   [Akshay94os](https://github.com/Akshay94os) - Initial work and primary maintainer.

### Acknowledgments

*   Built with the excellent [Django](https://www.djangoproject.com/) web framework.