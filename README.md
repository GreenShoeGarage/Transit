# TRANSIT

Field Instrument No. 032. A pocket surveyor's transit that runs entirely in the
browser from a single HTML file. Sight a line, work the coordinate geometry, and
recover true north, then keep every point in a field book you can export.

Part of the Field Instruments series at mbparks.com.

## What it does

TRANSIT has four faces, presented as tabs. The architecture is a small module
registry, so each face is self contained and new ones can be added without
touching the rest.

### Sight

Turns the device into a rough theodolite. The rear camera becomes a viewfinder
with a brass reticle, the magnetometer reports azimuth (corrected to true north
by the stored declination), and device tilt reports the vertical angle. GPS
supplies position. Recording a shot drops a point into the field book.

This is recon grade, not survey grade. Phone magnetometers wander a degree or
two on a clean day and far more near rebar, vehicles, and fence wire. Use it for
orientation, reconnaissance, and teaching, not for boundary work.

### COGO

Coordinate geometry on a local north and east plane.

- Inverse: two points into an azimuth, a quadrant bearing, and a distance.
- Forward: a new point from a starting point, an azimuth, and a distance.
- Closed traverse: enter legs as "azimuth, distance" and get the misclosure in
  north and east, the linear misclosure, the precision ratio as 1:X, the
  perimeter, the area by coordinates, and the Bowditch (compass rule) adjusted
  coordinates. Adjusted points can be sent straight to the field book.

### North

- Solar azimuth: the sun is a free true north reference. Enter or pull a
  position from GPS and TRANSIT computes the sun's azimuth and altitude for the
  current moment using a low precision solar model good to roughly an arcminute.
- Declination from the sun: sight the sun, read the magnetic azimuth off your
  compass, and TRANSIT derives your local magnetic declination, stores it, and
  applies it on the Sight panel.
- Angle bench: convert among decimal degrees, DD-MM-SS, quadrant bearing, and
  azimuth, with back azimuth and magnetic to true reconciliation.

### Book

The field book. Every point captured by Sight or computed by COGO collects here,
and you can add points by hand. Export as PNEZD CSV (point, northing, easting,
elevation, description), the format every survey package reads, or as a separate
latitude and longitude CSV for the GPS captures.

## Conventions

- Single file, no build step, no server dependencies.
- Works offline once loaded. Camera, sensors, and GPS use device APIs only.
- Light and dark themes. Dark is the default. The choice is remembered when the
  browser allows storage and degrades quietly when it does not.
- No em dashes anywhere in the prose or the code.

## Accuracy and limits

- Sensor sighting is for reconnaissance and teaching. It will not replace a
  total station.
- The solar model is low precision, suitable for field orientation rather than
  astronomic survey control.
- COGO works on a local plane. State plane projection, scale factor, and grid to
  ground reduction are planned for a future GRID module.
- Orthometric (real) heights need a geoid model, which is a large data file that
  conflicts with the single file rule, so heights here are whatever the device
  or your entries provide.

## Roadmap

The script ends with a clearly marked seam for future modules. Each is a single
TRANSIT.register block and appears as a tab with no other wiring.

- CURVES: horizontal and vertical curve layout with stakeout tables.
- LEVEL: differential leveling reduction and trig leveling.
- GRID: state plane Maryland, scale factor, and grid to ground.

## License

GPL-3.0

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version. This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY, without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more
details.
