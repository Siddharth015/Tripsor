# Google Maps Style - Dark Mode

## Table of Contents 🗺️

1.  **Overview** 
2.  **Style Definitions**

## 1. Overview

This style definition provides a dark mode theme for Google Maps. The style focuses on a minimalist and dark color scheme, emphasizing roads and bodies of water, while de-emphasizing labels and icons.

## 2. Style Definitions

The style definition uses a series of rules to adjust the visual appearance of different map features. Each rule targets a specific `featureType` (e.g., `road`, `water`, `poi`) and an `elementType` (e.g., `geometry`, `labels`, `labels.text`) to apply specific `stylers`.

| Feature Type          | Element Type        | Stylers                                                               | Description                                                                                                         |
| --------------------- | --------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `all`                 | `all`                 | `visibility: on`                                                           | Enables all map features.                                                                                        |
| `all`                 | `labels`              | `visibility: off`, `saturation: -100`                                  | Disables all labels and sets their saturation to -100.                                                       |
| `all`                 | `labels.text.fill`   | `saturation: 36`, `color: #000000`, `lightness: 40`, `visibility: off` | Sets the fill color and lightness of label text, then disables it.                                            |
| `all`                 | `labels.text.stroke` | `visibility: off`, `color: #000000`, `lightness: 16`                     | Sets the stroke color and lightness of label text, then disables it.                                            |
| `all`                 | `labels.icon`        | `visibility: off`                                                           | Disables all label icons.                                                                                      |
| `administrative`     | `geometry.fill`      | `color: #000000`, `lightness: 20`                                        | Sets the fill color and lightness of administrative features (e.g., countries, states).                       |
| `administrative`     | `geometry.stroke`     | `color: #000000`, `lightness: 17`, `weight: 1.2`                          | Sets the stroke color, lightness, and weight of administrative features.                                       |
| `landscape`           | `geometry`            | `color: #000000`, `lightness: 20`                                        | Sets the color and lightness of landscape features.                                                            |
| `landscape`           | `geometry.fill`       | `color: #4d6059`                                                           | Sets the fill color of landscape features.                                                                  |
| `landscape`           | `geometry.stroke`      | `color: #4d6059`                                                           | Sets the stroke color of landscape features.                                                                  |
| `landscape.natural`  | `geometry.fill`       | `color: #4d6059`                                                           | Sets the fill color of natural landscape features (e.g., forests, parks).                                    |
| `poi`                 | `geometry`            | `lightness: 21`                                                          | Adjusts the lightness of points of interest.                                                                     |
| `poi`                 | `geometry.fill`       | `color: #4d6059`                                                           | Sets the fill color of points of interest.                                                                  |
| `poi`                 | `geometry.stroke`      | `color: #4d6059`                                                           | Sets the stroke color of points of interest.                                                                  |
| `road`                | `geometry`            | `visibility: on`, `color: #7f8d89`                                      | Enables roads and sets their color.                                                                          |
| `road`                | `geometry.fill`       | `color: #7f8d89`                                                           | Sets the fill color of roads.                                                                                 |
| `road.highway`        | `geometry.fill`       | `color: #7f8d89`, `lightness: 17`                                        | Sets the fill color and lightness of highways.                                                                |
| `road.highway`        | `geometry.stroke`     | `color: #7f8d89`, `lightness: 29`, `weight: 0.2`                          | Sets the stroke color, lightness, and weight of highways.                                                       |
| `road.arterial`       | `geometry`            | `color: #000000`, `lightness: 18`                                        | Sets the color and lightness of arterial roads.                                                               |
| `road.arterial`       | `geometry.fill`       | `color: #7f8d89`                                                           | Sets the fill color of arterial roads.                                                                      |
| `road.arterial`       | `geometry.stroke`      | `color: #7f8d89`                                                           | Sets the stroke color of arterial roads.                                                                      |
| `road.local`          | `geometry`            | `color: #000000`, `lightness: 16`                                        | Sets the color and lightness of local roads.                                                                |
| `road.local`          | `geometry.fill`       | `color: #7f8d89`                                                           | Sets the fill color of local roads.                                                                         |
| `road.local`          | `geometry.stroke`      | `color: #7f8d89`                                                           | Sets the stroke color of local roads.                                                                         |
| `transit`              | `geometry`            | `color: #000000`, `lightness: 19`                                        | Sets the color and lightness of transit features.                                                             |
| `water`               | `all`                 | `color: #2b3638`, `visibility: on`                                       | Sets the color of water features and enables their visibility.                                                  |
| `water`               | `geometry`            | `color: #2b3638`, `lightness: 17`                                        | Sets the color and lightness of water features.                                                             |
| `water`               | `geometry.fill`       | `color: #24282b`                                                           | Sets the fill color of water features.                                                                      |
| `water`               | `geometry.stroke`      | `color: #24282b`                                                           | Sets the stroke color of water features.                                                                      |
| `water`               | `labels`              | `visibility: off`                                                           | Disables all water labels.                                                                                     |
| `water`               | `labels.text`         | `visibility: off`                                                           | Disables all water label text.                                                                                 |
| `water`               | `labels.text.fill`   | `visibility: off`                                                           | Disables the fill of water label text.                                                                        |
| `water`               | `labels.text.stroke` | `visibility: off`                                                           | Disables the stroke of water label text.                                                                        |
| `water`               | `labels.icon`        | `visibility: off`                                                           | Disables all water label icons.                                                                               |

This dark mode style for Google Maps can enhance map readability in low-light environments or for users who prefer a darker visual theme. 
