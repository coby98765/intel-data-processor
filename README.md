# Intel Data Processor

Process mission data and personnel records to generate concise intelligence reports.

> **Status:** Early prototype — simple, file-based processing with a small Python codebase.

## Features
- Ingest mission and personnel data (CSV or JSON)
- Validate and normalize fields (dates, statuses, clearances)
- Analyze assignments/availability with basic risk flags
- Generate a human‑readable report (Markdown/console)

## Project Structure
```
intel-data-processor/
├─ main.py                 # Orchestrates the end-to-end flow
├─ mission_processor.py    # Parses & validates missions
├─ personnel_analyzer.py   # Analyzes personnel skills/availability
├─ report_generator.py     # Builds a readable intelligence report
└─ README.md
```

## Quickstart

### 1) Prerequisites
- Python 3.10+

If a `requirements.txt` exists, install with:
```bash
pip install -r requirements.txt
```

### 2) Clone
```bash
git clone https://github.com/coby98765/intel-data-processor.git
cd intel-data-processor
```

### 3) Run
```bash
python main.py
```
By default, the script expects paths to the mission and personnel data (via prompts, config, or CLI flags).

## Data Formats

Suggested minimal schemas (CSV). JSON equivalents should use the same field names.

### Missions
```csv
mission_id,date,location,objective,status
MSN-1001,2025-08-01,North Sector,Recon,planned
MSN-1002,2025-08-03,West Ridge,Resupply,completed
```

### Personnel
```csv
person_id,name,role,skills,clearance,availability
P-001,Ella Cohen,Intel Analyst,"SIGINT;OSINT",Secret,available
P-002,Ori Levi,Field Operative,"Recon;First Aid",Top Secret,on_mission
```

## Example Output (Markdown)
```markdown
# Intelligence Report — 2025-08-10

## Mission Summary
- MSN-1001 (Recon, North Sector) — planned for 2025-08-01
- MSN-1002 (Resupply, West Ridge) — completed on 2025-08-03

## Personnel Overview
- 1 available (Secret+), 1 engaged (Top Secret)

## Notes & Flags
- Recon mission pending; ensure at least one Recon-qualified operative is available 24h prior.
```

## How It Works
1. **Load** mission/personnel datasets
2. **Validate & normalize** fields (dates, statuses, clearances)
3. **Analyze** mission requirements vs. personnel availability/skills
4. **Generate** a Markdown/console report

## CLI (Optional)
If you add CLI flags via `argparse`, a typical run could look like:
```bash
python main.py --missions data/missions.csv --personnel data/personnel.csv --out report.md
```

## Testing
Place tests under `tests/` and run:
```bash
pytest -q
```

## Roadmap
- [ ] CLI flags (`argparse`) for file paths and output
- [ ] Export to HTML/PDF
- [ ] Basic scoring (risk/readiness)
- [ ] Simple rules engine for assignments
- [ ] Input schema validation (Pydantic)

## Collaborators
- @coby98765
- GabiThaler
- zalosh12

