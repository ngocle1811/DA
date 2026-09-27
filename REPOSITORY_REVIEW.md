# Repository và framework review

**Ngày kiểm tra:** 2026-09-22  
**Phương pháp:** repo/tài liệu/registry chính thức và bài báo gốc; phân biệt release, tag, branch HEAD, package registry và model weights. Một repo mở không tự động làm cho mọi weights/dataset của nó có cùng license.

## 1. Bảng bắt buộc

| Repo | Giải quyết gì | Phần hữu ích | Dùng trực tiếp? | Hardware | License | Nhược điểm/rủi ro |
|---|---|---|---|---|---|---|
| [MediaPipe](https://github.com/google-ai-edge/mediapipe) | Pipeline/task ML cho media | Face Landmarker, video/live tracking | Có điều kiện trên PC/Pi | Windows, Linux, Raspberry Pi OS 64-bit theo Python setup; không có target P4 chính thức | Apache-2.0; kiểm riêng model card | Wheel/API/model version; drop frame ở live mode; failure cases pose/occlusion/light |
| [MediaPipe Samples](https://github.com/google-ai-edge/mediapipe-samples) | Minh họa cách gọi API | Raspberry Pi Face Landmarker sample | Tham khảo, không chép kiến trúc | PC/mobile/Pi theo sample | Apache-2.0 | Sample đơn giản, một số README cũ, thiếu telemetry/module hóa |
| [OpenCV](https://github.com/opencv/opencv) | Xử lý ảnh và geometry | color/resize/draw/video, `solvePnP`, calibration | Có trên PC/Pi | x86-64, ARM64 và nhiều nền tảng | Apache-2.0 | 4.x/5.x khác API; xung đột nhiều package `cv2`; không phải runtime P4 |
| [Open Model Zoo](https://github.com/openvinotoolkit/open_model_zoo) | Models/demos cho OpenVINO | gaze/head-pose candidate | Optional, environment riêng | PC; Pi support cần smoke test riêng | Code Apache-2.0; model có metadata riêng | Maintenance mode; latest tag cũ; Raspberry Pi OS không nằm trong matrix ARM64 chính thức |
| [L2CS-Net](https://github.com/Ahmednull/L2CS-Net) | Deep gaze yaw/pitch | Baseline gaze research | Optional, pin SHA/fork | PC; Pi chỉ sau benchmark | Code MIT; weights chưa rõ riêng | Không release; dependencies lỏng; ResNet-50 nặng; output không phải gaze zone |
| [Picamera2](https://github.com/raspberrypi/picamera2) | Python API camera trên libcamera | Adapter Camera Module 3/IMX708 | Có, qua APT trên Pi | Raspberry Pi OS | BSD-2-Clause | Repo ghi beta; phải giữ Picamera2/libcamera tương thích; không phải inference runtime |
| [ESP-DL](https://github.com/espressif/esp-dl) | Runtime/convert/model components cho Espressif | `.espdl`, quantization, operator/kernel, face model | Có ở Phase 16+ | ESP32-P4/S3 và targets được docs liệt kê | MIT | Operator/attribute/layout hạn chế; quantization bắt buộc cho nhiều CNN; registry/GitHub release lệch |
| [ESP-WHO](https://github.com/espressif/esp-who) | Platform/example vision dựa ESP-DL | Camera async, face detect, board scaffolding | Chọn lọc ở Phase 17 | P4 Function EV và các board nêu trong README | “ESPRESSIF MIT”, giới hạn sản phẩm Espressif | Master refactored chưa semver; latest v0.5.0 lỗi thời; không có blink/gaze/drowsiness example |

## 2. Snapshot version có thể tái kiểm tra

| Thành phần | Release/package/tag hiện hành | Commit kiểm tra | Ghi chú |
|---|---|---|---|
| MediaPipe repo | GitHub `v1.0.0`; PyPI `1.0.1` | [`20e8f2a`](https://github.com/google-ai-edge/mediapipe/commit/20e8f2ae3365d46fa02037b54911b72e13494809) | Package mới hơn GitHub release label |
| MediaPipe Samples | `v0.1.4` | [`c2518ec`](https://github.com/google-ai-edge/mediapipe-samples/commit/c2518ec444c3a3a99689e5d31eddadc240c83a0c) | Repo mẫu |
| OpenCV | `5.0.0`; maintenance `4.14.0` | [`8a03a93`](https://github.com/opencv/opencv/commit/8a03a932f6d75b818200c4293a929c052319f8c0) trên 5.x | Wheel: 5.0.0.93 / 4.14.0.94 |
| Open Model Zoo | Không có GitHub Release; tag `2024.6.0` | [`a6946b6`](https://github.com/openvinotoolkit/open_model_zoo/commit/a6946b6d6ce42cbf4278df20275fab199655fc7d) | Maintenance mode as model source |
| L2CS-Net | Không release/tag | [`a4d8f7f`](https://github.com/Ahmednull/L2CS-Net/commit/a4d8f7fa5436a2b2b9f088471623b552a85811bd) | Commit 2023-11-06 |
| Picamera2 | `v0.3.37` | [`73ce3b7`](https://github.com/raspberrypi/picamera2/commit/73ce3b7a27e600abec704a843975f4925f029d0a) | Deployment dùng APT version thực tế |
| ESP-DL | Component Registry `3.3.11`; GitHub Latest `v3.2.0` | [`1012855`](https://github.com/espressif/esp-dl/commit/10128554f7e7176ce3cedb99070bbff696018844) | Registry là nguồn component mới hơn |
| ESP-WHO | Master chưa semantic release; GitHub Latest `v0.5.0` lỗi thời | [`1abda05`](https://github.com/espressif/esp-who/commit/1abda05e1c0782237fcb9e8d33a2fa7e105f06b2) | Dùng commit + dependency lock |
| ESP-IDF | `v6.1` release hiện hành được nghiên cứu | [release](https://github.com/espressif/esp-idf/releases/tag/v6.1) | Reproduction WHO hiện lock 5.5.5 |
| OpenVINO runtime | `2026.4.0` | [release](https://github.com/openvinotoolkit/openvino/releases/tag/2026.4.0) | Optional, không là core baseline |

Không coi commit snapshot là “version triển khai”. Exact deployed version chỉ tồn tại sau khi environment thực sự build/run và được lock.

## 3. MediaPipe

### Hỗ trợ và output thật

[Python setup chính thức](https://developers.google.com/edge/mediapipe/solutions/setup_python) nêu Windows, macOS, Linux và Raspberry OS 64-bit, Python 3.9+. PyPI `mediapipe 1.0.1` có ARM64 Linux `manylinux_2_28_aarch64`; classifier liệt kê Python 3.9–3.12 và package kéo `opencv-contrib-python`.

[Face Landmarker Python](https://developers.google.com/edge/mediapipe/solutions/vision/face_landmarker/python) xuất 478 facial landmarks 3D; tùy chọn 52 blendshapes và facial transformation matrix. Nó **không** xuất EAR, MAR, PERCLOS, yawn, nod, gaze zone hay DMS state. Project phải tự định nghĩa/tính/đánh giá các tín hiệu đó.

`VIDEO`/`LIVE_STREAM` dùng tracking để giảm inference. Ở live stream, task có thể bỏ frame mới khi bận. Vì vậy phải đo bốn count khác nhau: capture, submitted, processed, dropped.

### Model limitations

[Face Mesh V2 Model Card](https://storage.googleapis.com/mediapipe-assets/Model%20Card%20MediaPipe%20Face%20Mesh%20V2.pdf) mô tả model Apache-2.0, thiết kế cho video monocular/front-facing mobile AR, không dùng cho quyết định life-critical. Failure cases gồm quay quá xa, occlusion, mặt xa camera, low light, noise/motion mạnh. Đây chính là lý do kiến trúc có quality gate/unknown.

### Quyết định

- PC/Pi: candidate baseline trực tiếp; phải benchmark.
- P4: không có target ESP-IDF/wheel/runtime trực tiếp. `.task` không phải `.espdl`; không nói “convert MediaPipe” nếu chưa tách model, export ONNX, audit operator và so accuracy.

## 4. MediaPipe Samples

[Repo samples](https://github.com/google-ai-edge/mediapipe-samples) chỉ minh họa fundamental steps. Có [Face Landmarker Raspberry Pi sample](https://github.com/google-ai-edge/mediapipe-samples/tree/main/examples/face_landmarker/raspberry_pi).

Sample dùng `cv2.VideoCapture`, callback/global state, BGR→RGB và UI minh họa. Một số hướng dẫn còn nhắc Buster. Dự án chỉ học cách tạo task/callback; sẽ thay bằng Picamera2, timestamp đơn điệu, bounded queue, structured results, latency/drop metrics và module có test.

## 5. OpenCV

- [OpenCV 5.0.0](https://github.com/opencv/opencv/releases/tag/5.0.0) là major stable mới và yêu cầu C++17.
- [OpenCV 4.14.0](https://github.com/opencv/opencv/releases/tag/4.14.0) là maintenance line 4.x.
- PyPI candidates: `opencv-contrib-python==5.0.0.93` và fallback có kiểm soát `4.14.0.94`.
- [Package guide](https://pypi.org/project/opencv-contrib-python/) yêu cầu chỉ cài **một** trong bốn wheel OpenCV vì đều dùng namespace `cv2`.

MediaPipe 1.0.1 kéo `opencv-contrib-python`; không cài thêm `opencv-python`, `*-headless` hoặc APT `python3-opencv` vào cùng interpreter mà không kiểm `cv2.__file__`. Candidate smoke đầu: MediaPipe 1.0.1 + contrib 5.0.0.93; nếu lỗi, thử 4.14.0.94 trong environment sạch và ghi kết quả. OpenCV không được giả định chạy trên P4.

## 6. Open Model Zoo và OpenVINO

[OMZ README](https://github.com/openvinotoolkit/open_model_zoo) nói repository ở maintenance mode như nguồn models. Trang GitHub Releases trống; `2024.6.0` là tag, không gọi sai là release.

Candidate hữu ích: [`gaze-estimation-adas-0002`](https://docs.openvino.ai/2023.3/omz_models_model_gaze_estimation_adas_0002.html): hai eye crop 60×60 + ba góc head pose → gaze vector 3D chưa normalize. Con số 6.95° trong model page dựa internal dataset 60 người, không phải accuracy cho cabin này.

[OpenVINO 2026.4 system requirements](https://docs.openvino.ai/2026/about-openvino/release-notes-openvino/system-requirements.html) có ARM/ARM64 CPU nhưng matrix ARM64 nêu Ubuntu 22.04, không nêu Raspberry Pi OS. Do đó:

- optional experiment trên PC;
- Pi smoke test riêng, không cam kết support;
- không đưa OpenVINO/OMZ vào dependency core;
- không dùng trên P4.

## 7. L2CS-Net

[Repo chính thức](https://github.com/Ahmednull/L2CS-Net) là PyTorch implementation của [arXiv:2203.03339](https://arxiv.org/abs/2203.03339); bản hội nghị ICFSP 2023 có [DOI](https://doi.org/10.1109/ICFSP59764.2023.10372944). Kiến trúc ResNet-50 với hai head yaw/pitch; output là góc gaze, không phải gaze zone/distraction state.

Rủi ro reproducibility:

- không release/tag;
- `pyproject.toml` dùng lower bounds và một Git dependency không pin commit;
- hướng dẫn cài đặt có đường dẫn fork;
- code MIT nhưng pretrained weights trên Drive không có license riêng rõ.

Chỉ dùng nếu Phase 8 chứng minh baseline nhẹ thiếu chất lượng: fork/pin exact SHA, lock dependency, checksum weights, lưu license record, benchmark PC/Pi before/after. Không port trực tiếp ResNet-50 sang P4.

## 8. Picamera2/libcamera/Raspberry Pi OS

Picamera2 là Python API chính thức thay PiCamera legacy và chạy trên libcamera. [Camera software docs](https://www.raspberrypi.com/documentation/computers/camera_software.html) liệt kê Camera Module 3/IMX708 được stack Raspberry Pi hỗ trợ.

Deployment policy:

- Raspberry Pi OS Lite 64-bit Trixie image 2026-09-15, kernel 6.18, SHA256 `cdf4f3bfac35ae947b46e4e767f935453810549779ac3290e05a6754aee627e5` là candidate.
- Cài `python3-picamera2` bằng APT theo [Picamera2 manual](https://datasheets.raspberrypi.com/camera/picamera2-manual.pdf), không ép `pip==0.3.37`.
- Ghi `python3 --version`, `apt-cache policy python3-picamera2`, libcamera/rpicam versions và `cv2.__file__` trên thiết bị thật.
- Tuân PEP 668/venv của OS; không để hai provider `cv2` cùng interpreter.

## 9. ESP-DL

[ESP Component Registry 3.3.11](https://components.espressif.com/components/espressif/esp-dl/versions/3.3.11) là nguồn stable mới hơn badge GitHub `v3.2.0`. Runtime/API chủ yếu C++, conversion/ESP-PPQ chạy Python. Model deploy là `.espdl`, không trực tiếp `.task`, ONNX hay PyTorch.

[Getting Started](https://docs.espressif.com/projects/esp-dl/en/latest/getting_started/readme.html) khuyến nghị ESP32-S3/P4 và ESP-IDF `release/v5.3`+. [Operator support table](https://github.com/espressif/esp-dl/blob/master/operator_support_state.md) ngày sinh 2026-09-01 nêu:

- khuyến nghị ONNX opset 18;
- 64 operator được triển khai/test, nhưng không đủ mọi attribute;
- Conv/Gemm/MatMul không hỗ trợ float32, nên CNN thực tế cần quantization;
- grouped convolution giới hạn `1` hoặc `input_channels`;
- Resize chỉ INT8 và hạn chế mode/attribute;
- một số op dùng NHWC/NWC thay ONNX layout thông thường;
- P4 dùng PIE v2 và round-half-to-even.

Repo có quantization w8a8/w16a16/w8a16, static memory planner và dual-core scheduling chủ yếu cho Conv2D/DepthwiseConv2D. Model zoo có face detection nhưng không có Face Mesh/gaze/drowsiness hoàn chỉnh.

**Kết luận:** đúng runtime cho P4, nhưng mỗi model phải có operator audit, calibration set, quantization accuracy parity, peak internal RAM/PSRAM và latency thật.

## 10. ESP-WHO

Master đã refactor cho ESP-DL mới, hỗ trợ P4, camera/inference async và LVGL. [Examples](https://github.com/espressif/esp-who/tree/master/examples) có face recognition/object detection/tracking/OCR/QR, không có official gaze, face mesh, blink, yawn hay drowsiness.

Điểm version quan trọng:

- GitHub “Latest” v0.5.0 năm 2018 là obsolete cho master hiện nay.
- Master chưa có semantic release; pin exact commit.
- P4 face-detect [dependency lock](https://github.com/espressif/esp-who/blob/master/examples/object_detect/dependencies.lock.esp32_p4_function_ev_board_noglib.human_face_detect) tại thời điểm kiểm tra khóa ESP-IDF 5.5.5 và ESP-DL 3.3.8.
- License là biến thể “ESPRESSIF MIT” chỉ cho dùng trên sản phẩm Espressif, không ghi đơn giản MIT chuẩn.

ESP-WHO là scaffold/reference cho camera→face trên P4, không phải hệ DMS sẵn có.

## 11. Camera P4 không dùng lại theo giả định

Pi Camera Module 3 là IMX708, được libcamera/Pi hỗ trợ. [Danh sách sensor của esp-video-components](https://github.com/espressif/esp-video-components/blob/master/esp_cam_sensor/README.md) hiện không liệt kê IMX708. P4 có MIPI-CSI/DVP/UVC không đủ chứng minh driver, pinout/voltage, RAW ISP tuning hay autofocus tương thích.

Phase 16 phải chọn sensor P4 được Espressif hỗ trợ (candidate board P4X current + camera bundle) hoặc UVC. IMX708/Camera Module 3 ghi `unverified/not in default P4 BOM`, không “plug-and-play”.

## 12. Hai dependency profile P4, không trộn

### Profile A — tái lập ESP-WHO trước

- WHO commit candidate `1abda05e1c0782237fcb9e8d33a2fa7e105f06b2`.
- Giữ lock example: ESP-IDF 5.5.5 + ESP-DL 3.3.8.
- Mục tiêu: build/flash camera + human-face-detect như upstream trước khi sửa.

### Profile B — nghiên cứu ESP-DL mới

- ESP-DL 3.3.11.
- ESP-IDF v6.1 candidate; chỉ chốt sau build/flash/inference test.
- Không tự nâng dependency của WHO rồi gọi đó là upstream-supported.

ESP-IDF v6.1 đổi default silicon revision P4 sang v3.0; chip `<3.0` cần `CONFIG_ESP32P4_SELECTS_REV_LESS_V3=y`. Benchmark phải ghi chip revision, board revision và binary compatibility.

## 13. Dependency policy PC/Pi

1. PC dùng Python 3.12.x hiện có để compatibility smoke; ghi exact patch.
2. Candidate: `mediapipe==1.0.1` + `opencv-contrib-python==5.0.0.93` trong venv sạch.
3. Fallback thử riêng `opencv-contrib-python==4.14.0.94`; không âm thầm downgrade.
4. Pi dùng Python của OS image trước; MediaPipe wheel smoke test; Picamera2 qua APT.
5. OpenVINO/L2CS có environment optional riêng.
6. Lock có hash chỉ tạo sau test import, sample inference, camera path và license/model hash.
7. Model manifest ghi URL, SHA256, model card/license, input color/range/normalization và output semantics.

## 14. Không copy code mù quáng

Trước khi lấy bất kỳ sample/module:

- đọc license ở exact commit;
- link file/source commit trong note;
- hiểu input/output/color/timestamp/threading;
- viết test nhỏ chứng minh hành vi;
- thay global/magic values bằng config/contracts;
- đo bằng pipeline của project;
- ghi phần đã sửa và lý do;
- không dùng metric upstream làm kết quả của project.
