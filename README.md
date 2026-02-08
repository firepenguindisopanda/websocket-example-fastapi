## Run the API Locally

```bash
.venv\Scripts\uvicorn.exe main:app --reload
```

### Generating the requirements.txt file from pyproject.toml

```bash
uv pip compile pyproject.toml -o requirements.txt
```

---

## Deploying to Render

This project is ready to deploy to [Render](https://render.com), which supports FastAPI and WebSockets out of the box.

### Steps to Deploy

1. **Push your code to GitHub.**
2. **Log in to the Render dashboard.**
3. Click **New +** → **Web Service**.
4. Connect your GitHub and select this repository.
5. Use the following settings:
		- **Environment:** Python 3.x
		- **Build Command:** `pip install -r requirements.txt`
		- **Start Command:** `uvicorn main:app --host 0.0.0.0 --port 10000`
		- **Port:** 10000 (set as an environment variable if needed)
6. Click **Create Web Service**. Render will build and deploy your app.

### WebSocket Support

Render supports WebSockets natively—no extra configuration is needed.

### Infrastructure as Code (Optional)

You can use the provided `render.yaml` file for automatic deployment setup:

```yaml
services:
	- type: web
		name: fastapi-websocket-app
		env: python
		buildCommand: "pip install -r requirements.txt"
		startCommand: "uvicorn main:app --host 0.0.0.0 --port 10000"
		plan: free
		envVars:
			- key: PORT
				value: 10000
```

This file should be placed in the root of your repository.