---
title: How to Get BarCode Module Instance
type: docs
weight: 90
feedback: BARCODECOM
url: /javascript-cpp/get-barcode-module-instance/
---
# Using the Global Module Instance with Aspose.BarCode.JS.Cpp.js

When working with the `Aspose.BarCode.JS.Cpp.js` library, it is essential to obtain a global module instance to access its features throughout your application. This guide explains how to load, initialize, and store the BarCode module as a global instance.

## Prerequisites

Before initializing the BarCode module, ensure the `Aspose.BarCode.JS.Cpp.js` script is included in your HTML file. This step is required for the library to function properly.


```html
<script type="text/javascript" src="Aspose.BarCode.JS.Cpp.js" async onload="initializeModule()"></script>
<script>
// Global BarCode module instance
var BarCodeInstance;

// Async function for module initialization
async function initializeModule() {
    try {
        // Load the BarCode module and store it in BarCodeInstance
        BarCodeInstance = await BarCode();
        console.log('BarCode module has loaded');
        
        // Additional code to enable barcode-related controls can be placed here
    } catch (error) {
        // Handle any errors that may occur during initialization
        console.error("BarCode module initialization error:", error);
    }
}
</script>
```