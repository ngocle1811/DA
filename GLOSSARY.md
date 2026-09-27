# Glossary — Bảng thuật ngữ sống

**Cập nhật:** 2026-09-22 — Phase 0  
Đây là nơi tra cứu nhanh. Các thuật ngữ quan trọng của Phase 0 được giải thích sâu sau bảng; report của từng phase vẫn phải nhắc lại ý nghĩa cần thiết, không chỉ trỏ về đây.

## 1. Bảng tra cứu

### 1.1 Hệ thống, AI và xử lý ảnh

| Thuật ngữ | Tên đầy đủ | Giải thích ngắn | Phase đầu tiên |
|---|---|---|---:|
| DMS | Driver Monitoring System | Hệ thống quan sát trạng thái/hành vi tài xế | 0 |
| CV | Computer Vision | Cho máy trích thông tin từ ảnh/video | 0 |
| AI | Artificial Intelligence | Nhóm kỹ thuật để máy thực hiện nhiệm vụ cần suy luận/nhận biết | 0 |
| ML | Machine Learning | Máy học quy luật từ dữ liệu thay vì chỉ viết luật tay | 0 |
| DL | Deep Learning | ML dùng mạng nhiều lớp học biểu diễn | 0 |
| Edge AI | Edge Artificial Intelligence | Chạy AI gần cảm biến, ở thiết bị biên | 0 |
| Pipeline | Processing Pipeline | Chuỗi bước xử lý có input/output rõ | 0 |
| Module | Software Module | Phần nhỏ có một trách nhiệm rõ | 0 |
| Perception | Perception Layer | Tầng trả lời camera đang quan sát thấy gì | 0 |
| Temporal processing | Temporal Processing | Xử lý diễn biến qua thời gian, không chỉ một frame | 0 |
| Decision layer | Decision Layer | Tầng biến chuỗi bằng chứng thành trạng thái/cảnh báo | 0 |
| Baseline | Baseline System | Phương án đầu làm mốc so sánh | 0 |
| Rule-based | Rule-based System | Hệ dùng luật do con người mô tả | 0 |
| Weighted score | Weighted Score | Tổng các tín hiệu sau khi nhân trọng số | 0 |
| State machine / FSM | Finite-State Machine | Máy trạng thái hữu hạn với luật chuyển trạng thái | 0 |
| Threshold | Decision Threshold | Mốc số dùng để đổi lớp/trạng thái | 0 |
| Heuristic | Heuristic Rule | Quy tắc kinh nghiệm hữu ích nhưng chưa phải định luật | 0 |
| Hysteresis | Hysteresis | Dùng điều kiện vào/ra khác nhau để tránh rung trạng thái | 0 |
| Calibration | Calibration | Thu dữ liệu tham chiếu để chỉnh theo camera/người/setup | 0 |
| Configuration | Configuration | Tham số bên ngoài code điều khiển hành vi hệ thống | 0 |
| Provenance | Data/Model Provenance | Nguồn gốc và lịch sử của dữ liệu/model/config | 0 |
| Ground truth | Ground Truth | Nhãn/giá trị tham chiếu dùng đánh giá | 0 |
| Quality gate | Quality Gate | Kiểm tra đầu vào đủ tin cậy trước khi quyết định | 0 |
| Unknown | Unknown State | Không đủ bằng chứng để kết luận trạng thái | 0 |
| Confidence | Confidence Score | Điểm tin cậy theo định nghĩa của model/backend; không mặc nhiên là xác suất đúng | 0 |

### 1.2 Ảnh, camera và hình học

| Thuật ngữ | Tên đầy đủ | Giải thích ngắn | Phase đầu tiên |
|---|---|---|---:|
| Pixel | Picture Element | Phần tử màu/sáng nhỏ nhất trong ảnh raster | 0 |
| Frame | Video Frame | Một ảnh tại một thời điểm trong video | 0 |
| Resolution | Image Resolution | Số pixel ngang × dọc, ví dụ 640×480 | 0 |
| RGB | Red-Green-Blue | Thứ tự ba kênh đỏ-lục-lam | 0 |
| BGR | Blue-Green-Red | Thứ tự kênh OpenCV thường dùng | 0 |
| YUV | Luma/Chrominance color model | Tách độ sáng khỏi thông tin màu | 0 |
| Timestamp | Timestamp | Mốc thời gian gắn với frame/observation | 0 |
| Monotonic clock | Monotonic Clock | Đồng hồ chỉ tăng, phù hợp đo duration | 0 |
| Buffer | Data Buffer | Vùng nhớ giữ dữ liệu tạm | 0 |
| Frame buffer | Frame Buffer | Buffer đủ chứa một hay nhiều ảnh | 0 |
| Resize | Image Resize | Đổi kích thước ảnh | 0 |
| Crop | Image Crop | Cắt lấy một vùng ảnh | 0 |
| ROI | Region of Interest | Vùng ảnh cần quan tâm | 0 |
| Bounding box | Bounding Box | Hình chữ nhật bao đối tượng | 0 |
| Coordinate | Coordinate | Số chỉ vị trí, thường là `(x,y)` | 0 |
| Normalized coordinate | Normalized Coordinate | Tọa độ theo tỉ lệ, thường 0–1 | 0 |
| Landmark | Facial Landmark | Điểm mốc hình học trên khuôn mặt | 0 |
| Euclidean distance | Euclidean Distance | Khoảng cách đường thẳng giữa hai điểm | 0 |
| Face detection | Face Detection | Tìm vị trí khuôn mặt trong ảnh | 0 |
| Face tracking | Face Tracking | Theo cùng khuôn mặt qua các frame | 0 |
| ISP | Image Signal Processor | Khối biến dữ liệu thô sensor thành ảnh dùng được | 0 |
| CMOS | Complementary Metal-Oxide-Semiconductor image sensor | Công nghệ cảm biến chuyển ánh sáng thành tín hiệu điện | 0 |
| CSI-2 | Camera Serial Interface 2 | Chuẩn truyền dữ liệu camera tốc độ cao | 0 |
| Autofocus | Automatic Focus | Tự điều chỉnh thấu kính để ảnh nét | 0 |
| PDAF | Phase Detection Autofocus | Lấy nét bằng sai lệch pha | 0 |
| Exposure | Exposure | Lượng ánh sáng sensor thu trong một lần chụp | 0 |
| Gain | Sensor/Analog Gain | Khuếch đại tín hiệu sensor, cũng khuếch đại nhiễu | 0 |
| IR | Infrared | Bức xạ hồng ngoại, ngoài vùng đỏ mắt người nhìn thấy | 0 |
| NIR | Near Infrared | Cận hồng ngoại, phần IR gần ánh sáng nhìn thấy | 0 |
| NoIR | No Infrared-cut Filter | Phiên bản camera không có kính chặn IR | 0 |
| IR-cut filter | Infrared-Cut Filter | Kính lọc chặn IR để màu visible tự nhiên hơn | 0 |
| IR illuminator | Infrared Illuminator | Nguồn chiếu IR để cảnh tối phản xạ ánh sáng về camera | 0 |
| Nanometre / nm | Nanometre | `10^-9` mét, đơn vị bước sóng; 850 nm là NIR | 0 |
| RAW10 | 10-bit Raw Sensor Format | Dữ liệu thô sensor với 10 bit mỗi sample trước xử lý ISP | 0 |
| HDR | High Dynamic Range | Kỹ thuật giữ chi tiết vùng rất sáng và rất tối | 0 |
| Back-illuminated sensor | Back-Side Illuminated Sensor | Sensor có cấu trúc giúp vùng nhạy sáng nhận photon hiệu quả hơn | 0 |

