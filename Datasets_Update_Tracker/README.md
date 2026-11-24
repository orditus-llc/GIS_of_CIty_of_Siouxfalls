# Datasets Update Tracker

Shows what the City of Sioux Falls has changed in its **Building Footprints** layer since you last looked.

Data source: [City of Sioux Falls, Building Footprints](https://www.arcgis.com/home/item.html?id=3ca4a96b2f5847fdbac6568c6dc20ee3&sublayer=5&dataTabView=table)
(served from `https://gis.siouxfalls.gov/arcgis/rest/services/Data/Property/MapServer/5`).

## Why this exists

The City doesn't publish when this layer was last edited: the layer has no last-edited date
or edit-tracking fields, and the "April 2025" date on DataWorks / ArcGIS Online is when the item's
description was changed, not the data. So the tracker compares the data itself.

## What it shows

- **Added** buildings (new OBJECTIDs)
- **Removed** buildings
- **Edited** buildings: which variable changed, with its old and new value
  (footprint area and perimeter changes mean the outline was redrawn)

Changes stay listed until you click **Mark as seen**. **Download CSV** exports all of them.

## How to use

1. Open this folder in VS Code and click **Go Live** (Live Server extension).
2. Open `footprint_updates.html`.

The first visit saves the current state of all ~100,000 buildings as your starting point.
Later visits list everything that changed since then.

## How it works

On each visit the page downloads the attributes of every building from the City's server
(about 3 seconds, no geometry) and compares them field by field with the copy saved at your
last "Mark as seen". That copy lives in your browser (IndexedDB), so each person and browser
has its own starting point.
