# Convert Avi to MP4

##### [Back to Home](../README.md)


### MP4로 변환하는 2가지 방법 

1. ffmeg을 이용한 변환 

```python
import subprocess
import os

src = './src'
dst = './mp4'

for root, dirs, filenames in os.walk(src, topdown=False):
    #print(filenames)
    for filename in filenames:
        print('[INFO] 1',filename)
        try:
            _format = ''
            if ".flv" in filename.lower():
                _format=".flv"
            if ".mp4" in filename.lower():
                _format=".mp4"
            if ".avi" in filename.lower():
                _format=".avi"
            if ".mov" in filename.lower():
                _format=".mov"

            inputfile = os.path.join(root, filename)
            print('[INFO] 1',inputfile)
            outputfile = os.path.join(dst, filename.lower().replace(_format, ".mp4"))
            subprocess.call(['ffmpeg', '-i', inputfile, outputfile])  
        except:
            print("An exception occurred")
```

<br>

2. MoviePy를 이용한 변환 

* MoviePy 패키지 설치하기 

```
$ pip3 install MoviePy
```

* MP4로 변환 하기

```python
import moviepy.editor as moviepy
clip = moviepy.VideoFileClip("myvideo.avi")
clip.write_videofile("myvideo.mp4")
```
