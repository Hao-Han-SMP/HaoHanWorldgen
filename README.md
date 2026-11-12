# HaoHanWorldgen

## 🌟 Giới thiệu

**HaoHanWorldgen** là plugin tạo thế giới Mặt Trăng (`haohan:lunar`) thuần Java dành cho máy chủ Minecraft HaoHanSMP chạy nền tảng **Purpur / Paper 1.21.11 (Java 21)**. 

Toàn bộ thế giới Mặt Trăng được xây dựng dựa trên Paper `ChunkGenerator` & `BiomeProvider` tùy chỉnh, mang lại khả năng sinh địa hình mượt mà, cấu hình linh hoạt qua file YAML và loại bỏ hoàn toàn các giới hạn giật lag của datapack thông thường.

### ✨ Tính năng nổi bật
* **Hệ thống tạo địa hình (Terrain Pipeline):**
  * **Biển Mặt Trăng (Maria):** Vùng trũng dung nham bazan bằng phẳng (độ cao ~35).
  * **Cao nguyên (Highlands):** Dãy núi anorthosite gồ ghề (độ cao ~68) kết hợp sóng terrain đa octave.
  * **Hố thiên thạch đa quy mô (Cellular/Worley Noise):** Micro (r=3-7), Small (r=8-16), Large (r=20-36 có vành nâng), Mega Basins (r=50-80) và Complex Craters (có đỉnh va chạm trung tâm).
  * **Núi lửa & Caldera:** Miệng núi lửa sụp và nón núi lửa rộng.
  * **Chống tạo gai (Anti-spike clamp):** Đảm bảo địa hình tự nhiên, không bị lỗi đỉnh gai dị dạng.
* **Xử lý bề mặt & Địa chất (Surface Pipeline):**
  * **Slope / Cliff Detection:** Tự động phát hiện vách đá dốc để làm lộ tầng đá nền (`Cobbled Deepslate`, `Tuff`), vùng phẳng phủ lớp bụi mịn regolith (`Concrete Powder`).
  * **Khe nứt sâu:** Vết nứt obsidian và crying obsidian ở các tầng sâu đáy hố (Y <= 18).
* **Biome Mặt Trăng:** Phân bổ mượt mà 7 biome đặc trưng (`lunar_maria`, `lunar_terrae`, `lunar_craters`, `lunar_bright_patches`, `lunar_crystal_craters`, `lunar_giant_crystals`, `lunar_giant_crystal_outskirts`).
* **Khoáng sản & Cấu trúc:** Sinh quặng đặc thù (Anorthosite, Ilmenite, Basalt), cụm thạch anh (Amethyst Spire), tảng đá rơi (ejecta boulders) và nạp cấu trúc `.nbt` (trạm dừng chân, trạm vũ trụ, căn cứ bỏ hoang,...).

---

## 🛠️ Yêu cầu môi trường

* **Java:** JDK 21 trở lên.
* **Server:** [Purpur](https://purpurmc.org/) hoặc [Paper](https://papermc.io/) phiên bản **1.21.11** (hoặc tương thích 1.21.x).

---

## 🔨 Hướng dẫn Build (Đóng gói JAR)

Dự án sử dụng trực tiếp công cụ chuẩn **Gradle Wrapper** đi kèm. Bạn không cần cài đặt thêm script ngoài.

### Trên Linux / macOS:
```bash
# Cấp quyền thực thi cho gradle wrapper (chỉ cần làm lần đầu)
chmod +x gradlew

# Build và chạy kiểm thử tự động (Unit Tests)
./gradlew build
```

### Trên Windows (PowerShell / CMD):
```powershell
.\gradlew.bat build
```

Sau khi build thành công:
* File `.jar` đầu ra sẽ nằm tại: **`build/libs/HaoHan-WorldGen-1.0.0.jar`**

---

## 📦 Hướng dẫn Cài đặt & Triển khai

1. **Build hoặc tải file JAR:** Lấy file `HaoHan-WorldGen-1.0.0.jar` từ thư mục `build/libs/`.
2. **Copy vào Server:** Đặt file JAR vào thư mục `plugins/` trên server Minecraft Purpur/Paper của bạn.
3. **Khởi động server:**
   * Plugin sẽ tự động đăng ký bootstrapper, nạp thế giới `haohan:lunar` với cấu hình generator tùy chỉnh.
   * Plugin cung cấp sẵn flag `provides: [HaoHanSMP-Datapack]`, do đó hoàn toàn tương thích và đồng bộ với plugin gameplay [HaoHanLunar](https://github.com/Hao-Han-SMP/HaoHanLunar).

---

## ⚙️ Cấu hình (`worldgen.yml`)

Khi chạy lần đầu, plugin sẽ tự động sinh file cấu hình `plugins/HaoHan-WorldGen/worldgen.yml`:
* Tùy chỉnh bật/tắt các yếu tố: hố thiên thạch, núi lửa, quặng, cụm tinh thể, tảng đá văng.
* Điều chỉnh quy mô và tần suất hố va chạm (`frequency-scale`, `depth-scale`, `rim-scale`).
* Tùy biến ngưỡng dốc vách đá (`slant-threshold`) và bảng vật liệu phân tầng.

### 🎮 Lệnh quản trị trong game (`haohan.admin` hoặc `OP`):
* `/lunar info` — Hiển thị chi tiết thông số cấu hình và trạng thái của worldgen.
* `/lunar reload` — Tải lại cấu hình `worldgen.yml` ngay lập tức mà **không cần khởi động lại máy chủ**.
* `/lunar tp` — Dịch chuyển an toàn đến bề mặt thế giới Mặt Trăng.

---

## 📄 Giấy phép

Dự án được phát hành theo giấy phép [MIT](LICENSE).
