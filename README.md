### GKImagePicker

Ever wanted a custom crop area for the UIImagePickerController? Now you can have it with _GKImagePicker_. Just set your custom crop area and that's it. Just 4 lines of code. If you don't set it, it uses the same crop area as the default UIImagePickerController.

### How to use it

- just drag and drop the files in under "GKClasses" & "GKImages" into your project.
- look at the sample code below.
- this project contains a sample project as well, just have a look at the implementation of `ViewController.m` 
- have fun and follow [@gekitz](http://www.twitter.com/gekitz).


### Sample Code

First create the GKImage picker:

''Swift
    let picker = GKImagePicker.init()
    picker.delegate = self
''

Specify your (starting) crop area:

''
picker.cropSize = CGSize.init(width: 200, height: 200)
''

Specify if the crop area can be resized:

''
picker.hasResizeableCropArea = true
''

Then you can present the picker, in a popover for instance: 

''
picker.imagePickerController = UIImagePickerController.init()
picker.imagePickerController!.modalPresentationStyle = .popover // or another presentation style
self.present(self.picker.imagePickerController!, animated: true, completion: nil)
if let popoverPresentationController = self.imagePicker.imagePickerController!.popoverPresentationController {
    popoverPresentationController.permittedArrowDirections = .up
    popoverPresentationController.barButtonItem = self.customBarButtonItem
''

You need to implement the delegate, if you want to use the cropped image:
''
extension YourViewController: GKImagePickerDelegate {

func imagePicker(_ imagePicker: GKImagePicker, cropped image: UIImage) {
    self.image = image // save the cropped image
    self.imagePicker.imagePickerController!.dismiss(animated: true, completion: nil) // dismiss the controller
}

}
''

This code results into the following controller + crop area:


It's even possible to let the user adjust the crop area (thanks to [@pathonhauser](http://www.twitter.com/pathonhauser) for this pull request) by setting one additional property:
	     
This code results into the following controller + adjustable crop area:
### License
Under MIT. See license file for details.



    