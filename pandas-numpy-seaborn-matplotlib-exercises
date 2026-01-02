import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# Veri seti
data = [
    {"id": 1, "kategori": "Elektronik", "urun": "Kulaklık", "fiyat": 1500, "adet": 2, "tarih": "2023-01-01"},
    {"id": 2, "kategori": "Moda", "urun": "T-shirt", "fiyat": 500, "adet": 5, "tarih": "2023-01-02"},
    {"id": 3, "kategori": "Elektronik", "urun": "Mouse", "fiyat": 800, "adet": 1, "tarih": "2023-01-03"},
    {"id": 4, "kategori": "Ev", "urun": "Lamba", "fiyat": 1200, "adet": 3, "tarih": "2023-01-04"},
    {"id": 5, "kategori": "Moda", "urun": "Pantolon", "fiyat": 1000, "adet": 2, "tarih": "2023-01-05"},
    {"id": 6, "kategori": "Elektronik", "urun": "Klavye", "fiyat": 2500, "adet": 1, "tarih": "2023-01-06"}]

df = pd.DataFrame(data)

df["toplam satış"] = df["fiyat"] * df["adet"]
print(df)

ilk_degerler = df.head(3)
print("\nİlk Değerler:", ilk_degerler)

desc = df.describe()
print("İstatiksel Değerler:" , desc)

def fiyat_segmenti(fiyat):
    if fiyat >= 2000:
        return "Yüksek Fiyat"
    elif 1000 <= fiyat < 2000:
        return "Ortalama Fiyat"
    else:
        return "Düşük Fiyat"

df["Fiyat Durumu"] = df["fiyat"].apply(fiyat_segmenti)
print("\nFiyat Durumu: ", df["Fiyat Durumu"] )

# Gruplama işlemi
groups = df.groupby("kategori")

group_sum = groups.sum(numeric_only=True)
group_mean = groups.mean(numeric_only=True)

print("\nKategoriye Göre Toplam:", group_sum)
print("\nKategoriye Göre Ortalama:", group_mean)

yuksek_ciro = df[df["toplam satış"] > 2000]
print("\nYüksek Ciro Yapan Ürünler:")
print(yuksek_ciro)

sns.set_style("whitegrid")
sns.scatterplot(x="fiyat", y="adet", data=df, hue="kategori")
plt.xlabel("Fiyat")
plt.ylabel("Adet")
plt.title("Adet - Fiyat İlişkisi")
plt.show()

df["tarih"] = pd.to_datetime(df["tarih"])
df = df.sort_values("tarih")

sns.set_style("darkgrid")
sns.lineplot(x="tarih", y="toplam satış", data=df, linestyle="-", marker="*")
plt.xlabel("Tarih")
plt.ylabel("Toplam Satış")
plt.title("Tarih - Toplam Satış İlişkisi")
plt.show()
