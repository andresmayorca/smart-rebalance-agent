# Smart Portfolio Rebalance API

A Flask API to calculate realistic portfolio allocations based on historical asset data.

## Prerequisites

- Python 3.11 or higher
- A virtual environment tool like `venv` or `uv`
- Installing uv: Use curl to download the script and execute it with sh:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```
## Installation

1. Clone the repository:
```bash
git clone <repo-url>
cd <repo-folder>
```

2. Create and activate a virtual environment with UV:
```bash
uv venv
```

3. Install the required dependencies:
```bash
uv pip install -r requirements.txt
```

## Environment Cleanup

If you need to reset your local dependencies and start fresh, remove the virtual environment:

```bash
rm -rf .venv
```

Then follow the installation steps again.

## Running the Development Server

To run the API locally with auto-reload enabled:

```bash
uv run gunicorn app.main:app
```

## Endpoints

### Health Check

**GET** `/`

Returns API status.

### Rebalance Portfolio

**POST** `/rebalance`

Calculates portfolio weights and allocation.

#### Request Body Example

```json
{
  "assets": ["ADA/USD", "ETH/USD", "SOL/USD", "STRK/USD"],
  "rebalance_period": "1H",
  "min_weight": 0.05,
  "max_weight": 0.35
}
```

#### Response Example

```json
{
  "success": true,
  "weights": [0.25, 0.25, 0.25, 0.25],
  "allocation": {
    "ETH": "25.00%",
    "ADA": "25.00%",
    "SOL": "25.00%",
    "STRK": "25.00%"
  }
}
```
