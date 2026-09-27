# Dataset Catalog và chiến lược dữ liệu

**Ngày kiểm tra:** 2026-09-22  
**Nguyên tắc:** nguồn chính thức/bài báo gốc trước; không bypass login/form/license; URL công khai không tự động đồng nghĩa quyền tải hàng loạt, sửa hoặc phân phối lại.

## 1. Kết luận lựa chọn

| Dataset | Vai trò dự kiến | Ưu tiên | Trạng thái tải tự động |
|---|---|---:|---|
| DMD 2026 | Gaze zone, distraction/activity; phụ trợ fatigue | Cao, có điều kiện license | Không: gửi form, chờ email |
| UTA-RLDD | Đánh giá chuỗi alert/low-vigilance/drowsy | Cao, có điều kiện license | Chưa được tác giả cho phép rõ |
| YawDD | Yawn; hard negatives talking/singing | Cao | Không: IEEE login, không bypass |
| Drive&Act | Hoạt động phụ/distraction action | Optional cho MVP | Direct HTTP có thể tải; rate thấp, không mirror |
| NTHU-DDD | Bổ sung night/active-IR/eyewear | Bổ sung có điều kiện | Không: ký thỏa thuận và được duyệt |
| Self-recorded | Camera domain, gaze calibration, edge cases | Bắt buộc | Do project kiểm soát, cần consent |

Không có bộ nào là ground truth hoàn hảo cho toàn hệ thống. Kết quả phải tách `eye`, `yawn`, `nod`, `drowsiness`, `gaze zone`, `distraction`; không tạo một accuracy chung bằng cách trộn ontology khác nhau.

## 2. Cách đọc trạng thái license

- **Verified:** nguồn chủ sở hữu ghi license/terms rõ.
- **Restricted:** có điều khoản phi thương mại/nghiên cứu/form/không phân phối.
- **Unclear:** có link tải nhưng không có license đủ rõ; phải hỏi chủ sở hữu trước use case ngoài đọc/đánh giá nội bộ.
- License source code, model weights, dataset và ảnh công bố là bốn thứ khác nhau.

Phase 0 **không tải dữ liệu** và không viết downloader vì chỉ thị hiện tại là “chưa code”. Script chỉ được tạo ở phase sử dụng dữ liệu, sau khi quyền truy cập đã được xác nhận.

## 3. DMD — Driver Monitoring Dataset

### Nguồn đã kiểm tra

