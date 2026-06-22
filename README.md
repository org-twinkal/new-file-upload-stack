# JWT file upload stack

This package contains:
- frontend static pages: `login.html`, `signup.html`, `upload.html`
- `frontend/nginx.conf` to serve the pages and reverse proxy API calls
- `auth/auth_service.py` for signup/login with JWT and MongoDB
- `backend/app.py` for protected file upload/list/download to Azure Blob Storage
- `docker-compose.yml` to start frontend, auth, backend and MongoDB

## Run
1. Copy `.env.example` to `.env` and change values.
2. Build and start:
   ```bash
   docker compose up --build -d
   ```
3. Open `http://<your-vm-ip>/`

## Required Azure configuration
- The VM must be able to reach the Azure Storage Account privately.
- Blob private endpoint and private DNS must already be configured in your Azure network.
- The VM identity used by Docker must have Blob data permissions on the storage account/container.

## Notes
- Login page is the first page.
- Signup is a separate page.
- Upload/list/download page is shown only after successful login because the browser stores the JWT token and sends it as a `Bearer` token to protected routes.
