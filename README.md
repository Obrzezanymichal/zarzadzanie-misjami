ZADANIE

JS


const misje = [];


function zaplanujMisje(nazwaMisji, typMisji) {
    const misja = {
        nazwa: "Ekspedycja na marsa",
        typ: "badawcza",
        zaloga: ["kpt. mariusz", "dr wasilek"],
        dystans: 0,
        celeBadawcze: ["analiza gleby", "zbieranie mineralow"],
        ladownia: {
            narzedzia: ["łazik", "butle z tlenem"],
            zapasy: 100
        }
    };
    misje.push(misja);
    return misja;
}


function dodajDoZalogi(misja, czlonek) {
    misja.zaloga.push(czlonek);
}


function zaladujSprzet(misja, sprzet) {
    misja.ladownia.narzedzia.push(sprzet);
}


function przemierzDystans(misja, odleglosc) {
    misja.dystans += odleglosc;
   
    const zuzycie = (odleglosc / 5) * 10;
    misja.ladownia.zapasy -= zuzycie;
    if (misja.ladownia.zapasy < 0) misja.ladownia.zapasy = 0;
}


function raportMisji(misja) {
    let raport = `*** RAPORT MISJI: ${misja.nazwa} ***\n`;
    raport += `Typ misji: ${misja.typ}\n`;
    raport += `Przebyty dystans: ${misja.dystans} AU\n`;
    raport += `Pozostałe zapasy: ${misja.ladownia.zapasy}%\n\n`;

    raport += "--- ZAŁOGA ---\n";
    if (misja.zaloga.length > 0) {
        raport += misja.zaloga.map(cz => `- ${cz}`).join("\n") + "\n\n";
    } else {
        raport += "Brak danych o załodze.\n\n";
    }

    raport += "--- SPRZĘT W ŁADOWNI ---\n";
    if (misja.ladownia.narzedzia.length > 0) {
        raport += misja.ladownia.narzedzia.map(s => `- ${s}`).join("\n");
    } else {
        raport += "Ładownia pusta.";
    }

    return raport;
}



const misjaAlfa = zaplanujMisje("Ekspedycja na Marsa", "Badawcza");

dodajDoZalogi(misjaAlfa, "Inżynier");
dodajDoZalogi(misjaAlfa, "Medyk");
dodajDoZalogi(misjaAlfa, "Biolog");
dodajDoZalogi(misjaAlfa, "Pilot");
dodajDoZalogi(misjaAlfa, "Architekt");
dodajDoZalogi(misjaAlfa, "Specjalista ds. komunikacji");

zaladujSprzet(misjaAlfa, "Moduł mieszkalny");
zaladujSprzet(misjaAlfa, "Generator tlenu");
zaladujSprzet(misjaAlfa, "Drukarka 3D");

przemierzDystans(misjaAlfa, 10);
przemierzDystans(misjaAlfa, 5);


INDEX

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script src="misje.js"></script>
<body>
    
</body>
</html>

console.log(raportMisji(misjaAlfa));
