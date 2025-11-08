# HealthCheckUp

A small utility to run health checks against services and report status, metrics, and alerts.

## Features
- Probe HTTP(S), TCP and custom checks
- Configurable intervals and timeouts
- JSON/Plain output and simple alerts
- Docker-friendly and lightweight

## Requirements
- Node >= 14 / Python >= 3.8 / Go 1.16 (adjust per implementation)
- Network access to target services

## Installation
1. Clone the repo:
    ```
    git clone <repo-url>
    cd healthcheckup
    ```
2. Install dependencies (example):
    - Node: `npm install`
    - Python: `pip install -r requirements.txt`
    - Go: `go build ./...`

## Configuration
Create a config file (example `config.yml` or `config.json`):
```yaml
checks:
  - name: web
     type: http
     url: http://localhost:8080/health
     interval: 30s
     timeout: 5s
  - name: redis
     type: tcp
     host: 127.0.0.1
     port: 6379
     interval: 60s
```

## Usage
Run the service:
- Node: `npm start -- --config config.yml`
- Python: `python healthcheckup.py --config config.yml`
- Go: `./healthcheckup --config config.yml`

Output examples:
- Human readable: logs to stdout
- JSON: `--output json` for machine consumption

## Docker
Build and run:
```
docker build -t healthcheckup .
docker run -v $(pwd)/config.yml:/app/config.yml healthcheckup --config /app/config.yml
```

## Logging & Alerts
- Logs to stdout by default
- Configure alert hooks (webhook, email) in config
- Retry and backoff settings are configurable per check

## Testing
- Unit tests: `npm test` / `pytest` / `go test ./...`
- Add integration tests for target services

## Contributing
- Fork, create branch, open PR
- Follow code style and include tests for new features

## License
Specify a license (e.g. MIT) in LICENSE file.

For questions or issues, open an issue in the repository.