### 1.3 Tín hiệu tài xế

| Thuật ngữ | Tên đầy đủ | Giải thích ngắn | Phase đầu tiên |
|---|---|---|---:|
| Eye state | Eye State | Trạng thái mắt mở/nhắm/unknown | 0 |
| EAR | Eye Aspect Ratio | Tỉ lệ chiều dọc/chiều ngang của mắt từ landmark | 0 |
| Blink | Eye Blink Event | Chuỗi mở→đóng→mở trong thời gian ngắn | 0 |
| Eye closure duration | Eye Closure Duration | Thời gian mắt đóng liên tục | 0 |
| PERCLOS | Percentage of Eyelid Closure Over the Pupil Over Time | Phần trăm thời gian mí che đồng tử đến mức quy định | 0 |
| `perclos_proxy` | Binary Eye-Closure Time Ratio | Tỉ lệ thời gian eye-state nhị phân là closed trên thời gian hợp lệ | 0 |
| Sliding window | Sliding Time Window | Khoảng thời gian gần nhất dịch theo hiện tại | 0 |
| Mouth state | Mouth State | Trạng thái miệng mở/đóng/unknown | 0 |
| MAR | Mouth Aspect Ratio | Tỉ lệ hình học độ mở miệng | 0 |
| Yawn | Yawn Event | Mẫu mở miệng kéo dài có onset/sustain/offset | 0 |
| Head pose | Head Pose | Hướng/tư thế đầu so với camera | 0 |
| Yaw | Yaw Angle | Góc quay đầu trái/phải quanh trục dọc | 0 |
| Pitch | Pitch Angle | Góc ngẩng/cúi quanh trục ngang | 0 |
| Roll | Roll Angle | Góc nghiêng tai về vai | 0 |
| PnP | Perspective-n-Point | Tìm pose từ cặp điểm 3D–2D | 0 |
| Camera intrinsics | Camera Intrinsic Parameters | Tham số nội tại như focal length và principal point | 0 |
| Focal length | Focal Length | Tham số mô tả mức phóng chiếu của camera | 0 |
| Principal point | Principal Point | Điểm trục quang học cắt mặt phẳng ảnh | 0 |
| Rotation | Rotation | Sự đổi hướng | 0 |
| Translation | Translation | Sự dịch chuyển vị trí | 0 |
| Head nod | Head-Nod Event | Chu kỳ cúi rồi trở về, không phải một pose đơn lẻ | 0 |
| Gaze | Eye Gaze | Hướng nhìn của mắt/người | 0 |
| Iris | Iris | Mống mắt, vòng màu quanh đồng tử | 0 |
| Pupil | Pupil | Đồng tử, lỗ tối ở giữa mống mắt | 0 |
| Gaze vector | Gaze Direction Vector | Vector chỉ hướng nhìn trong không gian | 0 |
| Gaze angle | Gaze Angle | Góc mô tả hướng nhìn | 0 |
| Angular error | Angular Error | Góc giữa hướng dự đoán và hướng thật | 0 |
| Gaze zone | Gaze Zone | Vùng chức năng tài xế đang nhìn | 0 |
| Event | Temporal Event | Hành vi có thời điểm bắt đầu/kết thúc | 0 |

### 1.4 Model và triển khai

