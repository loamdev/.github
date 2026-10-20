# Loam

**Realistic test data, without the seed script.**

Loam reads your Postgres schema and fills it with data that is correct against it — every foreign key
pointing at a row that actually exists, loaded with `COPY` rather than row-by-row `INSERT`.

Point it at a database:

```sh
loam seed --db-url postgres://user:pass@localhost:5432/mydb --rows 500
```

Or at the `docker-compose.yml` you already have, and get the whole stack:

```sh
loam up      # containers, schema, data — about 15 seconds
loam down    # nothing left behind
```

No cluster. No cloud account. No production data. Nothing leaves your machine.

### Why it does not rot

Most test data lives in a seed script, and a seed script is a second copy of your schema. It drifts
the moment someone writes a migration, and then somebody loses an afternoon to it.

Loam reads the live schema at runtime. There is nothing written down, so there is nothing to go
stale.

---

### Repositories

| | |
| --- | --- |
| [**loam**](https://github.com/Loamdev/Loam) | The CLI and the seeding engine. Apache 2.0 |

### Contributing

Start with [`LATER.md`](https://github.com/Loamdev/Loam/blob/main/LATER.md) — the *Help wanted*
section is the list of real gaps, and several are small. Adding support for a new column type is four
files and about fifteen lines; the recipe is in
[`docs/CONTRIBUTING.md`](https://github.com/Loamdev/Loam/blob/main/docs/CONTRIBUTING.md).

That file also draws the line on what belongs in the open repo, so nobody spends a weekend on
something that would then be declined.
