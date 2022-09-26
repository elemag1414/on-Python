# Simple Background Removal 

```python
import os, sys, cv2 
import numpy as np
from termcolor import colored 
from mouse_util import COLOR  ## COLOR tuple definition

### Youtube reference : https://www.youtube.com/watch?v=YrxhUePkAiY

baseDir = 'path/to/video'
videoFile = 'vidFile.mp4'
videoPath = os.path.join(baseDir, videoFile)

assert os.path.exists(videoPath), colored(f"{videoPath} Not Found", "yellow")

cap = cv2.VideoCapture(videoPath)
numFrames = int(cap.get(cv2.CAP_PROP_FRAME_COUNT))

success, frame = cap.read()
_mean = np.float32(frame)
fcnt = 1 


while True:

  success, frame = cap.read()

  if not success:
    break

  cv2.accumulateWeighted(frame, _mean, 0.001) # cv2.accumulateWeighted(src, dst, alpha)
  frameDelta = cv2.absdiff(frame, cv2.convertScaleAbs(_mean))

  frame = cv2.putText(frame, f"{fcnt}/{numFrames}", (20, 30), cv2.FONT_HERSHEY_SIMPLEX, .8, COLOR.yellow, 2)
  mergedFrame = np.concatenate((frame, frameDelta), axis=1)

  cv2.imshow(f"{videoFile} w/ background filtering", mergedFrame)

  keyIn = cv2.waitKey(25)
  if keyIn == ord('q'):
    break
  
  fcnt += 1

cv2.destroyAllWindows()
cap.release()

```