| Thuật ngữ | Tên đầy đủ | Giải thích ngắn | Phase đầu tiên |
|---|---|---|---:|
| Model | Mathematical/ML Model | Hàm biến input thành output theo tham số | 0 |
| Inference | Model Inference | Chạy model đã có để tạo dự đoán | 0 |
| Training | Model Training | Học tham số model từ dữ liệu | 0 |
| Pretrained model | Pretrained Model | Model đã học trên dữ liệu trước đó | 0 |
| Fine-tuning | Fine-tuning | Huấn luyện tiếp model pretrained trên dữ liệu đích | 0 |
| Training from scratch | Training from Scratch | Học model từ khởi tạo chưa huấn luyện | 0 |
| Loss | Training Loss | Hàm số phạt độ sai dùng để cập nhật model khi training | 0 |
| Validation loss | Validation Loss | Loss trên dữ liệu validation không dùng cập nhật weight | 0 |
| Learning curve | Learning Curve | Đồ thị metric/loss theo epoch hoặc lượng dữ liệu | 0 |
| Overfitting | Overfitting | Học quá sát train nên kém trên dữ liệu mới | 0 |
| Underfitting | Underfitting | Model chưa học đủ pattern ngay cả trên train | 0 |
| Tensor | Tensor | Mảng số nhiều chiều dùng trong model | 0 |
| Intermediate tensor | Intermediate Tensor | Tensor tạm giữa các layer/operator | 0 |
| Tensor arena | Tensor Arena | Vùng nhớ lập kế hoạch để chứa tensor khi inference | 0 |
| Operator | Neural-Network Operator | Phép toán trong graph, ví dụ convolution/add/resize | 0 |
| Kernel | Compute Kernel | Cài đặt mức thấp của một operator trên phần cứng | 0 |
| Runtime | Inference Runtime | Phần mềm nạp và thực thi model | 0 |
| Compiler | Compiler | Công cụ dịch source/model sang dạng chạy được | 0 |
| Model conversion | Model Conversion | Chuyển graph/weights sang format/runtime đích | 0 |
| ONNX | Open Neural Network Exchange | Format trao đổi graph model | 0 |
| TFLite | TensorFlow Lite | Runtime/format tối ưu cho thiết bị hạn chế hơn | 0 |
| Quantization | Quantization | Biểu diễn số bằng độ chính xác thấp hơn | 0 |
| FP32 | 32-bit Floating Point | Số dấu phẩy động 32 bit | 0 |
| FP16 | 16-bit Floating Point | Số dấu phẩy động 16 bit | 0 |
| INT8 | 8-bit Integer | Số nguyên 8 bit, thường dùng model quantized | 0 |
| Floating point | Floating-Point Number | Số có dấu chấm động, dải biểu diễn rộng | 0 |
| Fixed point | Fixed-Point Number | Số dùng vị trí dấu thập phân quy ước cố định | 0 |
| CPU | Central Processing Unit | Bộ xử lý đa dụng | 0 |
| GPU | Graphics Processing Unit | Bộ xử lý song song, ban đầu cho đồ họa | 0 |
| NPU | Neural Processing Unit | Bộ tăng tốc chuyên mạng neural | 0 |
| MCU | Microcontroller Unit | Vi điều khiển tích hợp CPU, memory, peripheral | 0 |
| RAM | Random Access Memory | Bộ nhớ làm việc đọc/ghi | 0 |
| SRAM | Static Random Access Memory | RAM nhanh, đắt diện tích, không cần refresh | 0 |
| PSRAM | Pseudo-Static RAM | RAM dung lượng lớn hơn SRAM nội nhưng chậm hơn | 0 |
| Flash | Flash Memory | Bộ nhớ không mất dữ liệu khi tắt điện | 0 |
| Cache | Cache Memory | Bộ nhớ nhỏ/nhanh lưu dữ liệu hay dùng | 0 |
| Memory bandwidth | Memory Bandwidth | Số byte có thể truyền mỗi giây | 0 |
| Stack | Call Stack | Vùng nhớ cho lời gọi hàm/biến cục bộ | 0 |
| Heap | Heap Memory | Vùng nhớ cấp phát động | 0 |
| DMA | Direct Memory Access | Phần cứng chuyển dữ liệu với ít CPU can thiệp | 0 |
| SIMD | Single Instruction, Multiple Data | Một lệnh xử lý nhiều phần tử dữ liệu | 0 |
| PIE/Xai | Processor Instruction Extensions / AI extension | Mở rộng lệnh trên ESP32 để tăng tốc DSP/AI | 0 |
| FPU | Floating-Point Unit | Khối phần cứng thực hiện số dấu phẩy động | 0 |
| DSP | Digital Signal Processing | Xử lý số cho tín hiệu/ảnh bằng phép toán lặp nhanh | 0 |
| MAC | Multiply–Accumulate | Nhân rồi cộng dồn, phép cơ bản của convolution | 0 |
| PPA | Pixel-Processing Accelerator | Khối P4 tăng tốc scale/rotate/blend pixel, không phải NPU | 0 |
| SoC | System on Chip | Chip tích hợp CPU, memory interface và peripherals | 0 |
| ISA | Instruction Set Architecture | Tập lệnh CPU hiểu được | 0 |
| Arm / RISC-V | CPU Instruction Architectures | Hai họ tập lệnh; Pi 5 dùng Arm, P4 dùng RISC-V | 0 |
| Firmware | Firmware | Phần mềm build/flash chạy trực tiếp trên thiết bị nhúng | 0 |
| RTOS | Real-Time Operating System | Hệ điều hành nhỏ quản lý task với yêu cầu timing | 0 |
| FreeRTOS | Free Real-Time Operating System | RTOS dùng trong ESP-IDF | 0 |

### 1.5 Dữ liệu và đánh giá

| Thuật ngữ | Tên đầy đủ | Giải thích ngắn | Phase đầu tiên |
|---|---|---|---:|
| Dataset | Dataset | Tập dữ liệu có cấu trúc dùng phát triển/đánh giá | 0 |
| Annotation | Data Annotation | Nhãn gắn với frame/event/video | 0 |
| Subject | Study Subject | Người tham gia tạo dữ liệu | 0 |
| Train split | Training Split | Phần dữ liệu dùng học/chọn tham số model | 0 |
| Validation split | Validation Split | Phần dùng chọn model/threshold, không báo kết quả cuối | 0 |
| Test split | Test Split | Phần khóa để đánh giá cuối | 0 |
| Subject-independent split | Subject-Independent Split | Không có cùng người ở train và test | 0 |
| Generalization | Generalization | Khả năng hoạt động trên dữ liệu/người chưa thấy | 0 |
| Data leakage | Data Leakage | Thông tin test lọt vào quá trình xây hệ thống | 0 |
| Domain shift | Domain Shift | Phân phối dữ liệu lúc dùng khác dữ liệu phát triển | 0 |
| Class imbalance | Class Imbalance | Số mẫu giữa lớp chênh lệch lớn | 0 |
| Confusion matrix | Confusion Matrix | Bảng đếm dự đoán so với nhãn thật | 0 |
| TP | True Positive | Cảnh báo đúng khi nguy hiểm thật | 0 |
| TN | True Negative | Không cảnh báo đúng khi an toàn thật | 0 |
| FP | False Positive | Cảnh báo sai khi không nguy hiểm | 0 |
| FN | False Negative | Bỏ sót nguy hiểm thật | 0 |
| Accuracy | Accuracy | Tỉ lệ mọi dự đoán đúng | 0 |
| Precision | Precision | Trong các cảnh báo, tỉ lệ đúng | 0 |
| Recall / Sensitivity | Recall / Sensitivity | Trong nguy hiểm thật, tỉ lệ phát hiện được | 0 |
| Specificity | Specificity | Trong trường hợp âm thật, tỉ lệ nhận đúng | 0 |
| F1-score | F1 Score | Trung bình điều hòa của Precision và Recall | 0 |
| Macro average | Macro Average | Tính metric từng lớp rồi trung bình đều | 0 |
| Micro average | Micro Average | Gộp các count của lớp rồi tính metric | 0 |
| MAE | Mean Absolute Error | Trung bình trị tuyệt đối sai số | 0 |
| Frame-level metric | Frame-Level Metric | Đánh giá từng frame | 0 |
| Event-level metric | Event-Level Metric | Đánh giá sự kiện trọn vẹn | 0 |
| IoU | Intersection over Union | Tỉ lệ giao/hợp của hai vùng hoặc hai khoảng thời gian | 0 |
| False alarms/hour | False Alarms per Hour | Số cảnh báo sai trên mỗi giờ video | 0 |
| Time-to-detect | Time to Detect | Trễ từ event thật bắt đầu đến lúc cảnh báo | 0 |
| Cross-validation | Cross-Validation | Đánh giá lặp qua nhiều cách chia train/validation | 0 |
| Fold | Cross-Validation Fold | Một nhóm dữ liệu trong protocol cross-validation | 0 |
| Ontology | Label Ontology | Danh sách nhãn và quan hệ/ý nghĩa chính thức giữa chúng | 0 |
| Metadata | Metadata | Dữ liệu mô tả dữ liệu khác, như subject/camera/light | 0 |
| Manifest | Data/Experiment Manifest | Danh sách máy đọc được mô tả file, split, hash, config | 0 |
| Hash / SHA-256 | Cryptographic Hash / Secure Hash Algorithm 256 | Dấu vân tay số để phát hiện file thay đổi | 0 |
| Checksum | Checksum | Giá trị kiểm tra tính toàn vẹn file; hash là một dạng mạnh | 0 |
| Idempotent | Idempotent Operation | Chạy lại cùng input/config cho cùng trạng thái output | 0 |
| Raw data | Raw Data | Dữ liệu gốc chưa biến đổi, được giữ bất biến | 0 |
| Derived data | Derived Data | Dữ liệu tạo từ raw qua preprocessing/annotation | 0 |

