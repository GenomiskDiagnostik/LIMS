
#<img width="90" height="90" alt="logo" src="https://github.com/user-attachments/assets/cfdd5b73-d477-477d-9ba6-acba4826ea60" /> GlimR - Genetic LIMS Reporter

A Laboratory Information Management System (LIMS) for genomic diagnostics developed by Thomas Lindestrand-Hansen. This repository contains the backend, frontend, configuration, and deployment scripts used to manage samples, track workflows, and integrate with sequencing and analysis pipelines.
If you need a the logo.png file - right click the logo and save as logo.png. Place the file next to GlimR.html.

## Status

Active — under active development. See the repository for current branches and issues.

## Features

- Sample registration and tracking
- Workflow and protocol management
- Integration with sequencing instruments and analysis pipelines
- User and role-based access control
- Audit trails and reporting
- Import/export (CSV, JSON) of sample and run data

<img width="1567" height="797" alt="Skærmbillede 2025-10-21 101535" src="https://github.com/user-attachments/assets/6bfa5412-1502-49f5-b699-3fc3bca23bf7" />

## Technologies

List of primary technologies used in this repository (actual components may vary by module):

- Programming languages: Python, JavaScript/TypeScript
- Web framework: Django / Flask / FastAPI (backend)
- Frontend: React / Vue (web UI)
- Database: PostgreSQL
- Task queue: Celery / RQ
- Containerization: Docker

## Getting started

1. Clone the repository:

   git clone https://github.com/GenomiskDiagnostik/LIMS.git
   cd LIMS

2. Review root README and module-specific READMEs for detailed setup instructions.

3. Create and activate a virtual environment (for Python components):

   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt

4. Configure environment variables. Copy example env files if provided:

   cp .env.example .env
   # Edit .env to set database, secret keys and service endpoints

5. Initialize the database and run migrations (example for Django):

   python manage.py migrate
   python manage.py createsuperuser

6. Start services locally using Docker Compose if provided:

   docker-compose up --build

## Running tests

Run unit and integration tests using the repository's preferred test runner. Example for Python:

   pytest

## Contributing

We welcome contributions. Please follow these guidelines:

- Read the code of conduct (if present).
- Open an issue before starting larger changes to discuss design and requirements.
- Create feature branches named feature/short-description and open a pull request.
- Write tests for new features and ensure existing tests pass.

## Security and data sensitivity

This project handles sensitive genomic and clinical information. Follow your organization's data protection policies and applicable laws (e.g., GDPR). Do not commit real patient data or secrets to the repository.

## License

Specify the license used by this repository (e.g., MIT, Apache-2.0). If none is present, add a LICENSE file or contact the repository owners for clarification.

## Contact

Maintained by GenomiskDiagnostik. For questions, open an issue or contact the maintainers listed in the repository.
