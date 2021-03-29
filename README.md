**Finding Lane Lines on the Road**
==================================

---

### 1. Pipeline Description - 파이프 라인 설명

선을 찾기 위한 pipeline은 draw_lines를 제외한 총 6단계로 나뉘어 집니다. Pipelines for finding lines are divided into six steps, excluding draw_lines.

먼저 이미지를 grayscale로 변환하여 한 채널로 만듭니다. First, convert the image to grayscale and make it one channel.

그 다음 가우시안 블러를 사용하여 이미지의 노이즈를 줄입니다. Next, reduce the noise in the image using Gaussian Blur.

이후 canny edge를 사용하여 이미지의 외곽 부분을 검출합니다. Subsequently, the edge part of the image is detected using the canny edge of the image.

검출한 외곽 부분을 관심 영역 설정으로 차선 부분만 남겨두도록 합니다. Leave the detected edge part only the lane part with the region of interest setting.

이후 허프 변환을 통해 직선을 검출합니다. Detects straight lines through a huff transformation.

검출한 직선을 보고, 기울기를 계산하여 해당 차선이 오른쪽인지 왼쪽인지 판별합니다. View the detected straight line and calculate the slope to determine whether the lane is right or left.

이렇게 판별한 직선을 해당 이미지에 그리도록 합니다. Draw the straight line you have determined on that image.

### 2. Identify potential shortcomings in pipeline - 파이프 라인에서의 잠재적 단점

해당 코드에서 왼쪽과 오른쪽 차선 판별 부분에서 현재 파이프 라인 상에서는 기울기를 통하여 구분하도록 하였습니다. 만약 기울기가 음의 값인 경우 오른쪽 차선, 양의 값인 경우 왼쪽 차선이 됩니다. 허나 차선이 기울어져 있는 경우, 오른쪽 차선의 기울기가 양의 값을 가지거나 왼쪽 차선이 음의 값을 가질 수 있습니다. 이때에 차선의 오른쪽 혹은 왼쪽 판별에 어려움이 있습니다.

Use the slope to determine the right and left lanes in the code. If the slope is negative, it will be the right lane. And if the slope is positive, it becomes the left lane. However, if the lane is tilted to one side, the slope of the right lane is positive or the slope of the left lane is negative. In this case, it is difficult to determine the right and left lanes.

### 3. Suggest possible improvements to pipeline - 파이프 라인에서의 개선점

기울기를 통해 오른쪽, 왼쪽 차선을 구별하는 것이 아니라 ROI를 오른쪽, 왼쪽으로 구별하여 차선을 찾도록 합니다. 이러한 경우, 차선이 한쪽으로 기울어져 있어도 오른쪽, 왼쪽 차선의 판별이 정확히 할 수 있습니다.

Rather than distinguishing right and left lanes through slope, distinguish ROI right and left to find lanes. In this case, even if the lane is tilted to one side, the right and left lanes can be accurately determined.
