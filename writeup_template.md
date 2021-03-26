**Finding Lane Lines on the Road**
==================================

---

### 1. Pipeline Description - 파이프 라인 설명

선을 찾기 위한 pipeline은 draw_lines를 제외한 총 6단계로 나뉘어 집니다.

먼저 이미지를 grayscale로 변환하여 한 채널로 만듭니다.

그 다음 가우시안 블러를 사용하여 이미지의 노이즈를 줄입니다.

이후 canny edge를 사용하여 이미지의 외곽부분을 검출합니다.

검출한 외곽부분을 관심영역 설정으로 차선부분만 남겨두도록 합니다.

이후 허프변환을 통해 직선을 검출합니다.

검출한 직선을 보고, 기울기를 계산하여 해당 차선이 오른쪽인지 왼쪽인지 판별합니다.

이렇게 판별한 직선을 해당 이미지에 그리도록 합니다.

### 2. Identify potential shortcomings with your current pipeline

해당 코드에서

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
