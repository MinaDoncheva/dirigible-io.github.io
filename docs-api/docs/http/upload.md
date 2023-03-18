---
title: Upload
---

Upload
===

HTTP Upload is used to consume files posted as multipart request.

=== "Overview"
- Module: `http/upload`
- Definition: [https://github.com/eclipse/dirigible/issues/16](https://github.com/eclipse/dirigible/issues/16)
- Source: [/http/upload.js](https://github.com/eclipse/dirigible/blob/master/components/api-http/src/main/resources/META-INF/dirigible/http/upload.js)
- Status: `stable`



### Basic Usage

```javascript
var upload = require("http/upload");
var request = require("http/request");
var response = require("http/response");

if (request.getMethod() === "POST") {
    if (upload.isMultipartContent()) {
        var fileItems = upload.parseRequest();
        for (i = 0; i < fileItems.size(); i++) {
            var fileItem = fileItems.get(i);
            if (!fileItem.isFormField()) {
                // Getting the file name and bytes
                response.println("File Name: " + fileItem.getName());
                response.println("File Bytes (as text): " + String.fromCharCode.apply(null, fileItem.getBytes()));
            } else {
                // Getting the headers
                var fileItemHeaders = fileItem.getHeaders();
                var fileItemHeaderNames = fileItemHeaders.getHeaderNames();

                var fieldHeaders = {};
                for (j=0; j<fileItemHeaderNames.size(); j++) {
                  var headerName = fileItemHeaderNames.get(j);
                  var headerValue = fileItemHeaders.getHeader(headerName);
                  fieldHeaders[headerName] = headerValue;
                }
                response.println("Field Headers: " + JSON.stringify(fieldHeaders));
                
                // Getting the field name and value
                response.println("Field Name: " + fileItem.getFieldName());
                response.println("Field Text: " + fileItem.getText());
            }
        }
    } else {
        response.println("The request's content must be 'multipart'");
    }
} else if (request.getMethod() === "GET") {
    response.println("Use POST request.");
}

response.flush();
response.close();
```


### Functions

---

Function     | Description | Returns
------------ | ----------- | --------
**isMultipartContent()**   | Returns true if the HTTP request contains files content and false otherwise | *boolean*
**parseRequest()**   | Returns a HttpFileItems object by parsing the HTTP request | *HttpFileItems*




### Objects

---

#### HttpFileItems


Function     | Description | Returns
------------ | ----------- | --------
**get(index)**   | The HttpFileItem object by the *index* | *HttpFileItem*
**size()**   | The size of the list of HttpFileItem objects | *HttpFileItem*


##### HttpFileItem


Function     | Description | Returns
------------ | ----------- | --------
**getContentType()**   | The HttpFileItem's data content type | *string*
**getName()**   | The HttpFileItem's name | *string*
**getSize()**   | The HttpFileItem's size | *long*
**getBytes()**   | Return the HttpFileItem's content as byte array | *array of byte*
**getText()**   | Return the HttpFileItem's content as string | *string*
**getInputStream()**   | Return the input stream of the HttpFileItem's content | *streams.InputStream*
**isFormField()**   | Whether the HttpFileItem represents a form field | *boolean*
**getFieldName()**   | The HttpFileItem's field name | *string*
**getHeaders()**   | The HttpFileItem's headers | *array of HttpFileItemHeaders*


#### HttpFileItemHeaders


Function     | Description | Returns
------------ | ----------- | --------
**getHeaderNames()**   | The HttpFileItemHeader's names | *array of strings*
**getHeader(headerName)**   | The HttpFileItemHeader's value for the given header name | *string*
