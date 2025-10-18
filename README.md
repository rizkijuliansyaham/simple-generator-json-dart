# 🧩 Flutter Model & Entity Generator (Build Version)

Aplikasi web ini digunakan untuk **mengubah JSON menjadi class Entity & Model Dart** secara otomatis.  
Didesain khusus untuk arsitektur **Clean Architecture Flutter**, agar pengembang dapat memisahkan layer `Entity` dan `Model` dengan mudah.

---

## 🚀 Fitur Utama

- ⚙️ **Generate Entity & Model Dart otomatis** dari struktur JSON
- 🧩 **EntityModel Utils** — menyediakan interface standar `EntityModel<T>` & `EntityModelToJsonAble<T>`
- 🧭 **Navigasi File** — daftar file hasil generate di panel kiri, klik untuk auto-scroll ke preview kanan
- 🔽 **Expand/Collapse Preview** — setiap file preview bisa dibuka/tutup, lengkap dengan tombol global *Expand All* dan *Collapse All*
- 💾 **Download ZIP** — unduh semua file hasil generate dalam satu paket ZIP
- 📋 **Copy Code** — salin kode file individual dengan satu klik
- ✨ **Auto Urutkan File** — class utama (root) selalu berada di urutan paling atas

---

## 🧩 Cara Menggunakan

1. Buka aplikasi di browser (misal:  
   [**https://rizkijuliansyaham.github.io/simple-generator-json-dart/**](https://rizkijuliansyaham.github.io/simple-generator-json-dart/)
   )

2. Masukkan **nama class utama** (misalnya `TravelHistoryItem`).

3. Paste JSON respons ke kolom kiri.

4. Klik tombol **Generate ➜** untuk memproses.

5. File hasil generate akan muncul di panel kanan, contohnya:
   - `travelhistoryitem.dart`
   - `travelhistoryitem_model.dart`
   - Sub-model lain otomatis dibuat sesuai struktur JSON.

6. Klik nama file di kiri untuk *auto-scroll* ke preview kanan.

7. Klik “Copy” untuk menyalin kode, atau “Download ZIP” untuk mengunduh seluruh file.

8. Gunakan tombol “🧩 Utils” untuk menampilkan helper interface:
   ```dart
   abstract class EntityModel<T> {
     T get toEntity;
   }

   abstract class EntityModelToJsonAble<T> implements EntityModel<T> {
     Map get toJson;
   }
   ```

---

## 📦 Hasil Output

Setiap kali kamu generate JSON, hasilnya berupa pasangan:
```
model_name.dart
model_name_model.dart
```

**Contoh:**
```dart
class Device {
  final String id;
  final String deviceName;

  const Device({
    required this.id,
    required this.deviceName,
  });
}
```

```dart
class DeviceModel implements EntityModel<Device> {
  final String id;
  final String deviceName;

  const DeviceModel({
    required this.id,
    required this.deviceName,
  });

  factory DeviceModel.fromJson(Map<String, dynamic> json) => DeviceModel(
        id: json['id'] ?? '',
        deviceName: json['deviceName'] ?? '',
      );

  Map<String, dynamic> toJson() => {
        'id': id,
        'deviceName': deviceName,
      };

  @override
  Device toEntity() => Device(
        id: id,
        deviceName: deviceName,
      );
}
```

---

## 🧰 Teknologi

- ⚛️ React 18 + Vite  
- 🎨 TailwindCSS  
- 🧠 JSZip + FileSaver (ZIP downloader)  
- 🌈 React Syntax Highlighter  
- 📋 Copy to Clipboard  

---

## 👨‍💻 Author

**Rizki Juliansyah**  
Flutter Developer · Clean Architecture Enthusiast  
💼 [LinkedIn](https://www.linkedin.com/in/rizkijuliansyah) · 🧠 [GitHub](https://github.com/rizkijuliansyah)

---

## 🪪 License
MIT License © 2025 Rizki Juliansyah
