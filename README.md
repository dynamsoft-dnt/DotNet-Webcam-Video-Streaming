# DotNet Webcam Video Streaming

The sample shows how to easily stream webcam video with [Dynamic .NET TWAIN][1] C# API. You can also implement a webcam barcode reader with [Dynamsoft Barcode SDK][2].

## Getting Started
1. Import the project to **Visual Studio**.
2. Install **Dynamic .NET TWAIN** and **Dynamsoft Barcode Reader** via **NuGet Package Manager**:

    ![install SDK via nuget](http://www.codepool.biz/wp-content/uploads/2016/10/nuget-package-manager.PNG)
3. Connect a USB webcam to your PC.
4. Build and run the application:

    ![Windows barcode reader with webcam](http://www.codepool.biz/wp-content/uploads/2016/10/dotnet-webcam-barcode-reader.PNG)

## Q&A
### Fail to build the project?
If you see the following error when building the project, remove the Dynamic .NET TWAIN reference for WPF:
![Building error caused by WPF reference](http://www.codepool.biz/wp-content/uploads/2016/10/nuget-wpf-error.PNG)

### How to display webcam video?

```C#
dynamicDotNetTwain.SupportedDeviceType = EnumSupportedDeviceType.SDT_WEBCAM;
SetWebCamAsDntSrc(cbxWebCamSrc.Text);
dynamicDotNetTwain.SetVideoContainer(picBoxWebCam);
dynamicDotNetTwain.OpenSource();
dynamicDotNetTwain.IfShowUI = true;
ResizeVideoWindow(0);
picBoxWebCam.Visible = true;
picBoxWebCam.BringToFront();
panelResult.BringToFront();
```

### How to receive frame buffer?

```C#
this.dynamicDotNetTwain.OnFrameCapture += new Dynamsoft.DotNet.TWAIN.Delegate.OnFrameCaptureHandler(this.dynamicDotNetTwain_OnFrameCapture);

private void dynamicDotNetTwain_OnFrameCapture(Dynamsoft.DotNet.TWAIN.Interface.OnFrameCaptureEventArgs arg)
{
    // Do something with the buffer
    Bitmap bitmap = arg.Frame;
}
```

[1]:http://www.dynamsoft.com/Products/.Net-TWAIN-Scanner.aspx
[2]:http://www.dynamsoft.com/Products/Dynamic-Barcode-Reader.aspx

