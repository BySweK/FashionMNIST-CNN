# 👕 FashionVision-CNN

**FashionMNIST üzerinde PyTorch kullanılarak geliştirilmiş bir Convolutional Neural Network (CNN) görüntü sınıflandırma projesi.**

Bu projede, FashionMNIST veri setindeki kıyafet görüntülerini farklı kategorilere sınıflandırabilen bir CNN modeli geliştirilmiştir. Proje boyunca veri hazırlama, model oluşturma, eğitim, değerlendirme ve modelin daha önce görmediği görüntüler üzerindeki tahmin süreçleri uygulanmıştır.

---

## 📌 Proje Hakkında

FashionVision-CNN, **FashionMNIST** veri seti üzerinde görüntü sınıflandırma problemini ele almaktadır.

Model, gri tonlamalı kıyafet görüntülerinden özellikleri öğrenerek görüntünün hangi sınıfa ait olduğunu tahmin eder.

Projenin temel amacı:

* PyTorch ile CNN mimarisi oluşturmak
* Görüntü verisini modele uygun hale getirmek
* Modeli eğitim verileri üzerinde eğitmek
* Test verileri üzerinde performansını değerlendirmek
* Eğitim sürecindeki Loss ve Accuracy değerlerini incelemek
* Modelin rastgele test görüntüleri üzerindeki tahminlerini görselleştirmek
* Eğitilmiş modeli dışarıdan alınan bir görüntü üzerinde test etmek

---

## 🧠 Kullanılan Teknolojiler

* **Python**
* **PyTorch**
* **TorchVision**
* **NumPy**
* **Pandas**
* **Matplotlib**
* **Pillow**
* **Jupyter Notebook**

---

## 📊 Dataset — FashionMNIST

Projede **FashionMNIST** veri seti kullanılmıştır.

Veri seti, farklı kıyafet ve aksesuar kategorilerine ait görüntülerden oluşmaktadır.

Modelin tahmin ettiği sınıflar:

| Label | Class         |
| ----: | ------------- |
|     0 | T-shirt / Top |
|     1 | Trouser       |
|     2 | Pullover      |
|     3 | Dress         |
|     4 | Coat          |
|     5 | Sandal        |
|     6 | Shirt         |
|     7 | Sneaker       |
|     8 | Bag           |
|     9 | Ankle Boot    |

Görüntüler model eğitiminden önce `64x64` boyutuna dönüştürülmüş ve gri tonlamalı görüntü olarak modele aktarılmıştır.

---

## 🏗️ CNN Model Mimarisi

Projede, **Tiny VGG yaklaşımından esinlenilen** bir CNN mimarisi kullanılmıştır.

Model genel olarak şu yapıdadır:

```text
Input Image
    │
    ▼
Convolution
    │
    ▼
ReLU
    │
    ▼
Convolution
    │
    ▼
ReLU
    │
    ▼
Max Pooling
    │
    ▼
Convolution
    │
    ▼
ReLU
    │
    ▼
Convolution
    │
    ▼
ReLU
    │
    ▼
Max Pooling
    │
    ▼
Flatten
    │
    ▼
Linear Layer
    │
    ▼
10 Classes
```

Modelin amacı, convolution katmanları aracılığıyla görüntülerdeki önemli görsel özellikleri öğrenmek ve son katmanda bu özellikleri kullanarak 10 sınıftan birini tahmin etmektir.

---

## ⚙️ Model Eğitimi

Model eğitiminde:

* **Loss Function:** Cross Entropy Loss
* **Optimizer:** Adam
* **Classification:** Multi-class classification
* **Epoch tabanlı eğitim:** Kullanılmıştır.

Eğitim süreci `train_step()` ve `test_step()` fonksiyonlarına ayrılarak oluşturulmuş ve daha sonra bu fonksiyonlar genel bir `train()` fonksiyonu içerisinde kullanılmıştır.

Bu yapı sayesinde eğitim ve değerlendirme işlemleri daha düzenli ve tekrar kullanılabilir hale getirilmiştir.

---

## 📈 Model Performansı

Model, FashionMNIST test verileri üzerinde yaklaşık olarak:

**🎯 %88 Test Accuracy**

seviyesinde sonuç elde etmiştir.

Eğitim sürecinde modelin:

* Training Loss
* Test Loss
* Training Accuracy
* Test Accuracy

değerleri takip edilmiş ve grafikler üzerinden incelenmiştir.

> Accuracy değeri kullanılan eğitim ayarlarına bağlı olarak değişebilir.

---

## 🔍 Model Tahminleri

Eğitim tamamlandıktan sonra model yalnızca test verileri üzerinde değil, ayrıca rastgele seçilen görüntüler üzerinde de test edilmiştir.

Tahmin sonuçlarında:

* Gerçek sınıf
* Modelin tahmini
* Görüntü

birlikte incelenmiştir.

Bu sayede modelin doğru ve yanlış sınıflandırmaları görsel olarak değerlendirilebilmiştir.

---

## 🌐 Gerçek Görüntü Üzerinde Test

Projede ayrıca internetten alınan bir görüntü modelin giriş formatına dönüştürülerek test edilmiştir.

Görüntü modele gönderilmeden önce:

```text
RGB
 ↓
Grayscale
 ↓
Resize 64x64
 ↓
Tensor
 ↓
Batch Dimension
 ↓
CNN
```

işlemlerinden geçirilmiştir.

Bu bölüm, modelin eğitim sırasında görmediği bir görüntü üzerindeki davranışını gözlemlemek amacıyla eklenmiştir.

> FashionMNIST ile gerçek dünya görüntüleri arasında önemli görsel farklılıklar bulunabileceğinden, dışarıdan alınan görüntüler üzerindeki tahminlerin test seti performansıyla aynı olması beklenmemelidir.

---


## 🎯 Projede Öğrenilenler

Bu proje kapsamında aşağıdaki konular üzerinde çalışılmıştır:

* FashionMNIST ile görüntü sınıflandırma
* PyTorch temelleri
* CNN mimarisi oluşturma
* `nn.Conv2d`
* `nn.ReLU`
* `nn.MaxPool2d`
* `nn.Linear`
* `CrossEntropyLoss`
* Adam Optimizer
* Training / Testing Loop
* GPU kullanımı
* Model performansının ölçülmesi
* Loss ve Accuracy analizi
* Görsel tahminlerin incelenmesi
* Eğitilmiş modelin dış görüntüler üzerinde test edilmesi

---


## 📌 Sonuç

FashionVision-CNN, FashionMNIST veri seti üzerinde temel bir CNN görüntü sınıflandırma pipeline'ının uçtan uca uygulanmasını amaçlayan bir projedir.

Proje ile veri hazırlama aşamasından model eğitimine, performans değerlendirmesinden model tahminlerinin görselleştirilmesine kadar temel bir görüntü sınıflandırma süreci uygulanmıştır.


---

## 👨‍💻 Author

**Yusuf Yüksel**

Python • Data Science • Machine Learning • Deep Learning
