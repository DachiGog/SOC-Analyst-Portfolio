# 📜 Zeek Field & Type Cheatsheet

A handy reference to commonly used **Zeek fields**, **types**, and **log structures**. Perfect for analysts, defenders, and Zeek scripters.

---

## 🧱 Zeek Log Structure Basics

Each Zeek log (e.g., `conn.log`, `http.log`) has:

- A **log stream name** (e.g., `Conn::LOG`)
- A **record type** (e.g., `Conn::Info`)
- Multiple **fields** with specific **data types**

---

## 🧩 Common Zeek Types

| Type            | Description                                           | Example                      |
|------------------|-------------------------------------------------------|------------------------------|
| `addr`           | IP address                                            | `192.168.1.10`               |
| `port`           | Port number with protocol                            | `80/tcp`, `53/udp`           |
| `time`           | Timestamp in seconds since epoch                     | `1681849281.23456`           |
| `interval`       | Time duration (float seconds)                        | `2.345`                      |
| `string`         | UTF-8 string                                          | `"GET /index.html"`          |
| `count`          | Unsigned integer                                     | `42`                         |
| `int`            | Signed integer                                       | `-5`, `100`                  |
| `bool`           | Boolean (true/false)                                 | `T`, `F`                     |
| `table`          | Key-value lookup table                               | `table[addr] of count`       |
| `set`            | Unordered unique elements                            | `set[string]`                |
| `vector`         | Ordered list (indexable)                             | `vector[string]`             |
| `record`         | Struct with named fields                             | `record { src: addr; port: port; }` |

---

## 📑 `conn.log` Fields (Connection Log)

| Field               | Type       | Description                          |
|---------------------|------------|--------------------------------------|
| `ts`                | `time`     | Timestamp of connection start        |
| `uid`               | `string`   | Unique connection ID                 |
| `id.orig_h`         | `addr`     | Originating host IP                  |
| `id.orig_p`         | `port`     | Originating port                     |
| `id.resp_h`         | `addr`     | Responding host IP                   |
| `id.resp_p`         | `port`     | Responding port                      |
| `proto`             | `enum`     | Protocol (`tcp`, `udp`, etc.)        |
| `service`           | `string`   | Detected service (e.g. `http`)       |
| `duration`          | `interval` | Connection duration                  |
| `orig_bytes`        | `count`    | Bytes sent by originator             |
| `resp_bytes`        | `count`    | Bytes sent by responder              |
| `conn_state`        | `string`   | Connection state (e.g. `S0`, `SF`)   |
| `missed_bytes`      | `count`    | Unparsed bytes due to packet loss    |
| `history`           | `string`   | Packet flags summary                 |

---

## 🌐 `http.log` Fields (HTTP Log)

| Field               | Type       | Description                              |
|---------------------|------------|------------------------------------------|
| `ts`                | `time`     | Timestamp of request                     |
| `uid`               | `string`   | Connection UID (join with `conn.log`)    |
| `id.orig_h/p`       | `addr/port`| Origin host/port                         |
| `id.resp_h/p`       | `addr/port`| Response host/port                       |
| `trans_depth`       | `count`    | Pipeline depth of request                |
| `method`            | `string`   | HTTP method (`GET`, `POST`, etc.)        |
| `host`              | `string`   | HTTP Host header                         |
| `uri`               | `string`   | Requested URI                            |
| `referrer`          | `string`   | HTTP Referer                             |
| `user_agent`        | `string`   | HTTP User-Agent                          |
| `status_code`       | `count`    | HTTP response code                       |
| `status_msg`        | `string`   | Response message                         |
| `info_code`         | `count`    | Info code (optional)                     |
| `tags`              | `set`      | Set of tags                              |

---

## ✉️ `dns.log` Fields (DNS Log)

| Field               | Type       | Description                           |
|---------------------|------------|---------------------------------------|
| `ts`                | `time`     | Timestamp of DNS query                |
| `uid`               | `string`   | Connection UID                        |
| `id.orig_h/p`       | `addr/port`| Origin host/port                      |
| `id.resp_h/p`       | `addr/port`| Response host/port                    |
| `proto`             | `enum`     | Protocol                              |
| `trans_id`          | `count`    | DNS transaction ID                    |
| `query`             | `string`   | DNS query                             |
| `qclass`            | `count`    | Query class                           |
| `qtype`             | `count`    | Query type (e.g., A = 1, AAAA = 28)   |
| `rcode`             | `count`    | Response code                         |
| `AA`, `TC`, `RD`, `RA`, `Z` | `bool` | DNS flags                       |
| `answers`           | `vector[string]` | Returned answers               |
| `TTLs`              | `vector[interval]` | TTLs for answers             |

---

## 📂 Useful Zeek Records

| Record Type        | Description                                |
|--------------------|--------------------------------------------|
| `Conn::Info`       | Connection log record                      |
| `HTTP::Info`       | HTTP log record                            |
| `DNS::Info`        | DNS log record                             |
| `SSL::Info`        | SSL/TLS log record                         |
| `Files::Info`      | File analysis record                       |
| `Notice::Info`     | Security notices and alerts                |

---

## 🛠️ Common Scripting Tips

- Access fields in event handlers using dot notation: `c$id$orig_h`
- Use `add`, `delete` for sets and tables
- Use `print` or `Log::write` to debug

---

> 💡 Want more field definitions? Check `zeek/scripts/base/protocols/*` or use the `zeek-cut` tool to explore logs easily!

---