- [Website chính thức](https://dmd.vicomtech.org/)
- [Repository Vicomtech](https://github.com/Vicomtech/DMD-Driver-Monitoring-Dataset)
- [Bài báo gốc](https://arxiv.org/abs/2008.12085)
- Cổng hiện hành: [Gaze & Hands](https://opendatasets.vicomtech.org/di21-dmd-dataset-gaze/8433939e), [Drowsiness](https://opendatasets.vicomtech.org/di21-dmd-dataset-drowsiness/99e2fbd7), [Distraction RGB](https://opendatasets.vicomtech.org/di21-dmd-dataset-distraction-rgb-ir/a268f10c)

Các URL trên hoạt động khi kiểm tra; cổng yêu cầu dữ liệu cần JavaScript/form.

### Nội dung và thay đổi quan trọng

Bài báo/bộ lịch sử mô tả 37 người, khoảng 41 giờ, ba camera (face/body/hands), RGB–IR–Depth, xe thật và simulator. **Bản công khai năm 2026 không còn giống toàn bộ corpus lịch sử**:

- chỉ RGB trong xe thật; simulator, IR và Depth đã bị loại khỏi public release;
- 14 subject ID công khai: `1, 5, 6, 7, 9, 10, 13, 14, 23, 28, 29, 33, 36, 37`;
- ba stream RGB: face, body, hands; video MP4;
- annotation OpenLABEL/VCD cho distraction/fatigue/gaze/head pose theo phạm vi từng gói.

Website lịch sử liệt kê phone/texting, drinking, passenger conversation, reaching, radio, hair/makeup; gaze road/window/mirror/radio/lap; yawning/microsleep/sleepy-driving; face/eye/body landmarks và hand/object. Danh sách đó **không chứng minh** mỗi nhãn đều đầy đủ trong mọi package 2026. Sau khi được cấp quyền phải inventory file/label thực tế trước khi viết loader.

### Dung lượng, license và truy cập

- “Khoảng 25 TB” là raw corpus lịch sử, không phải dung lượng tải RGB-14-subject hiện hành.
- Nguồn chính thức chưa công bố tổng dung lượng package hiện hành; ghi `unknown`, không suy ra.
- License: **CC BY-NC-ND 4.0**, thêm điều kiện từ 18 tuổi và academic use trên trang yêu cầu.
- NoDerivatives cho phép một số xử lý nội bộ nhưng hạn chế chia sẻ bản đã biến đổi; không phát hành lại clips/frames/annotations/derived bundles khi chưa xác nhận. Việc phân phối model weights học từ dữ liệu cũng cần legal/license review nếu điều khoản chưa rõ.

Quy trình: chọn portal → điền email/tên/tổ chức → chấp nhận terms/privacy → chờ link/hướng dẫn qua email. Không crawler, không reverse-engineer form, không tự gọi API ẩn.

### Dùng trong project

- Ưu: domain sát xe thật, nhiều view, temporal activity/gaze.
- Nhược: RGB-only public release, 14 người, tài liệu cũ dễ gây nhầm, license NC-ND.
- Module: face stream cho gaze-zone/distraction; fatigue/yawn chỉ sau annotation audit.
- Split: group theo 14 subject ID; không dùng random frame split.

## 4. UTA-RLDD — Real-Life Drowsiness Dataset

### Nguồn

- [Website tác giả](https://sites.google.com/view/utarldd/home)
- [Google Drive chính thức](https://drive.google.com/drive/folders/1d_QwgpMXnLY_FmLYXDn7TLcw0D-svXEl)
- [Bài báo CVPR Workshops 2019](https://openaccess.thecvf.com/content_CVPRW_2019/papers/AMFG/Ghoddoosian_A_Realistic_Dataset_and_Baseline_Temporal_Model_for_Early_Drowsiness_CVPRW_2019_paper.pdf)

Website và Drive hoạt động. Bài báo có lỗi đánh máy trong URL cũ; dùng `utarldd`, không `utarlld`.

### Nội dung

- 60 người khỏe mạnh, 180 video RGB, khoảng 30 giờ.
- Mỗi người có ba video khoảng 10 phút: alert=`0`, low vigilant=`5`, drowsy=`10`.
- Nhãn video do người tham gia tự báo dựa trên Karolinska Sleepiness Scale.
- 51 nam, 9 nữ; tuổi 20–59, trung bình 25; nhiều sắc tộc.
- 21/180 video có kính; 72/180 có nhiều râu.
- Tự quay bằng điện thoại/webcam, nhiều background/góc/resolution, dưới 30 FPS.
- Năm fold, mỗi fold 12 subject; nguồn khuyến nghị 5-fold cross-validation theo subject.
- Tổng dung lượng công bố: **111.3 GB**.
- Chỉ 36/60 người đồng ý dùng ảnh mặt trong publication; không tiết lộ danh tính.

### License/truy cập

Không thấy license chuẩn hoặc Terms of Use đầy đủ trên nguồn tác giả. Yêu cầu citation/quy tắc publication không thay thế license. Một bản sao Kaggle tự ghi CC0 nhưng nói không do tác giả upload; **không dùng CC0 đó làm license gốc**.

Drive công khai không có form UTA, nhưng có thể yêu cầu Google login/quota. Tác giả không nói rõ cho phép bulk/script download. Cho tới khi được làm rõ:

- tải thủ công bằng Drive hoặc API Drive chính thức dưới tài khoản được phép;
- không phát hành downloader công khai;
- không mirror/re-host;
- hỏi tác giả nếu định train/phân phối model hoặc dùng ngoài nghiên cứu nội bộ.

### Dùng trong project

- Ưu: chuỗi dài, ba mức, protocol subject-independent sẵn.
- Nhược: không trong xe; nhãn self-report áp toàn video; không có onset/offset blink/yawn/nod.
- Module: fusion `NORMAL/WARNING/DROWSY` ở mức video/segment phù hợp.
- Không được “nội suy” nhãn video thành ground truth từng frame/event.

## 5. YawDD — Yawning Detection Dataset

### Nguồn

- [DOI/IEEE DataPort](https://doi.org/10.21227/e1qm-hb90)
- [Metadata DataCite](https://api.datacite.org/dois/10.21227/e1qm-hb90)
- [Bài báo gốc](https://doi.org/10.1145/2557642.2563678)

DOI hoạt động và chuyển tới IEEE DataPort; trang ghi cập nhật 2026-07-29.

### Nội dung

- Hai phần, số công bố hiện hành: **351 video**.
- 322 video camera dưới rear-view mirror; mỗi người có 3–4 clip như silent, talking/singing, yawning.
- 29 video camera trên dashboard; mỗi video chứa các hành vi trên.
- Bài báo báo 107 volunteer (57 nam, 50 nữ); không đủ bằng chứng 29 người của phần dashboard là tập con hay người riêng.
- Xe đỗ; yawn diễn; ban ngày tới hoàng hôn.
- RGB AVI, 640×480, 30 FPS, không audio; clip phần đầu thường 15–40 s.
- Không có temporal labels theo IEEE DataPort.
- `YawDD.rar.gz` 4.94 GB; participant-information 328.64 KB.
- Participant file quy định video nào được phép trích ảnh công khai.

Bất nhất phải giữ trong audit: một câu của paper ghi 342 video, trong khi cùng paper và DataPort cho `322+29=351`.

### License/truy cập

DataCite hiện ghi **CC BY 4.0**. Tuy nhiên consent/paper gốc nói non-commercial research và giới hạn publication image; project áp dụng điều kiện chặt hơn khi các nguồn xung đột. Hỏi tác giả/IEEE nếu có thương mại, redistribution hoặc công bố ảnh.

Tải cần tài khoản IEEE miễn phí; không cần IEEE membership. Dùng giao diện chính thức, không bypass login, không coi endpoint ẩn là quyền tự động tải.

### Dùng trong project

- Ưu: hard negatives talking/singing trực tiếp chống luật sai “mouth open = yawn”; nhiều người/kính/kính râm/ánh sáng.
- Nhược: yawn diễn, xe đứng yên, không night/IR, không ranh giới event.
- Module: MAR/mouth/yawn; phải gán `start/end` trước event evaluation.
- Không dùng yawn làm ground truth drowsiness.

## 6. Drive&Act

### Nguồn

- [Website/download chính thức](https://www.driveandact.com/)
- [Bài báo ICCV 2019](https://openaccess.thecvf.com/content_ICCV_2019/html/Martin_DriveAct_A_Multi-Modal_Dataset_for_Fine-Grained_Driver_Behavior_Recognition_in_ICCV_2019_paper.html)
- [DOI](https://doi.org/10.1109/ICCV.2019.00289)

Website và 11 archive direct HTTP hoạt động; hỗ trợ byte-range/resume. Website nói từ 2021-05-27 không cần login/xin phép.

### Nội dung

- 15 người: 4 nữ, 11 nam.
- 29 session dài, 12 giờ, hơn 9.6 triệu frame.
- Simulator Audi A3 tĩnh; manual, automated và takeover.
- Bài báo mô tả 6 view; RGB/NIR/Depth/Kinect IR, 3D pose/head pose và interior model.
- 83 label thủ công ba tầng: 12 task/scenario, 34 semantic activity và atomic action–object–location.
- Có driving mode, hands-on-wheel, takeover timestamps và simulator signals.
- Ba official split subject-independent; mỗi split 10 train / 2 validation / 3 test.

Website không ghi dung lượng tổng. `Content-Length` của 11 archive được kiểm tra ngày 2026-09-22:

| Nhóm | Dung lượng |
|---|---:|
| 5 NIR archives | 11.49 GB |
| Kinect Depth | 9.74 GB |
| Kinect RGB | 5.26 GB |
| Kinect IR | 0.58 GB |
| Activities + 3D pose + interior | 0.46 GB |
| Tổng | 27.52 GB (25.63 GiB) |

### License/truy cập

Website ghi “Copyright Fraunhofer IOSB” và “Usage for research only”, không có CC/SPDX/EULA chi tiết. Không suy diễn quyền thương mại hoặc redistribution.

Direct HTTP cho phép downloader có resume về mặt kỹ thuật. Vì không có tuyên bố bot riêng, downloader tương lai phải tải tuần tự/rate thấp, kiểm checksum nếu nguồn có, và không mirror.

### Bất nhất/giới hạn

- Landing page ghi 5 views, paper/cấu trúc sensor ghi 6.
- Website ghi atomic `(6|17|14)`, paper ghi 5 action types.
- Intro nhắc head pose nhưng bảng download hiện không chỉ rõ archive head-pose độc lập; phải inventory trước khi phụ thuộc.
- Secondary activity không tự động có nghĩa `DISTRACTED`; distraction cần temporal/risk policy.

### Dùng trong project

Optional cho activity recognition. MVP nếu cần chỉ lấy `kinect_color.zip` + `iccv_activities_3s.zip`, không tải toàn bộ. Không dùng làm drowsiness/gaze-zone benchmark chính.

## 7. Bổ sung: NTHU Driver Drowsiness Detection Dataset

### Nguồn

- [Trang NTHU CV Lab](http://cv.cs.nthu.edu.tw/php/callforpaper/datasets/DDD/)
- [License Agreement](http://cv.cs.nthu.edu.tw/php/callforpaper/datasets/DDD/NTHU-DDD-LicenseAgreement.pdf)
- [Bài báo gốc](https://doi.org/10.1007/978-3-319-54526-4_9)

HTTP hoạt động nhưng HTTPS không kết nối khi kiểm tra. Không gửi dữ liệu nhạy cảm qua form HTTP; quy trình công bố là ký tài liệu rồi email.

### Nội dung

- 36 người, khoảng 9.5 giờ, simulator.
- Normal, yawning, slow blink, falling asleep, laughing và hành vi liên quan.
- `BareFace`, `Glasses`, `Sunglasses`, `Night-BareFace`, `Night-Glasses`.
- Active IR, AVI 640×480; night 15 FPS, còn lại 30 FPS.
- 18 người train; 18 người còn lại tạo 90 evaluation/test videos.
- EULA nói frame có drowsy/non-drowsy label. Các annotation stream mắt/đầu/miệng thường được nghiên cứu thứ cấp nhắc tới nhưng phải xác nhận gói thật sau cấp quyền.
- Không có dung lượng chính thức công bố.

### Điều khoản và truy cập

- Chỉ non-commercial research/educational use.
- Không chuyển cho bên thứ hai.
- Chỉ subject 010/021 được dùng ảnh trong academic publication theo agreement.
- Trích dẫn paper; NTHU có quyền chấm dứt access.
- Cần chữ ký department head/lab director, gửi tới email ghi trong agreement.

Không dùng bản mirror/Kaggle để né quy trình.

### Vai trò

Bổ sung night/active IR, eyewear, slow blink, yawn và head behavior. Giới hạn: simulator và hành vi diễn; không phải physiological drowsiness ground truth.

## 8. Dataset mapping theo task

| Task | Primary | Secondary/self | Không được suy diễn |
|---|---|---|---|
| Eye state/blink/closure | NTHU nếu annotation audit đạt; self-recorded event labels | YawDD/DMD quality tests | Video-level drowsy = eye closed frame |
| PERCLOS proxy | Self-recorded eyelid/eye-state timeline | NTHU nếu label đủ | UTA video label = PERCLOS GT |
| Yawn | YawDD | DMD/NTHU/self | Mouth open = yawn; yawn = drowsy |
| Head nod | Self-recorded | NTHU/DMD sau audit | Head down = nod |
| Drowsiness state | UTA-RLDD | NTHU + self simulated behavior | Simulated behavior = medical drowsiness |
| Gaze zone | DMD 2026 + self calibration | — | Head turned = distracted |
| Distraction event | DMD + self | Drive&Act activities | Secondary activity = unsafe distraction |
| IR/night robustness | NTHU | Pi NoIR self-recorded | RGB metric giữ nguyên dưới NIR |

## 9. Protocol tự quay an toàn và có đạo đức

### 9.1 Safety/consent

- Chỉ xe đỗ hoàn toàn với parking brake hoặc simulator; không chạy trên đường công cộng.
- Không gây thiếu ngủ, không dùng thuốc/chất gây buồn ngủ, không yêu cầu nhắm mắt khi điều khiển xe.
- Người tham gia từ 18 tuổi, consent bằng văn bản. Tách quyền tham gia, lưu video mặt, dùng sample image/publication.
- Cho phép rút consent/xóa theo policy đã thông báo.
- Dùng `subject_id` giả danh; không quay biển số/GPS/địa chỉ. Audio tắt mặc định.
- Dữ liệu gọi `SIMULATED_BEHAVIOR`; không gọi medical/physiological drowsiness.
- Nguồn 850 nm phải là thiết bị thương mại có tài liệu eye-safety; không tự tăng công suất.

### 9.2 Metadata bắt buộc

```text
dataset_id, subject_id, session_id, clip_id
camera_model, lens, camera_pose_id, resolution, nominal_fps, pixel_format
illumination_mode, ambient_light_notes, IR_device_id
eyewear, face_distance_band, seat_position_id
scenario, instructed_behavior, repetitions
consent_version, capture_date, raw_file_hash
```

Không đặt tên/ngày sinh/liên hệ cá nhân trong manifest kỹ thuật.

### 9.3 Session

1. Setup/consent/metadata; xe đứng yên.
2. Neutral calibration 1–2 phút: nhìn road reference, blink tự nhiên, miệng nghỉ, head neutral.
3. Gaze calibration: lần lượt `ROAD`, mirrors, dashboard, center display, down; có sample validation riêng.
4. Normal blocks: nhìn thẳng, blink, mirror checks ngắn, dashboard/display ngắn, nói chuyện.
5. Drowsiness-like blocks: đóng mắt có kiểm soát, slow/consecutive blink, yawn diễn, head down và nod cycle tách riêng.
6. Distraction blocks: nhìn trái/phải/down/display với short/long durations đã scripted.
7. Hard negatives: talking, laughing, mouth opening không yawn, face touch/occlusion, người khác vào frame.
8. Mixed continuous block 5–10 phút để temporal logic không dựa vào clip cắt đẹp.
9. Debrief và kiểm consent/retention.

Mỗi event scripted lặp 3–5 lần; random hóa thứ tự, cho nghỉ, dừng khi khó chịu. Đây là mục tiêu thu dữ liệu kỹ thuật, không phải cỡ mẫu chứng minh y khoa.

### 9.4 Edge-case matrix

Ưu tiên ít nhất hai session/người hoặc phân bố có chủ đích qua subjects:

- no glasses / clear glasses / reflective glasses;
- visible light / low light / approved NIR;
- front/side light;
- camera near/far, centered/offset, stable/vibration replay;
- small eye, facial hair, mask/hand occlusion;
- face near frame edge, large head rotation;
- autofocus/exposure transitions;
- second person entering frame.

Không cần mỗi subject làm mọi ô; manifest phải cho biết ô nào thực sự có.

## 10. Annotation protocol

### 10.1 Schema event

| Field | Ý nghĩa |
|---|---|
| `subject_id/session_id/source_video` | truy vết group |
| `start_time_s/end_time_s` | ranh giới theo timestamp video |
| `label` | ontology versioned |
| `behavior_origin` | spontaneous / instructed / unknown |
| `confidence` | annotator certainty theo rubric, không phải model confidence |
| `occlusion/visibility` | điều kiện quan sát |
| `annotator_id` | ID ẩn danh |
| `notes` | ambiguity/failure |

### 10.2 Quy tắc

- Event test được hai người gán độc lập; adjudicate disagreement trước khi freeze.
- `talking`, `laughing`, `mouth_open_other` là negative riêng cho yawn.
- `head_down_hold` khác `nod_cycle`.
- Gaze zone có `TRANSITION` hoặc `OTHER/UNKNOWN`, không ép mọi frame vào một zone.
- Không gán frame-level alert/low/drowsy từ label video UTA.
- Lưu raw annotation và derived labels; preprocessing không ghi đè raw.

## 11. Subject-independent split

### 11.1 Quy tắc tuyệt đối

Gán split theo subject **trước** khi cắt clip/frame/augmentation:

\[
Subjects_{train} \cap Subjects_{validation} = \varnothing,
Subjects_{train} \cap Subjects_{test} = \varnothing,
Subjects_{validation} \cap Subjects_{test} = \varnothing
\]

Tất cả session, derivative clips và augmented samples của một người ở cùng partition. Prefix ID bằng dataset để tránh hai dataset cùng có `subject_01`.

### 11.2 Theo dataset

- UTA-RLDD: giữ đúng 5 fold × 12 subject.
- Drive&Act: giữ ba split official 10/2/3.
- YawDD: parse participant information, group mọi clip theo person.
- DMD 2026: grouped folds từ 14 ID; không random file/frame split của tooling cũ nếu nó làm leakage.
- NTHU-DDD: giữ official identity split.
- Self-recorded: nếu ≥15 người, candidate 60/20/20 theo người hoặc grouped 5-fold; nếu ít hơn, grouped 5-fold/leave-one-subject-out và báo uncertainty.

Calibration của test subject chỉ dùng neutral/guided calibration segment đã pre-register; không dùng event labels test để chỉnh threshold. Báo cáo `zero-shot` và `calibrated` riêng.

## 12. Data leakage audit

Trước evaluation, script audit tương lai phải kiểm:

- không giao subject giữa split;
- không giao source video/hash hoặc near-duplicate derivative;
- model/threshold không được chọn bằng test;
- normalization/calibration population chỉ fit trên train, trừ calibration cá nhân được protocol cho phép;
- frame trích từ một event không rơi vào nhiều split;
- background/session dễ nhận diện không bị lặp bất hợp lý;
- public pretrained model có thể đã thấy dataset hay không; nếu không biết phải ghi limitation.

## 13. Cấu trúc dữ liệu tương lai

```text
data/
├── README.md
├── manifests/
│   ├── sources.csv
│   ├── subjects.csv
│   ├── sessions.csv
│   ├── splits_v1.csv
│   └── licenses/       # chỉ lưu terms nếu được phép
├── raw/<dataset>/      # read-only, gitignored
├── interim/<dataset>/  # extracted/converted, gitignored
├── processed/<task>/   # normalized labels/crops, gitignored
└── self_recorded/
```

Mỗi source manifest cần URL, ngày kiểm tra, license/terms URL, access approval, archive size, checksum và extraction tool version.

## 14. Download/preprocessing gate

Trước khi viết hoặc chạy downloader:

1. đọc lại license/terms tại thời điểm tải;
2. lưu bằng chứng approval mà không commit credential;
3. xác nhận storage/checksum;
4. không tự submit form/login;
5. rate-limit/resume theo nguồn cho phép;
6. raw archive read-only;
7. inventory subjects/files/labels;
8. tạo split manifest trước extraction dùng cho training;
9. viết preprocessing idempotent và log lỗi;
10. không commit dataset hoặc sample không có quyền phân phối.

## 15. Những điều Phase 0 chưa làm

- Không download dataset.
- Không chấp nhận terms thay người dùng.
- Không tạo tài khoản hoặc gửi form/email.
- Không viết downloader/preprocessor.
- Không công bố metric trên bất kỳ dataset nào.
- Không gọi behavior simulation là drowsiness thật.
