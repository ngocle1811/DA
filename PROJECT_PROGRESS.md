# Project Progress

**Cập nhật cuối:** 2026-09-22  
**Phase hiện tại:** Phase 0 — hoàn tất tài liệu thiết kế  
**Stop gate:** Chờ người dùng yêu cầu `continue phase 1` hoặc tương đương.

## 1. Trạng thái phase

| Phase | Trạng thái | Bằng chứng/output | Ghi chú |
|---:|---|---|---|
| 0 | **COMPLETE — DOCUMENTATION ONLY** | `PLAN.md`, `ARCHITECTURE.md`, `DATASET_CATALOG.md`, `REPOSITORY_REVIEW.md`, `GLOSSARY.md`, `PROJECT_PROGRESS.md`, `PHASE_00_REPORT.md` | Không code, không dataset/model download, không benchmark runtime |
| 1 | BLOCKED BY USER GATE | Chưa có | Chỉ bắt đầu khi người dùng yêu cầu |
| 2–12 | NOT STARTED | Chưa có | MVP functional/evaluation track |
| 13 | OPTIONAL / NOT STARTED | Chưa có | ML fusion chỉ sau baseline |
| 14–15 | NOT STARTED | Chưa có | Pi 5 deploy/optimize |
| 16–19 | NOT STARTED | Chưa có | ESP32-P4 feasibility/port/benchmark |
| 20 | NOT STARTED | Chưa có | So sánh cuối |

## 2. Checklist Phase 0

| Hạng mục | Trạng thái | Nơi ghi |
|---|---|---|
| Đọc và ràng buộc toàn yêu cầu | Done | `PHASE_00_REPORT.md` |
| Verify 8 repository chính | Done | `REPOSITORY_REVIEW.md` |
| Verify DMD, UTA-RLDD, YawDD, Drive&Act | Done, có caveat | `DATASET_CATALOG.md` |
| Đề xuất NTHU-DDD | Done, restricted | `DATASET_CATALOG.md` |
| Verify Pi 5/Camera Module 3 NoIR/Picamera2 | Done | `ARCHITECTURE.md`, report |
| Verify ESP32-P4/ESP-DL/ESP-WHO | Done, snapshot theo ngày | `REPOSITORY_REVIEW.md`, report |
| Architecture cuối | Done | `ARCHITECTURE.md` |
| Folder structure | Done | `PLAN.md` |
| Dependency/version policy | Done | `PLAN.md`, `REPOSITORY_REVIEW.md` |
| Benchmark/evaluation strategy | Done | `PLAN.md`, report |
| Dataset strategy/self-recording | Done | `DATASET_CATALOG.md` |
| MVP/optional/risks/P4-hard modules | Done | `PLAN.md`, `ARCHITECTURE.md` |
| Glossary Phase 0 | Done | `GLOSSARY.md` |

## 3. Quyết định đã khóa trong Phase 0

- Modular perception + temporal architecture.
- Hai state machine độc lập; cả hai có `UNKNOWN`.
- Duration dựa timestamp, không dựa FPS giả định.
- Baseline rule-based trước ML fusion.
- PC → Pi 5 CPU → profile/optimize → P4 feasibility.
- `perclos_proxy` dùng tên riêng cho baseline eye-state nhị phân, không đánh đồng PERCLOS gốc.
- MediaPipe Face Landmarker là candidate PC/Pi, không phải cam kết P4.
- P4 dùng sensor/driver đã xác minh; không giả định Camera Module 3 IMX708 plug-and-play.
- Public data và self-recorded data báo metric tách theo task/domain.
- Hành vi buồn ngủ diễn chỉ là `SIMULATED_BEHAVIOR`.

## 4. Môi trường được quan sát

| Item | Giá trị |
|---|---|
| Workspace | `D:\DA` |
| Git repository | Chưa khởi tạo |
| OS dev | Windows 11 Home 64-bit build 26200 |
| Python mặc định | 3.12.10 |
| Python khác | 3.11 |
| Git | 2.52.0.windows.1 |
| OpenCV / MediaPipe / psutil | Chưa cài |

Không có dependency nào được cài ở Phase 0.

## 5. Experiment registry

Chưa có experiment chạy. ID dự kiến đầu tiên của Phase 1:

- `EXP_CAM_PC_001`: camera capture baseline trên PC.
- `EXP_CAM_PC_002`: ảnh hưởng resolution/pixel format.
- `EXP_CAM_PI5_001`: Picamera2 capture baseline trên Pi 5, chỉ khi có thiết bị.

Các ID này là kế hoạch, chưa có result.

## 6. Benchmark log

Chưa tạo `benchmarks/results.csv` vì chưa có benchmark thực và Phase 0 không scaffold code/folder. Phase 1 sẽ tạo schema trước lần đo đầu. Không có metric/FPS/latency/RAM/power nào được tuyên bố.

## 7. Vấn đề mở cần kiểm ở phase tương ứng

| ID | Vấn đề | Phase xử lý |
|---|---|---:|
| O01 | MediaPipe 1.0.1 + OpenCV 5.0.0.93 import/inference ổn trên Python 3.12? | 2 |
| O02 | MediaPipe ARM64 wheel + Python/Picamera2 APT trên Pi OS Trixie có sạch `cv2` không? | 2/14 |
| O03 | Landmark indices/quality đủ ổn với glasses/NoIR? | 2–5 |
| O04 | Định nghĩa MAR và yawn matching rubric cuối | 5 |
| O05 | Camera intrinsics/pose convention | 6 |
| O06 | Gaze baseline có đủ phân biệt mirror/display/down? | 8–9 |
| O07 | Exact thresholds/window/weights | 3–10 qua calibration/validation |
| O08 | DMD package 2026 chứa label nào thực tế? | 12 sau approval/download |
| O09 | License UTA-RLDD cho intended use | Trước download/use |
| O10 | P4X board/camera BOM và chip revision | 16 |
| O11 | ESP-WHO locked profile build được nguyên trạng? | 16–17 |
| O12 | Model/operator/memory budget P4 | 16–18 |

## 8. Điều kiện bắt đầu Phase 1

Chỉ cần người dùng xác nhận tiếp tục. Phase 1 không cần dataset/model. Nếu chưa có Pi/camera, có thể hoàn thành phần PC/file-camera trước và đánh dấu phần hardware thật chưa đo; không bịa kết quả.

## 9. Handoff Phase 1

Phase 1 phải đọc lại:

- mục 12 của `PLAN.md`;
- `FramePacket`, timing points và camera adapter trong `ARCHITECTURE.md`;
- glossary camera/benchmark;
- version policy để tránh cài xung đột `cv2`;
- stop/report/update rule của master specification.
