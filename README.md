# Okul Not Sistemi (Ders Bazlı Gelişme + Madalya + Renkli Tavsiye + Not Sınırı)

dersler = ["Matematik", "Türkçe", "Fen Bilgisi", "İngilizce", "Tarih"]

donem1_ortalamalari = []
donem2_ortalamalari = []

# Renkler
RED = '\033[91m'
GREEN = '\033[92m'
YELLOW = '\033[93m'
BLUE = '\033[94m'
RESET = '\033[0m'

# Fonksiyon: Madalya yazdır
def madalya_yazdir(ortalama):
    if ortalama <= 50:
        print(RED + "Kaldın ❌ - Biraz daha çalışmalısın 📚" + RESET)
    elif 50 < ortalama < 60:
        print(YELLOW + "Bronz Madalya 🥉 - Geçtin ama biraz daha çalışsan iyi olur 👍" + RESET)
    elif 60 <= ortalama < 80:
        print(BLUE + "Gümüş Madalya 🥈" + RESET)
    elif 80 <= ortalama <= 100:
        print(GREEN + "Altın Madalya 🥇 - Çok iyi! Böyle devam et 🚀" + RESET)

# Fonksiyon: Not al ve 0-100 aralığında sınırla
def not_al(ders, sinav_no):
    while True:
        try:
            notu = int(input(f"{ders} {sinav_no}. sınav: "))
            if 0 <= notu <= 100:
                return notu
            else:
                print(RED + "⚠️ Not 0 ile 100 arasında olmalı! Tekrar giriniz." + RESET)
        except ValueError:
            print(RED + "⚠️ Lütfen geçerli bir sayı giriniz!" + RESET)

# 1. Dönem Notları
print("\n=== 1. Dönem Notları ===")
for ders in dersler:
    n1 = not_al(ders, 1)
    n2 = not_al(ders, 2)
    n3 = not_al(ders, 3)
    ort = (n1 + n2 + n3) / 3
    donem1_ortalamalari.append(ort)
    print(f"{ders} 1. dönem ortalaması: {ort:.2f}")

# 2. Dönem Notları
print("\n=== 2. Dönem Notları ===")
for i, ders in enumerate(dersler):
    m1 = not_al(ders, 1)
    m2 = not_al(ders, 2)
    m3 = not_al(ders, 3)
    ort = (m1 + m2 + m3) / 3
    donem2_ortalamalari.append(ort)
    print(f"{ders} 2. dönem ortalaması: {ort:.2f}")

    # Ders bazlı gelişme kontrolü
    if ort > donem1_ortalamalari[i]:
        print(GREEN + "Tebrikler, geçen döneme göre gelişme var 🎉" + RESET)
    elif ort < donem1_ortalamalari[i]:
        print(RED + "Biraz daha gayretli çalışırsan daha iyi olur 💪" + RESET)
    else:
        print(BLUE + "Ortalaman sabit, güzel 👍" + RESET)

# Ders bazlı ortalama listeleri
print("\n=== Ders Bazlı Ortalama Listeleri ===")
for i, ders in enumerate(dersler):
    print(f"{ders} - 1. Dönem: {donem1_ortalamalari[i]:.2f}, 2. Dönem: {donem2_ortalamalari[i]:.2f}")

# Genel dönem ortalamaları
donem1_genel = sum(donem1_ortalamalari) / len(donem1_ortalamalari)
donem2_genel = sum(donem2_ortalamalari) / len(donem2_ortalamalari)
yillik_genel = (donem1_genel + donem2_genel) / 2

print(f"\n📌 1. Dönem Genel Ortalama: {donem1_genel:.2f}")
madalya_yazdir(donem1_genel)

print(f"\n📌 2. Dönem Genel Ortalama: {donem2_genel:.2f}")
madalya_yazdir(donem2_genel)

print(f"\n🏆 Yıllık Genel Ortalama: {yillik_genel:.2f}")
madalya_yazdir(yillik_genel)

# Yıllık genel ortalamaya tavsiye
print("\n📌 Tavsiye Mesajı:")
if yillik_genel < 50:
    print(RED + "Genel ortalaman düşük 😔, tüm derslere daha fazla çalışmalısın!" + RESET)
elif 50 <= yillik_genel < 60:
    print(YELLOW + "Genel ortalaman biraz düşük 👍, özellikle zorlandığın derslere odaklan!" + RESET)
elif 60 <= yillik_genel < 80:
    print(BLUE + "Genel ortalaman iyi 😎, ama bazı derslerde daha da gelişebilirsin!" + RESET)
else:
    print(GREEN + "Genel ortalaman mükemmel 🎉, böyle devam et!" + RESET)
