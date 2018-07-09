# Airbrakex Logger Backend version 0.1.5

This is a project to test the Airbrakex logger backend.   
Version 0.1.5 has an issue when the backend is used with the console backend

## Reproduce issue


```
mix deps.get
iex -S mix
```

Execute in the iex console

```elixir
require Logger
Logger.info("test")
```

It generates the output

```

12:17:05.642 [info]  test
:ok
12:17:05.652 [error] GenEvent handler Airbrakex.LoggerBackend installed in Logger terminating
** (stop) {:noreply, %{level: :error, metadata: []}}
Last message: {:io_reply, #Reference<0.1304738109.3821010949.84041>, :ok}
State: %{level: :error, metadata: []}

12:17:05.653 [error] :gen_event handler Airbrakex.LoggerBackend installed at Logger
** (exit) {:noreply, %{level: :error, metadata: []}}

12:17:05.654 [error] GenServer #PID<0.181.0> terminating
** (stop) {:noreply, %{level: :error, metadata: []}}
Last message: {:gen_event_EXIT, Airbrakex.LoggerBackend, {:noreply, %{level: :error, metadata: []}}}
State: {Logger, Airbrakex.LoggerBackend}

```
