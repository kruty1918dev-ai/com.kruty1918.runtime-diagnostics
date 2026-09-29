# com.kruty1918.runtime-diagnostics

Reusable runtime diagnostics: health-check aggregation service, pluggable
health reporters, and global async/unhandled error logging.

## Install (Unity Package Manager)

Package Manager → **+** → **Add package from git URL**:

```
https://github.com/kruty1918dev-ai/com.kruty1918.runtime-diagnostics.git
```

or in `Packages/manifest.json`:

```json
"com.kruty1918.runtime-diagnostics": "https://github.com/kruty1918dev-ai/com.kruty1918.runtime-diagnostics.git#v0.1.0"
```

The repository is private — Git credentials (PAT / Git Credential Manager)
are required on every machine that resolves the package.

## API surface

| Type | Purpose |
|---|---|
| `IHealthCheckService` | Aggregates registered reporters into an overall health verdict |
| `IHealthReporter` | One probe per subsystem (network, services, content) |
| `HealthStatus` | Healthy / degraded / unhealthy verdict |

## Model

Reusable UPM package extracted from Moyva. No game-specific dependencies;
compose via your own installer/DI. Unobserved task exceptions and unhandled
errors are captured globally so "silent" async failures still reach the log.
