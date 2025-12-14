---
title: Troubleshooting
description: "How to debug recognition problems such as no results or false positives."
type: docs
weight: 50
url: /java/developer-guide/barcode-recognition/troubleshooting
---

# Troubleshooting

This section helps you debug recognition issues in a systematic way.
Start by reducing variables, then add complexity only when needed.

## A short checklist

1. Verify the input image is readable by humans and has enough resolution and contrast.
2. Restrict symbologies to the expected types instead of `ALL_SUPPORTED_TYPES`.
3. Use ROI when the barcode location is known.
4. Try a more robust preset (`HighQuality` or `MaxQuality`) on the same image.
5. Validate results using checksum rules and confidence thresholds.


