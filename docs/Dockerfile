FROM ghcr.io/astral-sh/uv:python3.12-bookworm-slim

WORKDIR /docs

# 1. Force uv to create the venv outside the working directory
#    This prevents your volume mount from hiding the installed packages.
ENV UV_PROJECT_ENVIRONMENT="/opt/venv"

# 2. Add the venv binaries to the system PATH immediately
ENV PATH="/opt/venv/bin:$PATH"

# 3. Copy files (Fixing the path for uv.lock to match current dir)
COPY pyproject.toml uv.lock ./

COPY mkdocs.yml .

# 4. Install dependencies
#    --frozen ensures we stick exactly to uv.lock versions
RUN uv sync --frozen --group docs