# FHIR Patient Care Incubator IG

This repository contains the HL7 Patient Care incubator Implementation Guide (IG) for resources being advanced toward future FHIR core inclusion.

The project is currently XML-first (resource definitions and examples are authored in `input/resources`) and uses the IG Publisher toolchain to generate the site and validation output.

## Scope

The current incubator content includes:

- ClinicalAssessment
- ConditionDefinition
- Linkage

## Prerequisites

Install the following tools before building locally:

- Java (required by the FHIR IG Publisher)
- Internet access for terminology validation and publisher/script updates

## Repository Layout

- `input/resources/`: source conformance resources and examples (grouped by resource)
- `input/pagecontent/`: markdown/XML narrative pages used by the IG site
- `sushi-config.yaml`: IG metadata and publisher parameters
- `ig.ini`: IG entrypoint used by the publisher
- `output/`: generated IG website and generated artifacts
- `fsh-generated/`: generated IG artifacts (including `ImplementationGuide-*.json`)
- `_updatePublisher.*`: fetches the latest publisher and helper scripts
- `_genonce.*`: one-time local IG generation

## Quick Start

### Windows (PowerShell)

1. Update publisher and helper scripts:

```powershell
.\_updatePublisher.bat -f
```

2. Build the IG once:

```powershell
.\_genonce.bat
```

### macOS/Linux

1. Update publisher and helper scripts:

```bash
./_updatePublisher.sh --force
```

2. Build the IG once:

```bash
./_genonce.sh
```

### Build Output

After a successful run, open:

- `output/index.html` for the rendered IG
- `output/qa.html` for validation and QA messages

## Authoring Workflow

1. Edit resource source files under `input/resources/<resource-name>/`.
2. Update narrative content in `input/pagecontent/`:
	 - `index.md` for homepage content
	 - `changes.md` for change history notes
	 - `StructureDefinition-*-intro.xml` and `StructureDefinition-*-notes.xml` for resource pages
3. Run `_genonce` to regenerate output.
4. Review `output/qa.html` and `output/artifacts.html`.

## Important Notes About SUSHI/FSH

- This repo does not currently maintain profile/value set definitions in FSH.
- `input/fsh/readme.md` documents that FSH usage is limited to auto-generating the IG resource.
- Do not expect `.fsh` authoring files as the primary source for conformance content in this project.

## Contributing

1. Make source edits in `input/` (not `output/`).
2. Rebuild with `_genonce`.
3. Include updated generated artifacts as required by your workflow.
4. Open a pull request with a clear summary of content and QA impact.

## License

The IG metadata declares license `CC0-1.0`.
