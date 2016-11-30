# AvatarGenerator
Utility class to generate avatar image from image captured from gallery or camera.

![Output sample](https://github.com/jineshfrancs/CameraHandler/blob/master/screens/facedetect.gif)

Create object for CameraHandler and call showDialogToCaptureImage() method to open Capture dialog
 ```
 handler=new CameraHandler(this);
 handler.showDialogToCaptureImage();
  ```
Override OnActivityResult and implement CameraHandler.OnImageResultListner interface

 ```
    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        handler.onActivityResult(requestCode, resultCode, data);
    }

    @Override
    public void onImageResult(String imageName, String imagePath, Bitmap imageFile, int sourceType) {
        if(sourceType==CameraHandler.CAMERA_TYPE){
            Log.e("imageName",imageName);
            Log.e("imagePath",imagePath);
            Log.e("type","CameraType");
            imageView.setImageBitmap(imageFile);
        }else if(sourceType==CameraHandler.GALLERY_TYPE){
            Log.e("imageName",imageName);
            Log.e("imagePath",imagePath);
            Log.e("type","GalleryType");
            imageView.setImageBitmap(imageFile);
        }
    }
    
 ```
You can change the default directory name to capture the images to sd card by changing this variable name in CameraHandler.java
 ```
private static final String IMAGE_DIRECTORY_NAME = "Give_a_directory_name_to_store_captured_images";
 ```