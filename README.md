# Spec Scripts API Schema

JSON Schema (in YAML format) defining the structure of Kaptain script API specifications.

## Purpose

This schema defines what a valid scripts API spec looks like. It will be used to validate:

- `spec-build-scripts-api` - Build scripts API
- `spec-deploy-scripts-api` - Deploy scripts API
- `spec-local-scripts-api` - Local scripts API
- Any other script bundle project API specs

## Files

- `spec-scripts-api-schema.yaml` - The JSON Schema definition

## Usage

Validate a spec against this schema:

```bash
# Using yq to convert to JSON, then jsonschema to validate
yq -o json spec-my-api.yaml | jsonschema ../spec-scripts-api-schema/spec-scripts-api-schema.yaml
```

## Schema Structure

The schema defines:

- **Metadata**: version, name, description
- **Tool Requirements**: ordered list of required tools with version constraints
- **Entrypoints**: public API surface (scripts called by consumers)
- **Internals**: supporting scripts (called by entrypoints)
- **Deprecations**: migration tracking

See the schema file for full field definitions.

## Versioning

Schema version uses major.minor format and is embedded in the schema at build time.

The version of a release of this spec can be found in the following fields:

- `$id`
- `version`
- `tagged`
- `release`
