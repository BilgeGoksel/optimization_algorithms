# Deniz Yırtıcıları Algoritması (Marine Predators Algorithm-MPA )

## Giriş

Marine Predators Algorithm (MPA), deniz yırtıcılarının avlanma stratejilerinden ilham alan, doğadan esinlenmiş bir metaheuristik optimizasyon algoritmasıdır. Bu algoritma, Lévy ve Brownian hareketlerini kullanarak yırtıcı ile av arasındaki biyolojik etkileşimleri taklit eder. İlk kez 2020 yılında "Expert Systems with Applications" dergisinde tanıtılmış olan bu algoritma, mühendislik problemleri ve matematiksel fonksiyonlar üzerinde çok başarılı sonuçlar vermiştir.

## Temel Özellikler

1. **Doğadan Esinlenme**: Algoritma, yırtıcı ve avın doğada izlediği stratejilerden esinlenmiştir.
   - **Lévy Hareketi**: Az av yoğunluklu alanlarda kullanılır, küçük adımlar ve uzun sıçramalarla karakterizedir.
   - **Brownian Hareketi**: Yüksek av yoğunluklu alanlarda daha düzenli ve kontrollü adımlar izler.
2. **Hafıza Mekanizması**: Algoritma, daha önce başarılı çözüm bulduğu konumları hafızaya alarak arama etkinliğini artırır.
3. **Keşfetme ve Sömürme Dengesi**: Algoritma, küresel ve yerel arama stratejilerini dengeli bir şekilde uygular.
4. **FAD ve Eddy Efektleri**: Yerel minimumlarda sıkışmayı önlemek için "Fish Aggregating Devices" gibi çevresel etkileri dikkate alır.

## Konum Güncelleme Denklemleri

MPA, üç temel fazda hareket eder ve her bir faz için farklı konum güncelleme denklemleri kullanılır:

### Faz 1: Yüksek Keşfetme

Brownian hareketi kullanılarak avlar çevrelerini yoğun bir şekilde keşfeder:

```math
stepsize[i, :] = RB[i, :] \cdot (Elite[i, :] - RB[i, :] \cdot Prey[i, :])
Prey[i, :] += P \cdot R \cdot stepsize[i, :]
```

### Faz 2: Geçiş

Popülasyon ikiye ayrılır:

- **Brownian Hareketi**:

```math
stepsize[i, :] = RB[i, :] \cdot (RB[i, :] \cdot Elite[i, :] - Prey[i, :])
Prey[i, :] = Elite[i, :] + P \cdot CF \cdot stepsize[i, :]
```

- **Lévy Hareketi**:

```math
stepsize[i, :] = RL[i, :] \cdot (Elite[i, :] - RL[i, :] \cdot Prey[i, :])
Prey[i, :] += P \cdot R \cdot stepsize[i, :]
```

### Faz 3: Yüksek Sömürme

Lévy hareketiyle yırtıcılar belirli bölgelerde daha detaylı arama yapar:

```math
stepsize[i, :] = RL[i, :] \cdot (RL[i, :] \cdot Elite[i, :] - Prey[i, :])
Prey[i, :] = Elite[i, :] + P \cdot CF \cdot stepsize[i, :]
```

## Keşfetme ve Sömürü Mekanizmaları

1. **Keşfetme (Exploration)**:

   - Algoritmanın ilk fazında, yırtıcı hareketsiz kalırken avlar Brownian hareketiyle alanı keşfeder.
   - Lévy hareketiyle daha az yoğun alanlarda uzun adımlar atılarak yeni çözüm bölgeleri bulunur.

2. **Sömürme (Exploitation)**:

   - İkinci ve üçüncü fazlarda, algoritma yırtıcının bulunduğu alanı daha detaylı inceleyerek daha iyi çözümler bulur.
   - Hafıza mekanizması, önceki iyi çözümlerin tekrar aranmasını sağlar.

3. **FAD ve Eddy Efektleri**:

   - Algoritmanın tıkanmasını önlemek için rastgele uzun adımlar kullanılır.
   - Yerel optimumlardan çıkılmasını sağlar.

## Referanslar

1. X. Zhun, Q. Heidari, A. Mirjalili, “Marine Predators Algorithm: A Nature-Inspired Metaheuristic,” Expert Systems with Applications, 2020.
2. MPA algoritmasının orijinal yayını: [ScienceDirect Linki](https://www.sciencedirect.com/science/article/abs/pii/S0957417420302025).



