# 🤖 Assignment IK ML DL RL – Inverse Kinematics Robot Planar 3-DOF

## Nama

Muhammad Zaidi

## NIM

4222301071

## Tujuan Praktikum

1. Memahami konsep Inverse Kinematics (IK) pada robot planar 3-DOF.
2. Mengimplementasikan Machine Learning, Deep Learning, dan Reinforcement Learning untuk menyelesaikan masalah IK.
3. Membandingkan performa KNN, Random Forest, Deep Learning (MLP), dan Reinforcement Learning (PPO).
4. Menganalisis pengaruh perubahan panjang link robot terhadap workspace dan akurasi model.
5. Melakukan optimasi metode Machine Learning.

---

# Analisis Hasil

Pada praktikum ini dilakukan perbandingan beberapa metode untuk menyelesaikan masalah Inverse Kinematics robot planar 3-DOF, yaitu KNN, Random Forest, Deep Learning, dan Reinforcement Learning.

Panjang link robot diubah dari [0.4, 0.3, 0.2] menjadi [0.5, 0.4, 0.3]. Perubahan ini meningkatkan jangkauan maksimum robot dari 0.9 meter menjadi 1.2 meter sehingga workspace robot menjadi lebih luas.

Berdasarkan hasil pengujian, metode KNN menghasilkan mean end-effector error sebesar 62.14 cm, sedangkan Random Forest menghasilkan mean end-effector error sebesar 66.41 cm. Perbedaan hasil ini menunjukkan bahwa performa model dipengaruhi oleh kualitas dataset, parameter model, dan distribusi data pelatihan.

Optimasi Random Forest dilakukan dengan meningkatkan jumlah pohon (n_estimators) dan kedalaman pohon (max_depth). Tujuan optimasi ini adalah meningkatkan kemampuan model dalam mempelajari hubungan antara posisi target dan sudut sendi robot.

---

# Pertanyaan Diskusi

## 1. Mengapa DL lebih akurat dari KNN meskipun datanya sama?

Deep Learning mampu mempelajari hubungan non-linear yang kompleks melalui beberapa lapisan neuron sehingga memiliki kemampuan generalisasi yang lebih baik. Sebaliknya, KNN hanya mengandalkan data tetangga terdekat sehingga performanya bergantung pada distribusi dataset yang tersedia.

## 2. Mengapa RL tidak butuh dataset tetapi training-nya lebih lama?

Reinforcement Learning belajar melalui interaksi langsung dengan environment menggunakan metode trial-and-error. Agent harus mencoba banyak aksi, menerima reward, dan memperbaiki policy secara bertahap sehingga membutuhkan waktu training yang lebih lama dibandingkan metode supervised learning.

## 3. Bagaimana menambahkan obstacle avoidance pada pendekatan RL?

Obstacle avoidance dapat ditambahkan dengan memasukkan posisi obstacle ke dalam state environment serta memberikan reward negatif ketika robot mendekati atau menabrak obstacle. Dengan demikian agent akan belajar mencapai target sekaligus menghindari hambatan.

## 4. Apa kelemahan supervised learning (ML/DL) untuk IK pada konfigurasi baru?

Model supervised learning sangat bergantung pada data pelatihan. Jika panjang link, workspace, atau konfigurasi robot berubah, maka model yang telah dilatih dapat mengalami penurunan akurasi dan perlu dilakukan pelatihan ulang menggunakan dataset baru.

---

# Tugas Praktikum

## 1. Mengubah Panjang Link Menjadi [0.5, 0.4, 0.3]

Konfigurasi awal:

```python
L1 = 0.4
L2 = 0.3
L3 = 0.2
```

Konfigurasi baru:

```python
L1 = 0.5
L2 = 0.4
L3 = 0.3
```

Perubahan jangkauan maksimum:

* Sebelum = 0.9 meter
* Sesudah = 1.2 meter

### Analisis

Perubahan panjang link meningkatkan workspace robot sehingga robot mampu menjangkau target yang lebih jauh dibandingkan konfigurasi sebelumnya.

## 2. Optimasi Metode Machine Learning

Optimasi dilakukan pada Random Forest dengan parameter:

```python
RandomForestRegressor(
    n_estimators=300,
    max_depth=20,
    min_samples_split=2,
    min_samples_leaf=1,
    random_state=42,
    n_jobs=-1
)
```

### Analisis

Optimasi dilakukan untuk meningkatkan kemampuan model dalam mempelajari hubungan antara posisi target dan sudut sendi robot. Dengan jumlah pohon yang lebih banyak dan kedalaman pohon yang lebih besar, model menjadi lebih stabil dan mampu menghasilkan prediksi yang lebih baik.

---

# Kesimpulan Akhir Praktikum

Pada praktikum ini telah dilakukan implementasi dan perbandingan beberapa metode untuk menyelesaikan masalah Inverse Kinematics robot planar 3-DOF, yaitu KNN, Random Forest, Deep Learning, dan Reinforcement Learning.

Perubahan panjang link dari [0.4, 0.3, 0.2] menjadi [0.5, 0.4, 0.3] berhasil meningkatkan jangkauan maksimum robot dari 0.9 meter menjadi 1.2 meter sehingga workspace robot menjadi lebih luas.

Optimasi metode Machine Learning dilakukan menggunakan Random Forest dengan penyesuaian parameter untuk meningkatkan performa model. Hasil praktikum menunjukkan bahwa setiap metode memiliki kelebihan dan kekurangan masing-masing. KNN memiliki implementasi yang sederhana, Random Forest memberikan prediksi yang stabil, Deep Learning mampu mempelajari hubungan non-linear yang kompleks, sedangkan Reinforcement Learning tidak memerlukan dataset namun membutuhkan waktu training yang lebih lama.

Secara keseluruhan, metode berbasis Deep Learning dan Reinforcement Learning memiliki potensi yang lebih baik untuk menyelesaikan permasalahan Inverse Kinematics yang kompleks dibandingkan metode Machine Learning konvensional.
