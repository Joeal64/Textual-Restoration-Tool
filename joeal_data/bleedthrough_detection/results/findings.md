## Observed results on this exploratory set
- **tone:** TP 9, FN 0, FP 3, TN 0.
  - significant: 6/6 flagged.
  - subtle: 3/3 flagged.
  - none: 3/3 flagged.
- **components:** TP 9, FN 0, FP 1, TN 2.
  - significant: 6/6 flagged.
  - subtle: 3/3 flagged.
  - none: 1/3 flagged.
- **edges:** TP 9, FN 0, FP 2, TN 1.
  - significant: 6/6 flagged.
  - subtle: 3/3 flagged.
  - none: 2/3 flagged.
- **Missed bleed-through (C):** none in this set
- **False alarms (C):** photo_15_92, scanned_page
- **Detector C routed:** mean F 90.74, pF 94.66, DRD 2.566 on nine DIBCO pages.
- **Our method, always:** mean F 90.74, pF 94.66, DRD 2.566 on nine DIBCO pages.
- **Plain Otsu:** mean F 88.47, pF 92.24, DRD 3.895 on nine DIBCO pages.
- Synthetic none: C flags 0/3; mean restoration F 99.49.
- Synthetic subtle: C flags 2/3; mean restoration F 99.64.
- Synthetic significant: C flags 3/3; mean restoration F 99.71.
- No-bleed stress controls: C falsely flags 1/12.

**Integration decision:** keep this notebook experimental. We need independently reviewed severity labels, clean historical handwriting negatives, mixed-degradation pages, source-group-separated calibration/test sets, and a threshold fixed before the final test. The printed negatives and repeated source pages prevent a general accuracy claim.

**Separation verified:** all 33 real/controlled inputs complete detection with the restoration functions replaced by raising stubs. Spy checks confirm exactly one restoration call per positive real-page decision and none for negative decisions. Negative-route pixels and source arrays remain unchanged. Forced decisions verify the order is detection, then (positive only) restoration.

**Interpretation:** the detector now derives its own dark-ink reference directly from three-class Otsu on a broad illumination-corrected analysis copy. It never consumes our restored foreground mask. Faint foreground, antialiasing, textured paper and shadows remain possible false-positive causes; the overlays and stress controls expose these. Synthetic severity does not establish real-world accuracy.

**Architecture next step:** estimate foreground support and exclusion distance relative to stroke width and test local foreground/ghost contrast. Retain all three independent evidence outputs for comparison; add Sam’s stain mask as a separately tested feature/exclusion, not a stain-first mutually exclusive route. Keep an uncertain outcome for faint foreground versus ghost writing. Preserve the existing restoration method while testing detector revisions.

The fixed 31/21 restoration kernels and the detector’s analysis resizing can affect scale sensitivity. All native-resolution restoration outputs were scored; detection at other scan resolutions still needs separate validation.