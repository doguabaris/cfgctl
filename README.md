# CFGCTL-CLI

A minimal CLI tool to **pull, push, diff, and list configuration files** for projects and
distributed environments. Designed for managing configurations across a variety of domains where
settings need to be easily manageable, versioned, and traceable.

---

### Some stand-out features:

- Initialize CLI with a central API endpoint
- Pull latest project configuration
- Push local config files to the server
- Diff between config versions
- List available config versions
- Caches configuration files under `configs/`

---

### Installation

```bash
npm install -g cfgctl
```

---

### Filename format

All configuration files must follow this naming convention:

```
<project>@<version>.json
```

Example:

```
configs/atlas@1.0.0.json
```

---

### File structure

All configuration files are expected to follow this structure:

```json
{
	"version": "1.0.0",
	"config": {
		"key": "value",
		"...": "..."
	}
}
```

---

### Quick Start

#### 1. Initialize once:

```bash
npx cfgctl init --api http://localhost:3000
```

This saves your API endpoint to `configs/.cfgctlrc.json`.

#### 2. Pull latest config for a project:

```bash
npx cfgctl pull <project>
```

Example:

```bash
npx cfgctl pull atlas
```

#### 3. Push local config file:

```bash
npx cfgctl push configs/atlas@1.0.1.json
```

#### 4. Diff two config files:

```bash
npx cfgctl diff configs/atlas@1.0.0.json configs/atlas@1.0.1.json
```

#### 5. List versions (based on filenames):

```bash
npx cfgctl list
```

---

### Testing

Start the mock API:

```bash
node tests/mock-api.mjs
```

Then run CLI commands while targeting `http://localhost:3000`.

---

### Requirements

- Node.js ≥ 20.18.1
- TypeScript
- API endpoint that serves configs at `/configs/:project/latest` and accepts POSTs at
  `/configs/:project`

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## License

This package is licensed under the [MIT License](LICENSE).