### 1.6 Benchmark và nền tảng

| Thuật ngữ | Tên đầy đủ | Giải thích ngắn | Phase đầu tiên |
|---|---|---|---:|
| Benchmark | Benchmark | Phép đo có protocol để so sánh tái lập | 0 |
| Profiling | Performance Profiling | Đo từng stage để tìm nơi tốn tài nguyên | 0 |
| Bottleneck | Performance Bottleneck | Stage giới hạn tốc độ/tài nguyên toàn hệ | 0 |
| FPS | Frames Per Second | Số frame xử lý mỗi giây | 0 |
| Latency | Latency | Thời gian một frame/event đi tới kết quả | 0 |
| Throughput | Throughput | Lượng công việc hoàn thành mỗi đơn vị thời gian | 0 |
| Percentile | Percentile | Mốc mà một phần trăm quan sát nằm dưới nó, ví dụ p95 | 0 |
| Cold start | Cold Start | Từ trạng thái chưa chạy tới output hợp lệ đầu tiên | 0 |
| Steady state | Steady State | Trạng thái chạy ổn định sau warm-up | 0 |
| RSS | Resident Set Size | RAM vật lý process đang giữ | 0 |
| Peak RAM | Peak RAM | RAM lớn nhất trong lần chạy | 0 |
| Power | Power | Tốc độ tiêu thụ năng lượng, đơn vị watt | 0 |
| Energy | Energy | Tổng năng lượng, đơn vị joule | 0 |
| Watt | Watt (W) | Một joule mỗi giây | 0 |
| Joule | Joule (J) | Đơn vị năng lượng | 0 |
| Millisecond | Millisecond (ms) | Một phần nghìn giây | 0 |
| MB / MiB | Megabyte / Mebibyte | 10^6 byte / 2^20 byte | 0 |
| Raspberry Pi 5 | Raspberry Pi 5 | Máy tính bo mạch đơn chạy Linux | 0 |
| ESP32-P4 | ESP32-P4 | MCU RISC-V cho multimedia/edge workloads | 0 |
| Raspberry Pi OS | Raspberry Pi Operating System | Hệ điều hành Linux chính thức cho Pi | 0 |
| ESP-IDF | Espressif IoT Development Framework | SDK/framework chính thức cho ESP32 | 0 |
| MediaPipe | MediaPipe | Framework/task runtime xử lý media và ML on-device | 0 |
| OpenCV | Open Source Computer Vision Library | Thư viện xử lý ảnh/thị giác máy tính | 0 |
| Picamera2 | Picamera2 | API Python camera chính thức trên libcamera cho Pi | 0 |
| libcamera | libcamera | Camera stack mã nguồn mở trên Linux | 0 |
| ESP-DL | Espressif Deep Learning | Thư viện/runtime model của Espressif | 0 |
| ESP-WHO | ESP-WHO | Nền tảng ví dụ image/face dựa trên ESP-DL | 0 |
| Open Model Zoo | OpenVINO Open Model Zoo | Bộ demo/tool/model metadata cho OpenVINO | 0 |
| L2CS-Net | L2CS-Net | Model học sâu dự đoán hai góc gaze | 0 |
| OS | Operating System | Hệ điều hành quản lý phần cứng/phần mềm | 0 |
| API | Application Programming Interface | Giao diện để phần mềm gọi chức năng | 0 |
| Framework | Software Framework | Khung tổ chức và runtime cho ứng dụng | 0 |
| Library | Software Library | Tập hàm/lớp để chương trình gọi | 0 |
| License | Software/Data License | Điều khoản pháp lý cho phép sử dụng/phân phối | 0 |

### 1.7 Versioning và tái lập

