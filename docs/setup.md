# Environment Setup

## Database Environment

### Objective

Set up a local PostgreSQL environment on macOS.
This project uses PostgreSQL as the main analysis layer.
Power BI connects to this database for dashboard and reporting output.

### Stack

- PostgreSQL 16 running in Docker
- Dataset: Contoso 1M orders, sourced from SQLBI Generator V2
- Query interface: VS Code with PostgreSQL extension

### Key Design Decisions

#### Use Docker over local installation

Docker simplifies the initial setup, avoiding the complexities of manual system-level installation and configuration. The docker-compose.yml in this repo is sufficient to reproduce 
the environment. Dataset is a pre generated CSV export from 
SQLBI Generator V2, available for download from the SQLBI Github.

#### Separate port (5433) for this project

The default PostgreSQL port (5432) was already used by a
previous container. Mapping to port 5433 avoids
conflict while keeping the setup explicit and documented.

#### Use Docker volume for data persistence

Database files are stored using Docker volume rather
than inside the container. This means data survives
container restarts and is not lost on docker compose down.


#### Dataset size: 1M orders

The SQLBI Generator supports multiple sizes. 1M orders was
selected as the right balance between analytical depth and development performance.

### Verified Output

| Table    | Row Count |
|----------|-----------|
| sales    | 2,348,911 |
| customer | 104,990   |
| date     | 4,018     |
| product  | 2,517     |
| store    | 74        |

Sales data covers **May 2016 – December 2025** (116 months).

---

## Reporting Environment

*To be documented after Power BI setup on Windows via VMware Fusion.*