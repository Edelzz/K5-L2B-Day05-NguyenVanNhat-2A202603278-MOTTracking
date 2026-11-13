# Báo cáo cá nhân — HoVaTen-MSSV

Đổi tên file theo quy tắc `MSSV_HoTen.md`. Ví dụ: `20241234_NguyenVanAn.md`.

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: **NGUYỄN VĂN NHẤT**
- MSSV: **2A202603278**
- Mã đề (A/B/C): DAY05-MOT17-09-B-2A202603278
- Email: nhatnvedelz@gmail.com
- Link repository: https://github.com/Edelzz/K5-L2B-Day05-NguyenVanNhat-2A202603278-MOTTracking.git
- Giờ bắt đầu: 16h30
- Giờ kết thúc: 17h45

## 1. Xem trước đoạn video (CP0)

Ghi **trước khi vẽ**, mỗi người một dòng.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---:|---:|---|---|---|
| P1 | 0 | 139 |  | 120 | Có mặt 0–119, 130–139; `outside` 120–129 |
| P2 | 0 | 148 |  |110 | Có mặt 0–109, 140–148; `outside` 110–139 |
| P3 | 0 | 109 |  |110  | Có mặt liên tục 0–109; sau đó không còn box |
| P4 | 0 | 149 |  |  | Có mặt liên tục 0–149 |
| P5 | 10 | 149 |  |  | Xuất hiện từ frame 10, có mặt liên tục đến 149 |

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.

| Mã | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---|---|---|---|---|---|
| P1 (MOT 1 / CVAT 0) | 13 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 130 | 130 | 10.0 | | |
| P2 (MOT 2 / CVAT 1) | 7 | 0, 10, 20, 30, 40, 50, 140 | 119 | 5.9 | | |
| P3 (MOT 3 / CVAT 2) | 6 | 0, 10, 20, 30, 40, 50 | 110 | 5.5 | | |
| P4 (MOT 4 / CVAT 3) | 15 | 0, 10, 20, 30, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 150 | 10.0 | | |
| P5 (MOT 5 / CVAT 4) | 15 | 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 140 | 10.7 | | |
| **Tổng** | **56** | — | **649** | **8.6** | | |

Keyframe / 100 frame của cả bài = tổng keyframe ÷ tổng số frame có mặt × 100 = 56 ÷ 649 × 100 = **8.6**.

Nhiều keyframe nhất: P4 và P5, cùng 15 keyframe (CVAT track 3 và 4). Lý do đặt nhiều keyframe không thể xác định chỉ từ file xuất.

Thời gian thực hiện và chỗ khó chưa có trong kết quả tự kiểm.

## 3. Đoạn bị che (CP2)

Kết quả xuất không có frame nào được đánh dấu `occluded=1`, nên không xác định được người bị che một phần từ số liệu này. Có hai khoảng `outside`:

| Mốc | Frame |
|---|---:|
| CVAT track 0 / MOT ID 1: mất hẳn (`outside`) | 120–129 |
| CVAT track 0 / MOT ID 1: hiện lại | 130 |
| CVAT track 1 / MOT ID 2: mất hẳn (`outside`) | 110–139 |
| CVAT track 1 / MOT ID 2: hiện lại | 140 |
| Bắt đầu bị che một phần / thấy rõ trở lại (`occluded`) | Không có cờ `occluded` trong file xuất |

- Thời gian `outside`: track 0 là 10 frame = 0.33 giây; track 1 là 30 frame = 1 giây (30 fps).
- File xuất giữ nguyên ID ở hai phía khoảng `outside`; không thể xác minh quyết định đó có đúng về ngoại hình, hướng và tốc độ nếu chỉ dựa vào số liệu.

Phần giải thích theo hình ảnh và ảnh chụp màn hình cần được bổ sung sau khi kiểm tra trên CVAT.

Ảnh chụp màn hình:

![Trước khi che]("...\report\individual\TruockhiChe.png")
 [Giữa đoạn che, thấy cờ trên panel object]  ("...\report\individual\TrongKhiChe.png")
![Sau khi hiện lại, cùng ID](("...\report\individual\XuatHienLai.png"))

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

