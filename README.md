# setup-postgres

The missing action for Postgres :tada:

- Faster (with the default version) and simpler than containers
- Works on Linux, Mac, and Windows
- Supports different versions

[![Build Status](https://github.com/ankane/setup-postgres/actions/workflows/build.yml/badge.svg)](https://github.com/ankane/setup-postgres/actions)

## Getting Started

Add it as a step to your workflow

```yml
      - uses: ankane/setup-postgres@v1
```

## Versions

Specify a version

```yml
      - uses: ankane/setup-postgres@v1
        with:
          postgres-version: 17
```

Currently supports

Version | `17` | `16` | `15` | `14` | `13` | `12`
--- | --- | --- | --- | --- | --- | ---
Ubuntu 24.04 | ✓ | default | ✓ | ✓ | ✓ | ✓
Ubuntu (rest) | ✓ | ✓ | ✓ | default | ✓ | ✓
Mac | ✓ | ✓ | ✓ | default | ✓ | ✓
Windows 2025 | default | | | | | |
Windows (rest) | | | | default | | |

Test against multiple versions

```yml
    strategy:
      matrix:
        postgres-version: [17, 16, 15, 14, 13]
    steps:
      - uses: ankane/setup-postgres@v1
        with:
          postgres-version: ${{ matrix.postgres-version }}
```

## Options

Create a database

```yml
      - uses: ankane/setup-postgres@v1
        with:
          database: testdb
```

Set `postgresql.conf` config

```yml
      - uses: ankane/setup-postgres@v1
        with:
          config: |
            shared_preload_libraries = 'pg_stat_statements'
```

Install development files (for building extensions)

```yml
      - uses: ankane/setup-postgres@v1
        with:
          dev-files: true
```

## Extra Steps

Run queries

```yml
      - run: psql -d testdb -c 'SHOW server_version'
```

## Related Actions

- [setup-mysql](https://github.com/ankane/setup-mysql)
- [setup-mariadb](https://github.com/ankane/setup-mariadb)
- [setup-mongodb](https://github.com/ankane/setup-mongodb)
- [setup-elasticsearch](https://github.com/ankane/setup-elasticsearch)
- [setup-opensearch](https://github.com/ankane/setup-opensearch)
- [setup-sqlserver](https://github.com/ankane/setup-sqlserver)

## Contributing

Everyone is encouraged to help improve this project. Here are a few ways you can help:

- [Report bugs](https://github.com/ankane/setup-postgres/issues)
- Fix bugs and [submit pull requests](https://github.com/ankane/setup-postgres/pulls)
- Write, clarify, or fix documentation
- Suggest or add new features
