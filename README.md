# Aplikasi Konversi Suhu  
Tugas 2 - Adrian Akhmad Firdaus (2210010491)

---

## Deskripsi

Aplikasi ini memungkinkan pengguna untuk mengonversi nilai suhu dari satu skala ke skala lainnya dengan antarmuka grafis yang sederhana.

---

## Fitur Aplikasi

1. **Konversi Antar Skala Suhu**:  
   - Pengguna memasukkan nilai suhu di `JTextField`, memilih skala awal dengan `JRadioButton`, dan arah konversi dengan `JComboBox`.  
   - Hasil konversi akan ditampilkan setelah tombol **Konversi** ditekan.  
   - **Contoh Kode Implementasi**:  
     ```java
     private void buttonKonversiActionPerformed(java.awt.event.ActionEvent evt) {                                               
         try {
             double inputSuhu = Double.parseDouble(txtInputSuhu.getText());
             String pilihanKonversi = (String) cmbKonversi.getSelectedItem();
             double hasil = 0.0;

             if (rCelcius.isSelected()) {
                 hasil = celsiusKeFahrenheit(inputSuhu); // Contoh konversi dari Celsius ke Fahrenheit
             }
             txtHasil.setText(String.valueOf(hasil));
         } catch (NumberFormatException e) {
             JOptionPane.showMessageDialog(this, "Masukkan angka yang valid!");
         }
     }
     ```

2. **Validasi Input Angka**:  
   - Membatasi input hanya untuk angka menggunakan `KeyAdapter`.  
   - **Contoh Kode Implementasi**:  
     ```java
     private void txtInputSuhuKeyTyped(java.awt.event.KeyEvent evt) {                                      
         char c = evt.getKeyChar();
         if (!Character.isDigit(c) && c != '.') {
             evt.consume();
         }
     }
     ```

3. **Konversi Otomatis**:  
   - Hasil konversi diperbarui secara otomatis ketika input suhu berubah menggunakan `DocumentListener`.  
   - **Contoh Kode Implementasi**:  
     ```java
     txtInputSuhu.getDocument().addDocumentListener(new DocumentListener() {
         @Override
         public void insertUpdate(DocumentEvent e) {
             lakukanKonversiOtomatis();
         }
         @Override
         public void removeUpdate(DocumentEvent e) {
             lakukanKonversiOtomatis();
         }
         @Override
         public void changedUpdate(DocumentEvent e) {
             lakukanKonversiOtomatis();
         }
     });
     ```

4. **Skala Suhu Tambahan**:  
   - Mendukung Celsius, Fahrenheit, Kelvin, dan Reamur.  
   - **Contoh Kode Implementasi**:  
     ```java
     private void rCelciusItemStateChanged(java.awt.event.ItemEvent evt) {                                          
         if (evt.getStateChange() == ItemEvent.SELECTED) {
             cmbKonversi.removeAllItems();
             cmbKonversi.addItem("Celsius ke Fahrenheit");
             cmbKonversi.addItem("Celsius ke Kelvin");
             cmbKonversi.addItem("Celsius ke Reamur");
         }
     }
     ```

---

## Komponen GUI

Aplikasi ini menggunakan komponen berikut:
- **JFrame**: Jendela utama aplikasi.  
- **JPanel**: Panel untuk menata elemen GUI.  
- **JLabel**: Label untuk input suhu dan hasil konversi.  
- **JTextField**: Input suhu (`txtInputSuhu`) dan output hasil (`txtHasil`).  
- **JRadioButton**: Pilihan skala awal.  
- **JComboBox**: Pilihan arah konversi.  
- **JButton**: Tombol untuk memulai konversi.  

---

## Struktur Program

### 1. Desain GUI  
   - Komponen dirancang menggunakan `GridBagLayout` agar lebih fleksibel.

### 2. Logika Program  
   - Semua rumus konversi antar skala suhu diterapkan.  
   - Contoh rumus untuk konversi:  
     ```java
     private double celsiusKeFahrenheit(double celsius) {
         return celsius * 9 / 5 + 32;
     }
     private double fahrenheitKeCelsius(double fahrenheit) {
         return (fahrenheit - 32) * 5 / 9;
     }
     ```

### 3. Events  
   - **ActionListener**: Untuk memproses konversi ketika tombol **Konversi** ditekan.  
     ```java
     private void buttonKonversiActionPerformed(java.awt.event.ActionEvent evt) { 
         // Logika konversi
     }
     ```
   - **KeyAdapter**: Membatasi input hanya angka.  
   - **DocumentListener**: Untuk memperbarui hasil konversi secara otomatis.  
   - **ItemListener**: Untuk memperbarui pilihan arah konversi berdasarkan skala awal yang dipilih.

---

## Cara Menjalankan Aplikasi

1. Clone atau unduh repositori ini.  
2. Buka proyek di NetBeans IDE 8.2.  
3. Jalankan file utama `KonversiSuhuForm.java`.  
4. Masukkan nilai suhu, pilih skala awal, dan pilih arah konversi.  
5. Tekan tombol **Konversi** untuk melihat hasilnya.  

---

## Tampilan Saat Aplikasi Dijalankan

![Tampilan Aplikasi](https://github.com/user-attachments/assets/aa7fccc4-104e-45d7-b7e3-46d11e61d8dc)

---

## Indikator Penilaian

| No  | Komponen           | Persentase |
|-----|---------------------|------------|
| 1   | Komponen GUI       | 10%        |
| 2   | Logika Program     | 20%        |
| 3   | Events             | 15%        |
| 4   | Kesesuaian UI      | 15%        |
| 5   | Memenuhi Variasi   | 40%        |
| **TOTAL** |               | **100%**   |

---

## Pembuat

- **Nama**: Adrian Akhmad Firdaus  
- **NPM**: 2210010491  
- **Kelas**: 5A Reguler Pagi  
- **Tugas**: Tugas 2 - Aplikasi Konversi Suhu  
- **Fakultas**: Teknologi Informasi (FTI)  
- **Universitas**: Universitas Islam Kalimantan Muhammad Arsyad Al Banjari Banjarmasin  

--- 
