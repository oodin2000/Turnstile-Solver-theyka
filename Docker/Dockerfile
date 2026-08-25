FROM python:3.10-slim

RUN apt-get update && apt-get install -y \
    wget \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

# Install Chromium via apt (lebih ringan dari Chrome)
RUN apt-get update && apt-get install -y chromium && rm -rf /var/lib/apt/lists/*

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

ENV CHROME_PATH=/usr/bin/chromium
ENV PYTHONUNBUFFERED=1

CMD ["python", "api_solver.py", "--host", "0.0.0.0", "--port", "8080", "--headless", "True", "--thread", "1", "--browser_type", "chromium", "--useragent", "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"]
