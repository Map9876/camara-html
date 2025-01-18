# camara-html
网页摄像头

GPT 4o
￼
Copilot Chat
Modify code to use front camera

https://www.cnblogs.com/jocongmin/p/18617914
js 如何调用浏览器摄像头api，MediaDevices.getUserMedia

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Take Photo</title>
</head>
<body>
  <h1>Take a Photo</h1>
  <video id="video" width="640" height="480" autoplay></video>
  <button id="snap">Snap Photo</button>
  <canvas id="canvas" width="640" height="480"></canvas>

  <script>
    // 获取视频元素和画布元素
    const video = document.getElementById('video');
    const canvas = document.getElementById('canvas');
    const context = canvas.getContext('2d');
    const snapButton = document.getElementById('snap');

    // 请求访问用户的摄像头
    navigator.mediaDevices.getUserMedia({ video: true })
      .then(stream => {
        // 将视频流设置为视频元素的源
        video.srcObject = stream;
      })
      .catch(error => {
        console.error('Error accessing the camera', error);
      });

    // 当用户点击“Snap Photo”按钮时，拍摄照片
    snapButton.addEventListener('click', () => {
      // 将视频帧绘制到画布上
      context.drawImage(video, 0, 0, 640, 480);

      // 从画布中提取图像数据
      const imageData = canvas.toDataURL('image/png');

      // 你可以在这里使用图像数据，例如将其发送到服务器或显示在页面上
      console.log(imageData);
    });
  </script>
</body>
</html> 
```

 'facingMode': "user" 调用前置摄像头，后置摄像头使用video
 
修改为前置摄像头
要修改代码以使用前置摄像头，可以在调用 getUserMedia 方法时，设置 video 选项中的 facingMode 为 user。这是修改后的代码：

HTML

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Take Photo</title>
</head>
<body>
  <h1>Take a Photo</h1>
  <video id="video" width="640" height="480" autoplay></video>
  <button id="snap">Snap Photo</button>
  <canvas id="canvas" width="640" height="480"></canvas>

  <script>
    // 获取视频元素和画布元素
    const video = document.getElementById('video');
    const canvas = document.getElementById('canvas');
    const context = canvas.getContext('2d');
    const snapButton = document.getElementById('snap');

    // 请求访问用户的前置摄像头
    navigator.mediaDevices.getUserMedia({ video: { facingMode: 'user' } })
      .then(stream => {
        // 将视频流设置为视频元素的源
        video.srcObject = stream;
      })
      .catch(error => {
        console.error('Error accessing the camera', error);
      });

    // 当用户点击“Snap Photo”按钮时，拍摄照片
    snapButton.addEventListener('click', () => {
      // 将视频帧绘制到画布上
      context.drawImage(video, 0, 0, 640, 480);

      // 从画布中提取图像数据
      const imageData = canvas.toDataURL('image/png');

      // 你可以在这里使用图像数据，例如将其发送到服务器或显示在页面上
      console.log(imageData);
    });
  </script>
</body>
</html>


```           if(navigator.mediaDevices&&navigator.mediaDevices.getUserMedia){
                navigator.mediaDevices.getUserMedia({
                    'audio':true,
                    'video':{ 'facingMode': "user" }//调用前置摄像头，后置摄像头使用video: { facingMode: { exact: "environment" } }
                
https://github.com/copilot/c/014b67ac-5049-4c4d-a74e-d20e542b0ca8

https://segmentfault.com/a/1190000014222822
                    