Kết quả tự kiểm file có 0 lỗi và 0 cảnh báo; đây không phải kết quả của lượt review ID bằng mắt, nên bảng dưới cần điền sau khi thực hiện hai lượt review.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| | | |Đã review 2 lượt và không phát hiện lỗi | | |
| | | | | | |
| | | | | | |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| | | | | | | |

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

...

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `NguyenVanNhat_mot.zip` |
| Tên file CVAT for video 1.1 | `NguyenVanNhat_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | 5 |
| Frame `outside` không có dòng trong `gt/gt.txt` (đúng / sai) | Đúng |
| Job đã completed trên CVAT máy cá nhân | |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
Số frame in theo CVAT (bắt đầu từ 0). Trong gt.txt, frame_id = frame CVAT + 1.

=== File MOT 1.1: NguyenVanNhat_mot.zip ===
  Số track ID: 5   |   Tổng số box: 649
  [OK]        Đúng 5 track ID.

  Track | Frame có mặt | Số frame | Đoạn vắng (outside)
      1 |   0–139      |      130 | 120–129
      2 |   0–148      |      119 | 110–139
      3 |   0–109      |      110 | -
      4 |   0–149      |      150 | -
      5 |  10–149      |      140 | -


=== File CVAT for video 1.1: NguyenVanNhat_cvat_video.zip ===

  Track | Nhãn   | Frame thấy | Keyframe | KF/100 frame | Frame occluded | Lần bật outside
      0 | person |        130 |       13 |         10.0 |              0 |               2
              Track 0: keyframe ở frame [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 130]
      1 | person |        119 |        7 |          5.9 |              0 |               2
              Track 1: keyframe ở frame [0, 10, 20, 30, 40, 50, 140]
      2 | person |        110 |        6 |          5.5 |              0 |               1
              Track 2: keyframe ở frame [0, 10, 20, 30, 40, 50]
      3 | person |        150 |       15 |         10.0 |              0 |               0
              Track 3: keyframe ở frame [0, 10, 20, 30, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149]
      4 | person |        140 |       15 |         10.7 |              0 |               0
              Track 4: keyframe ở frame [10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149]

  Tổng: 56 keyframe / 649 frame có mặt = 8.6 keyframe / 100 frame
  [OK]        Đọc được 5 track từ annotations.xml.

=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 0
  Đạt. Dán phần tóm tắt này vào báo cáo mục 5.
```

## 6. Ba câu kết

1. **Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?**

   Có thể xem xét bổ sung keyframe ngay trước khi P1 chuyển sang `outside` (frame 119) và P2 chuyển sang `outside` (frame 109), để kiểm soát chuyển tiếp từ box cuối sang trạng thái vắng.

2. **Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?**

   Các trường hợp cần kiểm tra trực quan là P1 tái xuất hiện ở frame 130 sau 10 frame vắng và P2 tái xuất hiện ở frame 140 sau 30 frame vắng. File xuất hiện giữ cùng track ID

3. **Một lỗi ID có thể làm xe tự lái dự đoán sai chuyển động thế nào? Ảnh hưởng MOTA hay IDF1 nhiều hơn?**

   Ví dụ giả định: nếu xảy ra `id_switch` giữa hai người, hệ thống có thể nối nhầm hai quỹ đạo, ước lượng vận tốc/hướng di chuyển sai và đưa ra quyết định tránh vật cản không phù hợp. IDF1 phản ánh trực tiếp chất lượng duy trì danh tính; MOTA cũng bị ảnh hưởng bởi số lần ID switch. 
## Bonus (nếu làm)

### B1 — Hai người đi sát

...

### B2 — So cách đặt keyframe

| Cách đặt | Số keyframe | Frame trôi nhất | Ghi chú |
|---|---:|---:|---|
| Đều mỗi 30 frame | | | |
| Theo chỗ đổi hướng | | | |

...

### B3 — So với tracker có sẵn

| Frame | Mã người | Tracker làm gì | Nhãn của bạn | Giải thích (đoán rồi sửa / ghép IoU / box score thấp / ngoại hình) |
|---:|---|---|---|---|
| | | | | |
| | | | | |

## 7. Tài liệu tham khảo và công cụ AI đã dùng

- GitHub Copilot: hỗ trợ điền các số liệu kiểm tra vào báo cáo từ kết quả tự kiểm.
