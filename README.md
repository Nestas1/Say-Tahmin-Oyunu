<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sayı Tahmin Oyunu</title>
    <style>
        body { font-family: Arial, sans-serif; background-color: #f0f8ff; text-align: center; }
        #game-container { margin-top: 50px; }
        input { padding: 10px; font-size: 16px; }
        button { padding: 10px 20px; font-size: 16px; margin-left: 10px; }
        #output { margin-top: 20px; }
        .hidden { display: none; }
    </style>
</head>
<body>
    <h1>Sayı Tahmin Oyunu</h1>
    <div id="game-container">
        <p>1 ile 100 arasında bir sayı tahmin et!</p>
        <input type="number" id="tahmin" min="1" max="100" />
        <button onclick="tahminYap()">Tahmin Et</button>
        <button onclick="oyunuBaslat()">Yeniden Başlat</button>
    </div>
    <div id="output"></div>

    <script>
        let rastgeleSayi;
        let sayac = 0;

        function oyunuBaslat() {
            rastgeleSayi = Math.floor(Math.random() * 100) + 1;
            sayac = 0;
            document.getElementById("output").innerHTML = "";
            document.getElementById("tahmin").value = "";
            document.getElementById("game-container").querySelector("button:first-child").disabled = false;
            document.getElementById("tahmin").disabled = false;
        }

        function tahminYap() {
            const tahmin = parseInt(document.getElementById("tahmin").value);
            const output = document.getElementById("output");
            sayac++;

            if (tahmin < 1 || tahmin > 100 || isNaN(tahmin)) {
                output.innerHTML = "Lütfen 1 ile 100 arasında bir sayı girin.";
            } else if (tahmin < rastgeleSayi) {
                output.innerHTML = "Daha yüksek bir sayı deneyin.";
            } else if (tahmin > rastgeleSayi) {
                output.innerHTML = "Daha düşük bir sayı deneyin.";
            } else {
                output.innerHTML = `Tebrikler! ${sayac} tahminde doğru bildin!`;
                document.getElementById("game-container").querySelector("button:first-child").disabled = true;
                document.getElementById("tahmin").disabled = true;
            }
        }

        // Oyunu başlat
        oyunuBaslat();
    </script>
</body>
</html>
