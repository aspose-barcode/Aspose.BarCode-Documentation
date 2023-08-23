---
title: QualitySettings
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 250
url: /python-net/api-reference/aspose.barcode.barcoderecognition/qualitysettings/
---

## QualitySettings class

QualitySettings allows to configure recognition quality and speed manually.<br/>            You can quickly set up QualitySettings by embedded presets: HighPerformance, NormalQuality, <br/>            HighQuality, MaxBarCodes or you can manually configure separate options.<br/>            Default value of QualitySettings is NormalQuality.

The QualitySettings type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|high_performance|HighPerformance recognition quality preset. High quality barcodes are recognized well in this mode.|
|normal_quality|NormalQuality recognition quality preset. Suitable for the most of barcodes|
|high_quality_detection|HighQualityDetection recognition quality preset. Same as NormalQuality but with high quality [detector_settings](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/qualitysettings/)|
|max_quality_detection|MaxQualityDetection recognition quality preset. Same as NormalQuality but with highest quality [detector_settings](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/qualitysettings/).<br/>            Allows to detect diagonal and damaged barcodes.|
|high_quality|HighQuality recognition quality preset. This preset is developed for low quality barcodes.<br/>            Allows to detect diagonal and highly damaged barcodes.|
|max_bar_codes|MaxBarCodes recognition quality preset. This preset is developed to recognize all possible barcodes, even incorrect barcodes.|
|allow_invert_image|Allows engine to recognize inverse color image as additional scan. Mode can be used when barcode is white on black background.|
|allow_incorrect_barcodes|Allows engine to recognize barcodes which has incorrect checksumm or incorrect values. <br/>            Mode can be used to recognize damaged barcodes with incorrect text.|
|read_tiny_barcodes|Allows engine to recognize tiny barcodes on large images. Ignored if [allow_incorrect_barcodes](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/qualitysettings/) is set to True. Default value: False.|
|check_more_1d_variants|Allows engine to recognize 1D barcodes with checksum by checking more recognition variants. Default value: False.|
|allow_complex_background|Allows engine to recognize color barcodes on color background as additional scan. Extremely slow mode.|
|allow_median_smoothing|Allows engine to enable median smoothing as additional scan. Mode helps to recognize noised barcodes.|
|median_smoothing_window_size|Window size for median smoothing. Typical values are 3 or 4. Default value is 3. AllowMedianSmoothing must be set.|
|allow_regular_image|Allows engine to recognize regular image without any restorations as main scan. Mode to recognize image as is.|
|allow_decreased_image|Allows engine to recognize decreased image as additional scan. Size for decreasing is selected by internal engine algorithms.<br/>            Mode helps to recognize barcodes which are noised and blurred but captured with high resolution.|
|allow_white_spots_removing|Allows engine to recognize image without small white spots as additional scan. Mode helps to recognize noised image as well as median smoothing filtering.|
|allow_one_d_additional_scan|Allows engine for 1D barcodes to recognize regular image with different params as additional scan. Mode helps to recongize low height 1D barcodes.|
|use_old_barcode_detector|Switches to the old barcode detector.|
|allow_one_d_fast_barcodes_detector|Allows engine for 1D barcodes to quickly recognize high quality barcodes which fill almost whole image. <br/>            Mode helps to quickly recognize generated barcodes from Internet.|
|fast_scan_only|Allows engine for 1D barcodes to quickly recognize middle slice of an image and return result without using any time-consuming algorithms.|
|allow_micro_white_spots_removing|Allows engine for Postal barcodes to recognize slightly noised images. Mode helps to recognize sligtly damaged Postal barcodes.|
|allow_salt_and_paper_filtering|Allows engine to recognize barcodes with salt and paper noise type. Mode can remove small noise with white and black dots.|
|allow_detect_scan_gap|Allows engine to use gap between scans to increase recognition speed. Mode can make recognition problems with low height barcodes.|
|allow_datamatrix_industrial_barcodes|Allows engine for Datamatrix to recognize dashed industrial Datamatrix barcodes. <br/>            Slow mode which helps only for dashed barcodes which consist from spots.|
|allow_qr_micro_qr_restoration|Allows engine for QR/MicroQR to recognize damaged MicroQR barcodes.|
|allow_one_d_wiped_bars_restoration|Allows engine for 1D barcodes to recognize barcodes with single wiped/glued bars in pattern.|
|allow_additional_restorations|Allows engine using additional image restorations to recognize corrupted barcodes. At this time, it is used only in MicroPdf417 barcode type.|
|detector_settings|Barcode detector settings.|

### See Also

* namespace [aspose.barcode.barcoderecognition](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