| Thuật ngữ | Tên đầy đủ | Giải thích ngắn | Phase đầu tiên |
|---|---|---|---:|
| Repository / repo | Source-Code Repository | Kho lưu source và lịch sử thay đổi | 0 |
| Commit | Version-Control Commit | Snapshot thay đổi có mã định danh | 0 |
| Branch | Version-Control Branch | Dòng phát triển có tên, thay đổi theo commit mới | 0 |
| Tag | Version-Control Tag | Nhãn cố định trỏ tới commit, thường dùng đánh version | 0 |
| Release | Software Release | Bản phát hành được maintainer công bố, có thể gắn tag/artifact | 0 |
| Semantic version | Semantic Versioning | Cách đặt `major.minor.patch` với ý nghĩa tương thích | 0 |
| Dependency | Software Dependency | Package/thành phần mà project cần | 0 |
| Dependency lock | Dependency Lock File | Danh sách exact version/hash đã giải quyết | 0 |
| Package registry | Package Registry | Dịch vụ phân phối package/version như PyPI/ESP Registry | 0 |
| PyPI | Python Package Index | Registry package Python | 0 |
| Wheel | Python Wheel | Gói Python dựng sẵn, thường phụ thuộc OS/CPU | 0 |
| APT | Advanced Package Tool | Trình quản lý package Debian/Raspberry Pi OS | 0 |
| Virtual environment / venv | Python Virtual Environment | Môi trường package Python cô lập | 0 |
| x86-64 | 64-bit x86 Architecture | Kiến trúc CPU thường gặp trên PC Windows/Linux | 0 |
| ARM64 / AArch64 | 64-bit Arm Architecture | Kiến trúc CPU 64 bit của Pi và nhiều thiết bị | 0 |
| ABI | Application Binary Interface | Quy ước nhị phân để binary/library tương tác | 0 |
| Reproducibility | Reproducibility | Khả năng người khác lặp lại cùng điều kiện/kết quả | 0 |
| Telemetry | Telemetry | Dữ liệu đo/log hệ thống khi chạy | 0 |
| Structured log | Structured Log | Log theo field/schema thay vì câu chữ tự do | 0 |

## 2. Phiếu giải thích sâu các khái niệm cốt lõi

### DMS — Driver Monitoring System

**Tên đầy đủ:** Driver Monitoring System  
**Tên tiếng Việt dễ hiểu:** hệ thống theo dõi tài xế

1. **Là gì?** Hệ thống dùng cảm biến và thuật toán để ước lượng trạng thái/hành vi liên quan việc lái xe.
2. **Trực giác:** một “người quan sát” chỉ nhìn bằng camera, nhưng phải thừa nhận khi không thấy rõ.
3. **Dùng ở đâu?** Toàn project; output là drowsiness và distraction.
4. **Input:** video tài xế, config và calibration.
5. **Output:** tín hiệu, event, state, cảnh báo và log.
6. **Tại sao cần?** Để phát hiện pattern có thể liên quan rủi ro.
7. **Nếu không có?** Không có pipeline tổng hợp; chỉ còn demo từng công thức.
8. **Công thức:** không có một công thức DMS duy nhất.
9. **Thuật toán:** capture → perception → temporal logic → decision → evaluation.
10. **Sơ đồ:** xem `ARCHITECTURE.md`.
11. **Gần giống:** ADAS quan sát đường/xe; DMS tập trung người lái.
12. **Vì sao chọn?** Đây là mục tiêu đồ án, nhưng giới hạn ở nguyên mẫu nghiên cứu.

### Computer Vision và Edge AI

**Tên đầy đủ:** Computer Vision; Edge Artificial Intelligence  
**Tên tiếng Việt dễ hiểu:** thị giác máy tính; AI chạy gần camera

1. **Là gì?** CV biến pixel thành thông tin; Edge AI chạy phép biến đổi đó trên PC/Pi/MCU tại chỗ thay vì gửi cloud.
2. **Trực giác:** CV “đọc” ảnh; edge nói “đọc ở đâu”.
3. **Dùng ở đâu?** Face, landmark, eye, mouth, pose, gaze.
4. **Input:** ảnh/video.
5. **Output:** vị trí, điểm, lớp hoặc số liên tục.
6. **Tại sao cần?** Camera chỉ tạo pixel, chưa tạo quyết định.
7. **Nếu không có?** Không thể tự động trích trạng thái tài xế.
8. **Công thức:** không có công thức duy nhất.
9. **Bước:** acquire → preprocess → infer/geometry → validate → timestamp.
10. **Sơ đồ:** `Camera → Pixel → Feature → Temporal Evidence`.
11. **Gần giống:** cloud AI; cloud có tài nguyên lớn nhưng tăng phụ thuộc mạng/privacy/latency.
12. **Vì sao chọn?** DMS cần hoạt động tại xe và giữ dữ liệu mặt cục bộ khi có thể.

### Pipeline và module

**Tên đầy đủ:** Processing Pipeline; Software Module  
**Tên tiếng Việt dễ hiểu:** dây chuyền xử lý; khối chức năng

1. Pipeline là chuỗi module; module là một khối có trách nhiệm hẹp.
2. Trực giác: như dây chuyền, mỗi trạm nhận một vật và bàn giao vật đã xử lý.
3. Dùng để tách camera, face, feature, temporal, alert, metric.
4. Input/output do contract định nghĩa.
5. Output mỗi stage phải kèm validity/timestamp.
6. Cần để test/thay backend/port từng phần.
7. Không tách sẽ thành file lớn, khó tìm lỗi và khó benchmark.
8. Không có công thức.
9. Thuật toán tổng: validate input → transform → validate output → emit telemetry.
10. `camera → face → landmark → feature → temporal → state`.
11. End-to-end model gộp nhiều bước nhưng khó diễn giải/port hơn.
12. Project chọn module để phục vụ học tập và P4 feasibility.

### Perception và temporal processing

**Tên đầy đủ:** Perception Layer; Temporal Processing  
**Tên tiếng Việt dễ hiểu:** tầng nhìn; xử lý theo thời gian

1. Perception mô tả một thời điểm; temporal processing kết nối nhiều thời điểm.
2. Một ảnh miệng mở giống một chữ cái; chuỗi mở-kéo dài-đóng mới giống một “từ” yawn.
3. Dùng ở mọi signal/event.
4. Input temporal là observations có timestamp.
5. Output là event/state cùng duration/evidence.
6. Cần để chống noise một frame và hiểu hành vi.
7. Không có nó sẽ sinh luật sai “một frame = nguy hiểm”.
8. Duration `Δt = t_end - t_start`, đơn vị giây.
9. Update state theo observation mới, hysteresis và timeout.
10. `observation(t0..tn) → event → state`.
11. RNN/Transformer cũng xử lý thời gian nhưng khó giải thích và cần dữ liệu hơn.
12. Baseline chọn state machine vì minh bạch.

