# TSDB Simulation with QuestDB

This repository contains a Python-based simulation of MT5 positions (buy/sell) for multiple symbols (EURUSD, GBPUSD, XAUUSD) that are sent to QuestDB using **line protocol** with **multipart/form-data**.

The simulation supports **multi-threading** to simulate multiple symbols concurrently.

---

## Demo

![Peeraphat361](Peeraphat361.png)

---

## Features

- Multi-threaded simulation of MT5 positions
- Supports multiple currency/gold symbols
- Sends positions to QuestDB in real-time
- Uses `multipart/form-data` for HTTP ingestion (required by QuestDB)

---

## Requirements

- Python 3.9+
- `requests` library
- QuestDB running on `http://localhost:9000`

---

## Usage

1. Make sure QuestDB is running.
2. Create the table in QuestDB:

```sql
CREATE TABLE positions (
    symbol SYMBOL CAPACITY 256 CACHE,
    ticket LONG,
    type STRING,
    volume DOUBLE,
    price_open DOUBLE,
    price_current DOUBLE,
    profit DOUBLE,
    time TIMESTAMP
) TIMESTAMP(time) PARTITION BY NONE;
