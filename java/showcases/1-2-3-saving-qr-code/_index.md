---
title: Save QR Codes
type: docs
ai_search_scope: "barcode_java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
url: /java/1-2-3-saving-qr-code/
---

## **How to Save QR Code**
To save the generated QR Code image, please refer to the following steps:

1. Select the Type
1. Input the QR Code content data
1. Customize QR Code Settings (Optional)
1. Click **Generate Preview** button
1. Click the desired image format link such as PNG, GIF, JPEG, TIFF to download under **Download As** section

You will see **File Download** dialog box on your browser to save the generated QR Code on your system.

## **Procedure**
### **API**
{{< highlight java >}}

 GET /qrcodegen/api/qrcode/generate?data=<URL>&foreColor=&bgColor=&ecc=&size=&format=[png|jpeg|gif|tiff|bmp]&download=true

Example:

http://localhost:8080/qrcodegen/api/qrcode/generate?data=http://aspose.com&foreColor=&bgColor=&ecc=&size=&format=png&download=true


{{< /highlight >}}

### **Java Script**
The ***addRequestSettings*** function is used to add customize QR Code settings to the API request parameters.

{{< highlight java >}}

  addRequestSettings : function(requestString){

 requestString = requestString + "&ecc=" + this.$('.errorCorrectionCode option:selected').text();

 requestString = requestString + "&foreColor=" + encodeURIComponent(this.$('.input-fcolor').val());

 requestString = requestString + "&bgColor=" + encodeURIComponent(this.$('.input-bgcolor').val());

 if(this.$('.input-size').val() != "100x100")

 requestString = requestString + "&size=" + this.$('.input-size').val();

 return requestString;

 }

{{< /highlight >}}

### **Java**  
**Core API Method - QRCodeManagementController.generateQRCode** 

{{< highlight java >}}

 @RequestMapping(value = "generate", method = RequestMethod.GET,

    		produces = {MediaType.IMAGE_JPEG_VALUE, MediaType.IMAGE_PNG_VALUE, MediaType.IMAGE_GIF_VALUE, MediaType_IMAGE_TIFF_VALUE, MediaType_IMAGE_BMP_VALUE})

    @ApiOperation(value = "Generate QR Code.")

    public ResponseEntity<byte[]>  generateQRCode(

    		@ApiParam( value = "data", name="data" , required = true)

    		@RequestParam("data") String data,

        HttpServletRequest request,HttpServletResponse response,

        @ApiParam( value = "A user-chosen password that can be used with password-based encryption (PBE) Algo PBEWITHMD5AND128BITAES-CBC-OPENSSL)", name="passKey", required=false) @RequestParam(required=false, value="passKey") String passKey,

        @ApiParam( value = "ForeColor e.g #000000 (Black - RGB(hex))", name="foreColor", required=false) @RequestParam(required=false, value="foreColor") String foreColor,

        @ApiParam( value = "BackgroundColor e.g #FFFFFF (White - RGB(hex))", name="bgColor", required=false) @RequestParam(required=false, value="bgColor") String bgColor,

        @ApiParam( value = "L|M|Q|H - Reed-Solomon error correctionCode Level(from low to high) default=Low", name="ecc", required=false) @RequestParam(required=false, value="ecc") String ecc,

        @ApiParam( value = "Image Size e.g #150x150", name="size", required=false) @RequestParam(required=false, value="size") String size,

        @ApiParam( value = "jpeg|tiff|gif|png|bmp - default=png", name="format", required=false) @RequestParam(required=false, value="format") String format,

        @ApiParam( value = "true|false default=false", name="download", required=false) @RequestParam(required=false, value="download") boolean download,

        @ApiIgnore @Value("#{request.getHeader('" +  ACCEPT_HEADER + "')}") String acceptHeaderValue) throws Exception {


{{< /highlight >}}

**Save QR Code Image** - **QRCodeManagementController.generateQRCode**  

{{< highlight java >}}

 if(download){

 MediaType responseType = responseImageTypeDto.getMediaType();

         responseHeaders.setContentType(responseType);

         responseHeaders.add("Content-Disposition", "attachment; filename="+"Aspose_BarCode_QRCodeGen." + responseType.getSubtype());

 }

{{< /highlight >}}
