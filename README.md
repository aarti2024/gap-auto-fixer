# Gap Auto Fixer — ArcGIS Python Toolbox

An ArcGIS Pro Python Toolbox (`.pyt`) that automatically detects and fixes small
gaps between polygon boundaries within a specified tolerance.

## Features

- Detects gaps between an input boundary layer and a gap layer
- Estimates gap width using an area-to-perimeter ratio (`2 × area / perimeter`)
- Merges gaps within tolerance into the nearest neighboring polygon
- Validates coordinate reference systems before processing
- Leaves the original boundary layer unmodified — writes to a new output feature class
- Detailed progress messages and a fixed/skipped/failed summary on completion
- Adds the output automatically to the current map (if run inside ArcGIS Pro)

## Tool Interface

![Gap Auto Fixer tool pane](images/tool_ui.jpeg)

## Requirements

- ArcGIS Pro (Standard license or higher)
- `arcpy`

## Usage

1. Add `GapAutoFixer.pyt` to your ArcGIS Pro project (Catalog pane → right-click → Add Toolbox).
2. Open the **Gap Auto Fixer** tool.
3. Provide:
   - **Input Boundary** — polygon feature layer
   - **Gap Layer** — polygon feature layer representing candidate gaps
   - **Maximum Gap Width** — linear unit tolerance (e.g. `2 Meters`)
   - **Output Boundary** — output feature class path
4. Run the tool. Gaps within tolerance are merged into the nearest boundary polygon;
   gaps exceeding tolerance are skipped and reported.

## Notes

- Boundary and Gap layers must share the same coordinate system.
- Run topology validation on the output after processing.

## License

MIT