### Calibration

**Tên đầy đủ:** System/User Calibration  
**Tên tiếng Việt dễ hiểu:** hiệu chỉnh theo setup/người

1. Thu mẫu tham chiếu để biến feature tương đối thành ý nghĩa trong setup hiện tại.
2. Giống chỉnh cân về số 0 trước khi cân vật.
3. Dùng cho mắt mở/nhắm, head neutral và gaze zones.
4. Input là sample đã hướng dẫn và metadata camera/ghế.
5. Output là baseline/range/classifier và calibration ID.
6. Cần vì hình học mắt, camera và ghế khác nhau.
7. Không có có thể tăng sai số hệ thống theo từng người.
8. Ví dụ chuẩn hóa: `z=(x-μ)/σ`; `μ` là trung bình baseline, `σ` là độ lệch chuẩn. Chỉ dùng nếu `σ` ổn định và khác 0.
9. Thu → lọc quality → fit → validate trên sample khác → lưu version → kiểm drift.
10. `guided samples → calibration artifact → live mapping`.
11. Population threshold dễ dùng hơn nhưng kém cá nhân hóa.
12. Chọn calibration cho gaze zone; threshold toàn dân vẫn là baseline so sánh.

### Landmark, ROI và bounding box

**Tên đầy đủ:** Facial Landmark; Region of Interest; Bounding Box  
**Tên tiếng Việt dễ hiểu:** điểm mốc; vùng quan tâm; hộp bao

1. Bbox định vị vùng mặt; ROI là phần ảnh được chọn; landmark là điểm đặc trưng bên trong.
2. Bbox như khung quanh ngôi nhà; landmark như vị trí cửa/sổ; ROI như phần muốn phóng to.
3. Dùng cho mắt, miệng, pose, gaze.
4. Input là frame hoặc face crop.
5. Output là rectangle và tọa độ điểm.
6. Cần để tính hình học và giảm vùng model phải xử lý.
7. Sai bbox/landmark kéo sai mọi tín hiệu sau.
8. Tọa độ chuẩn hóa đổi về pixel: `x_px=x_norm×width`, `y_px=y_norm×height`.
9. Detect → validate → crop/track → landmark → map về ảnh gốc.
10. `frame ⊃ bbox/ROI ⊃ landmarks`.
11. Segmentation cho mask chi tiết hơn nhưng nặng hơn.
12. Landmark là baseline dễ diễn giải.

### EAR và khoảng cách Euclid

**Tên đầy đủ:** Eye Aspect Ratio; Euclidean Distance  
**Tên tiếng Việt dễ hiểu:** tỉ lệ độ mở mắt; khoảng cách đường thẳng

1. EAR so độ cao mắt với độ rộng mắt.
2. Mắt khép làm khoảng dọc nhỏ, trong khi ngang thay đổi ít hơn.
3. Dùng cho eye state, blink và closure.
4. Input là sáu landmark quanh mắt.
5. Output là một số không đơn vị.
6. Cần một feature hình học nhẹ và tương đối ít phụ thuộc kích thước ảnh.
7. Không chuẩn hóa theo ngang, cùng một mắt ở gần camera cho số pixel lớn hơn.
8. `d=sqrt((x2-x1)^2+(y2-y1)^2)`; EAR đầy đủ và ví dụ nằm trong `ARCHITECTURE.md`.
9. Lấy hai khoảng dọc → cộng → chia hai lần khoảng ngang → kiểm quality.
10. `landmarks → distances → ratio → time series`.
11. Eye classifier học ảnh có thể chịu pose tốt hơn nhưng nặng và cần dữ liệu.
12. Chọn EAR làm baseline, không xem nó là ground truth.

### PERCLOS và sliding window

**Tên đầy đủ:** Percentage of Eyelid Closure Over the Pupil Over Time; Sliding Time Window  
**Tên tiếng Việt dễ hiểu:** tỉ lệ thời gian mí che mắt; cửa sổ thời gian trượt

1. PERCLOS đo đóng mắt tích lũy trong một khoảng; project ban đầu chỉ đo proxy eye-state nhị phân.
2. Một lần nhắm ngắn không đáng kể như mắt đóng nhiều trong cả phút.
3. Dùng cho nhánh drowsiness.
4. Input eye observations + timestamp + validity.
5. Output tỉ lệ 0–1 hoặc phần trăm và coverage.
6. Cần tổng hợp dài hạn hơn blink.
7. Không có sẽ bỏ qua xu hướng đóng mắt kéo dài/lặp lại.
8. `closed_valid_time / valid_time`; ví dụ 12/57=21.05% trong cửa sổ 60 s có 3 s unknown.
9. Thêm interval → loại interval hết hạn → cộng duration valid/closed → phát tỉ lệ + coverage.
10. `eye states → time window → ratio`.
11. Frame ratio đơn giản nhưng sai khi FPS thay đổi/drop.
12. Chọn tích phân theo thời gian vì deployment không đảm bảo FPS cố định.

### Head pose, PnP, yaw/pitch/roll

**Tên đầy đủ:** Head Pose; Perspective-n-Point; Yaw/Pitch/Roll  
**Tên tiếng Việt dễ hiểu:** hướng đầu; tìm pose từ điểm 3D–2D; ba góc quay

1. PnP ước lượng rotation/translation của mô hình 3D từ landmark 2D và camera intrinsics.
2. Biết hình dạng tham chiếu và vị trí nó xuất hiện trên ảnh giúp suy ra nó quay thế nào.
3. Dùng cho nod và gaze/distraction.
4. Input 3D points, 2D points, camera matrix, distortion.
5. Output rotation/translation, sau đó đổi thành góc theo convention đã ghi.
6. Cần tách quay đầu khỏi chuyển động điểm đơn lẻ.
7. Không có pose, gaze zone chỉ dựa iris dễ sai khi quay đầu.
8. Phép chiếu khái niệm `s·p = A[R|t]P`; `P` điểm 3D, `p` điểm ảnh, `A` camera matrix, `R/t` rotation/translation, `s` scale chiếu.
9. Calibrate camera → chọn correspondence → solve → reprojection check → đổi góc → smooth.
10. `3D face + 2D landmarks + intrinsics → pose`.
11. Pose-regression model bỏ explicit geometry nhưng cần data/model.
12. PnP là baseline dễ kiểm tra; P4 có thể cần solver khác.

