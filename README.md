# ius_crypto_negotiatione_bot

A cryptocurrency trading bot in Elixir/OTP, built while working through
*Create a cryptocurrency trading bot in Elixir* by Kamil Skowron.

| app | role |
|-----|------|
| `streamer` | connects to the Binance WebSocket API and decodes trade events, one supervised streamer per symbol |
| `naive` | a naive trading strategy: a `Leader` per symbol runs `Trader` processes that buy and sell on fixed margins |
| `binance_mock` | a stand-in for the Binance REST API, so the bot can trade without real money |
| `data_warehouse` | subscribes to trade events and orders and stores them in PostgreSQL |
| `core` | shared structs and service supervision |

```sh
docker-compose up -d     # PostgreSQL
mix deps.get
iex -S mix
```

Binance API keys go into `config/secrets.exs`, which is git-ignored and loaded only
if present.
