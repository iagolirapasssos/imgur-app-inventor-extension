# Imgur Upload Extension for MIT App Inventor

## Overview

This extension allows you to upload images to Imgur and make GET requests from within your MIT App Inventor projects. With this extension, you can easily send HTTP requests, including the ability to upload images using **multipart/form-data**, directly from your App Inventor apps.

---

## For Block Programmers (MIT App Inventor Users)

### How to Use the Extension

1. **Adding the Extension**:
   - Download the `.aix` file of the extension and import it into your MIT App Inventor project.
   - Go to the "Extensions" section and click "Import Extension". Then, upload the `.aix` file.
   
2. **Blocks Provided by the Extension**:
   The extension provides two main functions for you to use in your App Inventor project:

   - **SendGetRequest(url)**: Sends an asynchronous GET request to the specified URL.
     - **Events**:
       - `GotResponse(responseContent)`: Triggered when a GET request receives a response.
       - `ErrorOccurred(errorMessage)`: Triggered when an error occurs during the request.

   - **UploadImageToImgur(imagePath, authToken)**: Uploads an image file to Imgur using a POST request with `multipart/form-data`.
     - **Parameters**:
       - `imagePath`: The local file path of the image (captured by the camera or chosen from the file system).
       - `authToken`: Your Imgur API token (you need to create an Imgur account and get the API token from your Imgur dashboard).
     - **Events**:
       - `ImageUploaded(responseContent)`: Triggered when the image is successfully uploaded.
       - `ErrorOccurred(errorMessage)`: Triggered when an error occurs during the image upload process.

### Example Blocks:

Here is an example of how you can use these blocks to upload an image to Imgur:

```plaintext
when Button1.Click
    call Camera1.TakePicture

when Camera1.AfterPicture(image)
    call Imgur1.UploadImageToImgur(image, "your_imgur_api_token")

when Imgur1.ImageUploaded(responseContent)
    set Label1.Text to responseContent

when Imgur1.ErrorOccurred(errorMessage)
    set Label1.Text to "Error: " + errorMessage
```

### Key Notes for MIT App Inventor Users:
- **Authorization**: Make sure you have a valid Imgur API token.
- **Image Path**: Use the Camera or File component to get the correct file path of the image.
- **Error Handling**: Always handle possible errors using the `ErrorOccurred` event to ensure a smooth user experience.

---

## For Java Developers

### Contributing to the Project

If you're a Java developer and would like to contribute to this extension, here are some things to keep in mind:

#### Areas for Improvement

1. **Error Handling**:
   - Currently, the extension catches general exceptions and passes error messages back to App Inventor via the `ErrorOccurred` event. This could be improved by providing more detailed error handling, including specific HTTP error codes and messages from the server.

2. **Progress Tracking**:
   - For large image uploads, it would be useful to implement a progress tracking feature. This could involve adding events to indicate the percentage of the file that has been uploaded.

3. **Improving Compatibility**:
   - At present, the extension is designed to work with Imgur's API using `multipart/form-data` for uploads. However, we could expand this extension to support other media upload platforms, such as Google Drive or Dropbox, through modular improvements.

4. **Refactoring the Request Handling Logic**:
   - The code could be refactored to use a more structured approach for handling various types of HTTP requests (e.g., `PUT`, `DELETE`, etc.) and file types.
   - Additionally, we could introduce more flexibility in request headers and parameters, making the extension more versatile for other APIs beyond Imgur.

5. **Testing and Optimizing for Large Files**:
   - Currently, the image upload process reads the entire file into memory. Optimizing the file handling process for large image uploads, such as using buffered streams or chunked transfer encoding, would prevent potential memory issues in devices with limited resources.

6. **Documentation**:
   - Further documentation could be created to guide developers on extending this project for other file formats or HTTP methods. A clear example-based approach would help developers who are new to extension development for MIT App Inventor.

#### How to Contribute

- **Clone the Repository**: You can fork and clone the repository to make your contributions.
- **Build Environment**: The extension is currently built with Java 7 to ensure compatibility with MIT App Inventor's limitations.
- **Testing**: Ensure that any changes or new features are well-tested within the App Inventor environment, especially for different device types and Android versions.
- **Pull Requests**: Once you've made your changes, submit a pull request with detailed information on what was changed and why. Make sure to include any new examples or use cases if necessary.

---

### License

This extension is open source. Feel free to modify and distribute it as needed, but make sure to give proper credit to the original authors.

---

If you have any questions or suggestions, feel free to open an issue or contact the project maintainers.