### Gaze, gaze vector và angular error

**Tên đầy đủ:** Eye Gaze; Gaze Direction Vector; Angular Error  
**Tên tiếng Việt dễ hiểu:** hướng nhìn; mũi tên hướng nhìn; sai số góc

1. Gaze là hướng mắt; vector gaze biểu diễn hướng; angular error so hai hướng.
2. Hai mũi tên càng lệch, góc giữa chúng càng lớn.
3. Dùng cho distraction/gaze zones.
4. Input mắt/iris/head pose hoặc hai vector dự đoán/thật.
5. Output zone hoặc góc sai số degree.
6. Cần vì head pose một mình không biết mắt liếc.
7. Thiếu gaze làm mirror/dashboard/road dễ lẫn.
8. `θ=acos((g_pred·g_true)/(||g_pred||·||g_true||))`; đổi radian sang degree bằng `θ_deg=θ_rad×180/π`.
9. Normalize vectors → dot product → clamp [-1,1] → arccos → degrees.
10. `eye+head → gaze → calibrated zone`.
11. Point-of-regard chi tiết hơn zone nhưng khó hơn nhiều.
12. MVP chọn coarse zones; deep angular gaze là optional.

### Benchmark, FPS, latency và throughput

**Tên đầy đủ:** Benchmark; Frames Per Second; Latency; Throughput  
**Tên tiếng Việt dễ hiểu:** phép đo chuẩn; frame/giây; độ trễ; năng suất xử lý

1. Benchmark là protocol đo; FPS/throughput đo lượng hoàn thành; latency đo thời gian một đơn vị.
2. Quầy có thể phục vụ nhiều khách/phút nhưng một khách vẫn chờ lâu.
3. Dùng mọi phase deployment.
4. Input workload, config, thiết bị, timestamps.
5. Output phân phối thời gian/tốc độ/tài nguyên.
6. Cần để biết bottleneck và so công bằng.
7. Không có dễ tối ưu mù hoặc nhầm camera FPS với inference FPS.
8. `FPS=processed_frames/elapsed_seconds`; latency ms=`Δt_seconds×1000`.
9. Khóa manifest → warm-up → chạy lặp → log raw → tính percentile → công bố điều kiện.
10. `workload + protocol → measurements → comparison`.
11. Average che tail; p95/p99 cho thấy frame chậm.
12. Project báo cả throughput, latency và dropped frames.

### Confusion matrix và các metric phân loại

**Tên đầy đủ:** Confusion Matrix; Accuracy; Precision; Recall; Specificity; F1 Score  
**Tên tiếng Việt dễ hiểu:** bảng đúng/sai và các tỉ lệ rút ra từ bảng

1. TP/TN/FP/FN đếm bốn kiểu kết quả nhị phân.
2. Với drowsiness: TP cảnh báo đúng, FP cảnh báo nhầm, FN bỏ sót, TN yên lặng đúng.
3. Dùng đánh giá eye state, alarm và từng class one-vs-rest.
4. Input dự đoán + ground truth cùng đơn vị đánh giá.
5. Output các count và tỉ lệ.
6. Cần vì mỗi loại lỗi có hậu quả khác.
7. Accuracy đơn độc gây hiểu nhầm khi phần lớn frame là normal.
8. `Accuracy=(TP+TN)/all`; `Precision=TP/(TP+FP)`; `Recall=TP/(TP+FN)`; `Specificity=TN/(TN+FP)`; `F1=2PR/(P+R)`.
9. Chốt positive class → align sample/event → đếm → tính cùng zero-division policy.
10. `labels + predictions → matrix → metrics`.
11. Macro cho mỗi lớp trọng lượng như nhau; micro ưu tiên lớp nhiều mẫu.
12. Project báo confusion matrix, per-class và event metric; không chỉ Accuracy.

**Ví dụ:** TP=18, FP=2, FN=3, TN=77. Accuracy=95%, Precision=90%, Recall≈85.7%, Specificity≈97.5%, F1≈87.8%. Dù Accuracy cao, ba sự kiện nguy hiểm vẫn bị bỏ sót nên phải nhìn Recall/FN.

### Dataset, subject-independent split và data leakage

**Tên đầy đủ:** Dataset; Subject-Independent Split; Data Leakage  
**Tên tiếng Việt dễ hiểu:** tập dữ liệu; chia tách người; rò rỉ thông tin test

1. Split độc lập subject giữ toàn bộ phiên của một người trong đúng một split; leakage xảy ra khi test ảnh hưởng development.
2. Nếu model thấy cùng khuôn mặt trong train và test, nó có thể “nhớ người” thay vì học tín hiệu.
3. Dùng khi chia public/self-recorded data.
4. Input manifest subject/session/video.
5. Output danh sách train/validation/test không giao subject.
6. Cần để đo generalization sang tài xế mới.
7. Random frame split có thể cho metric giả cao.
8. Kiểm tra tập hợp: `Subjects_train ∩ Subjects_test = ∅`.
9. Group by subject → stratify ở mức group nếu có thể → khóa split → audit hashes.
10. `subjects → grouped split → frozen test`.
11. Session-independent yếu hơn nếu cùng người vẫn ở hai split.
12. Subject-independent là mặc định; ngoại lệ phải giải thích.

### CPU, MCU, RAM, SRAM, PSRAM và Flash

**Tên đầy đủ:** Central Processing Unit; Microcontroller Unit; Random/Static/Pseudo-Static RAM; Flash Memory  
**Tên tiếng Việt dễ hiểu:** bộ xử lý; vi điều khiển; các loại bộ nhớ làm việc/lưu trữ

