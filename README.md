

## Run the api

```bash
.venv\Scripts\uvicorn.exe main:app --reload
```

### Generating the requirements.txt file from pyrproject.toml

`uv pip compile pyproject.toml -o requirements.txt`