1. Pi là máy tính Linux quanh CPU; P4 là MCU tích hợp tài nguyên chặt. SRAM nhanh/ít, PSRAM lớn/chậm hơn, Flash lưu firmware/model.
2. Giống bàn làm việc: SRAM là mặt bàn gần tay, PSRAM là bàn phụ, Flash là tủ hồ sơ.
3. Dùng để lập ngân sách frame/model/tensor/task.
4. Input là dữ liệu/chỉ thị cần lưu/xử lý.
5. Output là phép tính và dữ liệu trung gian.
6. Cần hiểu peak working memory chứ không chỉ file model.
7. Thiếu memory gây allocation fail/crash hoặc copy chậm.
8. Frame bytes=`height×width×channels×bytes_per_channel`; 1920×1080 RGB8 ≈5.93 MiB.
9. Lập inventory buffer → lifetime → đặt internal/external → reuse → đo peak/largest block.
10. `Flash → load → RAM/PSRAM → CPU/operator`.
11. NPU là accelerator riêng; ESP32-P4 có instruction extension, không nên tự gọi là NPU.
12. Pi full pipeline trước; P4 thiết kế lại memory-aware.

### Quantization, FP32 và INT8

**Tên đầy đủ:** Model Quantization; 32-bit Floating Point; 8-bit Integer  
**Tên tiếng Việt dễ hiểu:** giảm độ chính xác biểu diễn số; số thực 32 bit; số nguyên 8 bit

1. Quantization ánh xạ số thực sang tập mức rời rạc nhỏ hơn.
2. Thay thước rất mịn bằng thước ít vạch: nhẹ/nhanh hơn nhưng làm tròn nhiều hơn.
3. Dùng khi tối ưu Pi/P4 sau baseline.
4. Input weights/activations FP và calibration/training data.
5. Output model/tensor quantized và scale/zero-point hoặc scheme tương ứng.
6. INT8 thường dùng 1 byte thay 4 byte FP32 và tận dụng kernel integer.
7. Không có có thể vượt RAM/latency P4; làm sai có thể giảm accuracy.
8. Dạng affine thường gặp: `real≈scale×(q-zero_point)`; ESP-DL có chiến lược riêng phải theo tài liệu version dùng.
9. Chọn data đại diện → quantize → kiểm operator → đo accuracy/memory/latency before-after.
10. `FP model + calibration → INT8 model → validate`.
11. FP16 là trung gian; fixed-point thủ công khác quantization graph tự động.
12. Không quantize mù; Phase 18 bắt buộc bảng trade-off.

### Model, training, inference và fine-tuning

**Tên đầy đủ:** Machine-Learning Model; Training; Inference; Fine-tuning  
**Tên tiếng Việt dễ hiểu:** mô hình; quá trình học; quá trình dự đoán; học tiếp model có sẵn

1. **Là gì?** Model là hàm có tham số. Training điều chỉnh tham số bằng dữ liệu; inference giữ tham số cố định để dự đoán; fine-tuning là training tiếp pretrained model trên miền đích.
2. **Trực giác:** training giống học từ bài tập; inference giống làm bài; fine-tuning giống học thêm chuyên ngành. Training from scratch bắt đầu từ tham số chưa học.
3. **Dùng ở đâu?** Face/landmark backend có model pretrained; Phase 13/18 có thể train/fine-tune/quantize nếu có lý do.
4. **Input:** training nhận samples, labels, loss và optimizer; inference nhận sample + weights đã khóa.
5. **Output:** training tạo weights/checkpoint/curves; inference tạo dự đoán.
6. **Tại sao cần?** Một số perception pattern khó mô tả hoàn toàn bằng luật tay.
7. **Nếu không có?** Chỉ dùng geometry/rules; có thể nhẹ nhưng kém robust trong điều kiện khó.
8. **Công thức khái niệm:** training tìm `w* = argmin_w L(w; data_train)`. `w` là weights; `L` là loss. Validation loss đo bằng `w` hiện tại trên validation nhưng không dùng sample đó để cập nhật `w`.
9. **Bước:** chọn data/split → train → chọn bằng validation → khóa → test một lần → deploy benchmark.
10. **Sơ đồ:** `train data → update weights → validation → frozen model → test/inference`.
11. **Phương pháp tương tự:** fine-tuning cần ít dữ liệu hơn scratch nhưng có thể giữ bias của pretraining; rule-based không học weights.
12. **Vì sao project chọn gì?** Dùng pretrained perception để có baseline; ML fusion/fine-tuning chỉ sau khi rule baseline và dataset audit tồn tại.

`Loss` thấp không tự động nghĩa sản phẩm tốt: model có thể overfit, dữ liệu lệch miền, alarm nhiều hoặc quá chậm. Nếu kiến trúc/input/precision không đổi, fine-tuning thường **không làm inference nhanh hơn** và model size thường không đổi; vẫn phải benchmark accuracy/generalization/latency/model size trước–sau.

### IR, Near-IR, NoIR và IR-cut filter

**Tên đầy đủ:** Infrared; Near Infrared; No Infrared-cut; Infrared-cut Filter  
**Tên tiếng Việt dễ hiểu:** hồng ngoại; cận hồng ngoại; camera không có kính chặn IR

1. IR nằm ngoài ánh sáng đỏ nhìn thấy; near-IR nằm gần vùng nhìn thấy. IR-cut chặn phần này để màu ban ngày tự nhiên hơn; NoIR bỏ filter đó.
2. Mắt người khó thấy nhưng sensor có thể nhận ánh sáng phản xạ từ nguồn 850 nm.
3. Dùng cho cabin tối với Camera Module 3 NoIR.
4. Input là photon visible/NIR phản xạ từ cảnh.
5. Output là tín hiệu sensor/ảnh; không phải nhiệt độ.
6. Cần NoIR + illuminator vì không có photon thì camera vẫn tối.
7. Camera thường + IR-cut sẽ giảm độ nhạy với nguồn NIR.
8. `850 nm = 850×10^-9 m`; đây là bước sóng, không phải công suất.
9. Chọn nguồn có tài liệu an toàn → bố trí → đo exposure/reflection → ghi metadata → đánh giá model riêng.
10. `IR illuminator → mặt → phản xạ → NoIR sensor`.
11. Thermal camera đo bức xạ nhiệt dải khác; NoIR không phải thermal.
12. NoIR phù hợp nghiên cứu thiếu sáng nhưng cần xử lý màu, kính phản xạ và an toàn mắt.

## 3. Quy tắc cập nhật

- Thuật ngữ mới phải vào bảng ở cùng phase xuất hiện.
- Nếu có nhiều định nghĩa trong tài liệu, project phải ghi đúng biến thể đang dùng.
- Tên metric luôn đi kèm positive class, level (frame/event), unit và zero-division policy.
- Tên version/framework không thay cho giải thích chức năng.
