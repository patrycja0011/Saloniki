<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Słoneczna Macedonia i Półwysep Chalkidiki – Pacia Travel</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Playfair+Display:ital,wght@0,600;0,700;1,400&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <style>
        :root {
            --primary: #0A2540;
            --accent: #007791;
            --gold: #D4AF37;
            --light-bg: #F8FAFC;
            --card-bg: #FFFFFF;
            --text-dark: #1E293B;
            --text-muted: #64748B;
            --border: #E2E8F0;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--light-bg);
            color: var(--text-dark);
            line-height: 1.6;
        }

        a {
            color: var(--accent);
            text-decoration: none;
            font-weight: 600;
        }

        a:hover {
            text-decoration: underline;
        }

        header {
            background: linear-gradient(rgba(10, 37, 64, 0.75), rgba(0, 119, 145, 0.75)), url('https://images.unsplash.com/photo-1570077188670-e3a8d69ac5ff?auto=format&fit=crop&w=1920&q=80') center/cover no-repeat;
            color: #FFFFFF;
            padding: 90px 20px;
            text-align: center;
        }

        .header-content {
            max-width: 950px;
            margin: 0 auto;
        }

        .badge {
            display: inline-block;
            background-color: var(--gold);
            color: var(--primary);
            padding: 6px 18px;
            font-weight: 700;
            border-radius: 20px;
            text-transform: uppercase;
            font-size: 0.85rem;
            letter-spacing: 1px;
            margin-bottom: 20px;
        }

        h1 {
            font-family: 'Playfair Display', serif;
            font-size: 2.8rem;
            margin-bottom: 15px;
            line-height: 1.2;
        }

        .subtitle {
            font-size: 1.2rem;
            font-weight: 300;
            opacity: 0.95;
            margin-bottom: 30px;
        }

        .quick-stats {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(8px);
            padding: 10px 20px;
            border-radius: 12px;
            font-size: 0.9rem;
            border: 1px solid rgba(255, 255, 255, 0.25);
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 50px 20px;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 2.2rem;
            color: var(--primary);
            text-align: center;
            margin-bottom: 15px;
        }

        .section-subtitle {
            text-align: center;
            color: var(--text-muted);
            margin-bottom: 40px;
            font-size: 1.05rem;
        }

        .titles-box {
            background-color: var(--card-bg);
            border-left: 4px solid var(--accent);
            padding: 25px;
            border-radius: 8px;
            margin-bottom: 30px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
        }

        .titles-box h3 {
            color: var(--primary);
            margin-bottom: 12px;
            font-family: 'Playfair Display', serif;
        }

        .titles-box ul {
            list-style: none;
        }

        .titles-box li {
            margin-bottom: 8px;
            padding-left: 20px;
            position: relative;
        }

        .titles-box li::before {
            content: "✓";
            position: absolute;
            left: 0;
            color: var(--accent);
            font-weight: bold;
        }

        .info-foreign {
            background-color: #EFF6FF;
            border: 1px solid #BFDBFE;
            color: #1E40AF;
            padding: 18px 24px;
            border-radius: 8px;
            margin-bottom: 40px;
            font-size: 0.95rem;
            text-align: center;
        }

        .highlights-box {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid var(--border);
            margin-bottom: 40px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.03);
        }

        .custom-list {
            list-style: none;
        }

        .custom-list li {
            position: relative;
            padding-left: 25px;
            margin-bottom: 12px;
            font-size: 0.98rem;
        }

        .custom-list li::before {
            content: "•";
            color: var(--accent);
            font-weight: bold;
            font-size: 1.5rem;
            position: absolute;
            left: 5px;
            top: -5px;
        }

        #map-container {
            background: var(--card-bg);
            border-radius: 12px;
            border: 1px solid var(--border);
            padding: 20px;
            margin-bottom: 40px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.03);
        }

        #map {
            height: 420px;
            width: 100%;
            border-radius: 8px;
        }

        .day-card {
            background: var(--card-bg);
            border-radius: 12px;
            border: 1px solid var(--border);
            padding: 30px;
            margin-bottom: 25px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.03);
        }

        .day-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.4rem;
            color: var(--primary);
            border-bottom: 2px solid var(--light-bg);
            padding-bottom: 12px;
            margin-bottom: 15px;
        }

        .day-body {
            font-size: 0.98rem;
            color: var(--text-dark);
            margin-bottom: 20px;
        }

        .restaurants-box {
            background-color: #F1F5F9;
            padding: 15px 20px;
            border-radius: 8px;
            border-left: 3px solid var(--gold);
            font-size: 0.92rem;
        }

        .restaurants-box strong {
            color: var(--primary);
            display: block;
            margin-bottom: 6px;
        }

        .restaurants-box ul {
            list-style: none;
        }

        .restaurants-box li {
            margin-bottom: 4px;
        }

        .grid-two {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .info-card {
            background: var(--card-bg);
            border-radius: 12px;
            border: 1px solid var(--border);
            padding: 30px;
        }

        .info-card h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.4rem;
            color: var(--primary);
            margin-bottom: 18px;
        }

        footer {
            background-color: var(--primary);
            color: #FFFFFF;
            text-align: center;
            padding: 35px 20px;
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .grid-two { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <header>
        <div class="header-content">
            <span class="badge">Wyjątkowa Podróż Poślubna</span>
            <h1>Słoneczna Macedonia i Półwysep Chalkidiki</h1>
            <p class="subtitle">Mityczny Olimp, Klasztory w Meteorach, rejs na Wyspę Diaporos oraz relaks na plażach Chalkidiki</p>
            
            <div class="quick-stats">
                <div class="stat-card">✈️ Przelot z Warszawy</div>
                <div class="stat-card">🚗 Wynajęty Samochód w Cenie</div>
                <div class="stat-card">🏨 2 Bazy Noclegowe (BB)</div>
                <div class="stat-card">⌛ 8 Dni / 7 Nocy</div>
            </div>
        </div>
    </header>

    <div class="container">

        <div class="titles-box">
            <h3>Propozycje Tytułów Wyjazdu</h3>
            <ul>
                <li>Słoneczna Macedonia i Półwysep Chalkidiki – Mityczny Olimp, Rejs na Diaporos i Meteory.</li>
                <li>Grecka Podróż Poślubna – Mityczne Szczyty, Lazurowe Zatoki i Wieczór z Muzyką.</li>
                <li>Saloniki, Meteory i Urokliwa Sytonia – Romantyczny Rejs, Wodospady i Dwie Bazy Noclegowe.</li>
                <li>Skarby Północnej Grecji – Klasztory Meteorów, Błękitna Laguna i Relaks nad Morzem.</li>
            </ul>
        </div>

        <div class="titles-box" style="border-left-color: var(--gold);">
            <h3>Trasa Wyjazdu</h3>
            <p><strong>Saloniki – Litochoro – Masyw Olimpu – Meteory – Edesa – Półwysep Sytonia – Rejs na Diaporos – Saloniki</strong></p>
        </div>

        <div class="info-foreign">
            Osoby mieszkające poza granicami Polski, serdecznie zapraszamy do kontaktu z naszym biurem. Z przyjemnością przygotujemy indywidualną kalkulację przelotu z dowolnego portu lotniczego na świecie.
        </div>

        <h2 class="section-title">Wstęp Prosprzedażowy i SEO</h2>
        <p class="section-subtitle">
            Wasza wyjątkowa grecka podróż to marzenie każdego nowożeńca! Wyprawa łącząca fascynującą historię, mityczne krajobrazy oraz beztroski wypoczynek nad brzegiem Morza Egejskiego. Podczas tego wyjazdu odkryjecie tajemnice mitycznego Masywu Olimpu, przejdziecie urokliwymi szlakami w Litochoro oraz zachwycicie się słynnymi klasztorami w Meteorach wzniesionymi na skałach zawieszonych między niebem a ziemią. Odbędziecie również romantyczny rejs łodzią po turkusowych zatokach wyspy Diaporos i zregenerujecie siły na najpiękniejszych piaszczystych plażach Półwyspu Sytonia.
        </p>

        <div class="highlights-box">
            <h3 class="section-title" style="font-size: 1.5rem; text-align: left; margin-bottom: 20px;">Miejsca które Was zachwycą</h3>
            <ul class="custom-list">
                <li>Mityczny Olimp oraz spektakularny wąwóz Enipeas w Litochoro.</li>
                <li>Unikalne w skali świata klasztory w Meteorach usytuowane na skałach.</li>
                <li>Park wodospadów w Edesie.</li>
                <li>Panoramiczne widoki ze starego miasta Ano Poli w Salonikach.</li>
                <li>Romantyczny rejs łodzią wokół wyspy Diaporos z kąpielą w Błękitnej Lagunie.</li>
                <li>Magiczny wieczór w tradycyjnej tawernie przy dźwiękach greckiej muzyki na żywo.</li>
                <li>Błogi wypoczynek na lazurowych plażach Półwyspu Sytonia.</li>
            </ul>
        </div>

        <div id="map-container">
            <h3 class="section-title" style="font-size: 1.5rem; text-align: left; margin-bottom: 15px;">Mapa Trasy i Atrakcji</h3>
            <div id="map"></div>
        </div>

        <h2 class="section-title">Dzienny Program Wyjazdu</h2>

        <div class="day-card">
            <div class="day-title">Dzień 1. Przylot do Salonik i przejazd na Riwierę Olimpijską</div>
            <div class="day-body">
                Po przylocie na lotnisko w Salonikach odbierzecie samochód z wypożyczalni. To jest czas, aby rozpocząć Waszą grecką przygodę! Jedziecie w stronę Riwiery Olimpijskiej, do miejsca Waszej pierwszej bazy noclegowej.
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 2. Masyw Olimpu, Wąwóz Enipeas i malownicze Litochoro</div>
            <div class="day-body">
                Po śniadaniu w hotelu wyruszycie w stronę Masywu Olimpu. Rozpoczniecie od spaceru po urokliwym miasteczku Litochoro, które zbudowane jest w tradycyjnej zabudowie. Tam polecamy wstąpić na kawę do klimatycznej kawiarni na głównym rynku. Później czeka Was przyjemny trekking wzdłuż malowniczego wąwozu Enipeas. Dotrzecie do punktu Prionia na wysokości 1100 m n.p.m., skąd roztacza się zachwycający widok. Po drodze miniecie dawny klasztor św. Dionizego. W drugiej części dnia możecie odwiedzić ruiny zamku Platamonas lub zabytkową wieś Palaios Panteleimonas. Po zwiedzaniu czas na kolację w lokalnej restauracji i powrót do Waszego hotelu.
            </div>
            <div class="restaurants-box">
                <strong>Propozycje restauracji</strong>
                <ul>
                    <li>Gastrodromio En Olympo w Litochoro – <a href="https://maps.app.goo.gl/pkuJJ4LR58Ky7osM9" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Ta Mezedakia – <a href="https://maps.app.goo.gl/cMTbJx5bcYQLmAi18" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Psarokokkalo w Plaka Litochoro – <a href="https://maps.app.goo.gl/q6jSr1u5EKiVCJaZ6" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 3. Wycieczka do Słynnych Klasztorów w Meteorach</div>
            <div class="day-body">
                Po śniadaniu wyruszycie na jednodniową wycieczkę do słynnych Meteorów. Odkryjecie majestatyczne monastyry wybudowane na pionowych skałach i zwiedzicie wybrane wnętrza klasztorne. W ciągu dnia będziecie mogli zatrzymać się w kawiarni z panoramicznym widokiem na skały. Przed wieczornym powrotem polecamy obejrzeć zachód słońca nad doliną z punktu widokowego Psaropetra. Na noc wracacie do swojego hotelu w okolicy Riwiery Olimpijskiej.
            </div>
            <div class="restaurants-box">
                <strong>Propozycje restauracji</strong>
                <ul>
                    <li>Meteoron Panorama w Kalambace – <a href="https://maps.app.goo.gl/owsoqVRnNGJt1uNa8?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Valia Calda w Kalambace – <a href="https://maps.app.goo.gl/sFJ6ZpmbB2KJWZ7N9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Meteora Restaurant w Kalambace – <a href="https://maps.app.goo.gl/SKhiHV71KekeYkNL7?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 4. Wodospady Edesy, przejazd na Chalkidiki</div>
            <div class="day-body">
                Po śniadaniu wykwaterujecie się z hotelu i przejedziecie do malowniczej Edesy, aby podziwiać słynny park przyrodniczy oraz szumiące wodospady. Możecie wypić kawę w lokalu tuż obok kaskad wodnych. Następnie przejedziecie do Salonik i wjedziecie na wzgórze Ano Poli, skąd rozpościera się panorama całego miasta. Popołudnie spędzicie na spacerze po historycznej dzielnicy Ladadika. Wieczorem polecamy zasiąść w tradycyjnej greckiej tawernie na wyjątkową kolację połączoną z koncertem muzyki na żywo. Po wieczornych atrakcjach przejedziecie do waszej drugiej bazy noclegowej w okolicy Półwyspu Sytonia.
            </div>
            <div class="restaurants-box">
                <strong>Propozycje restauracji</strong>
                <ul>
                    <li>Palati – <a href="https://maps.app.goo.gl/M2zQVZrGPk2yT7956?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 5. Czas na relaksik</div>
            <div class="day-body">
                Pierwszy dzień totalnego lenistwa. Robicie to, na co macie ochotę! Jeśli nabierzecie ochoty na małą wyprawę, możecie pojechać na krótką wycieczkę do zabytkowej miejscowości Afytos na Półwyspie Kasandra, słynącej z tradycyjnej kamiennej zabudowy. Zatrzymacie się tam na kawę i deser w urokliwym miejscu na klifie z niesamowitym widokiem na morze.
            </div>
            <div class="restaurants-box">
                <strong>Propozycje restauracji</strong>
                <ul>
                    <li>Thea Thalassa w Afytos – <a href="https://maps.app.goo.gl/2pEKnwc7viM1W9BE9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Strouboulis Restaurant w Afytos – <a href="https://maps.app.goo.gl/6bqJBqwUZtuZ6pg8A?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Notos All Day Bar w Afytos – <a href="https://maps.app.goo.gl/Ne7chDvgkTjBkpyXA?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 6. Słoneczny relaks i kąpiele na lazurowych plażach</div>
            <div class="day-body">
                Czas przeznaczony na pełny wypoczynek. Oddacie się relaksowi na piaszczystych plażach Sytonii słynących z krystalicznie czystej wody.
            </div>
            <div class="restaurants-box">
                <strong>Propozycje restauracji</strong>
                <ul>
                    <li>Tzitzikas w Porto Koufo – <a href="https://maps.app.goo.gl/4f3jLs7XMGVwHTFMA" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Paidiko Sxoleio w Sarti – <a href="https://maps.app.goo.gl/3bbzcjLES72wm3Pb9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 7. Rejs łodzią na Wyspę Diaporos</div>
            <div class="day-body">
                Po śniadaniu czeka Was wyjątkowa morska przygoda! Wyruszycie w rejs łodzią wokół wyspy Diaporos oraz bezludnych wysepek archipelagu Vourvourou. Będziecie kąpać się w słynnej Błękitnej Lagunie i odkrywać ukryte plaże dostępne wyłącznie od strony morza. W południe odpoczniecie przy kawie w uroczej kawiarence nadmorskiej, a na kolację ze świeżo złowioną rybą wyruszycie do sprawdzonej tawerny rybnej.
            </div>
            <div class="restaurants-box">
                <strong>Propozycje restauracji</strong>
                <ul>
                    <li>Aristos Fish Restaurant w Ormos Panagias – <a href="https://maps.app.goo.gl/PXc2hTGzumAuUuHy8?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Taverna Akrogiali w Vourvourou – <a href="https://maps.app.goo.gl/yJ3szyiZ9LriBMsA9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 8. Perły Salonik i powrót do Polski</div>
            <div class="day-body">
                Po śniadaniu i wymeldowaniu z hotelu przejedziecie do serca Salonik. Zwiedzicie reprezentacyjny plac Arystotelesa oraz zobaczycie słynną Białą Wieżę stojącą przy nadmorskim bulwarze, skąd roztacza się piękny widok z tarasu. Wypijecie pożegnalną kawę w starym porcie z widokiem na całe miasto. Zrobicie ostatnie zakupy greckich specjałów, oliwy oraz przypraw na tradycyjnym targu. Następnie przejedziecie na lotnisko w Salonikach, zwrócicie samochód i odlecicie do Warszawy.
            </div>
            <div class="restaurants-box">
                <strong>Propozycje restauracji</strong>
                <ul>
                    <li>Brunchsin – <a href="https://maps.app.goo.gl/f2SDTfcpmY2QHfD87?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Mpakal – <a href="https://maps.app.goo.gl/tdm54XoaKvpKTRnz6?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Full tou Meze – <a href="https://maps.app.goo.gl/sJZhRLLwbg5WRvpq6?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <p style="text-align: center; font-style: italic; color: var(--text-muted); margin-bottom: 40px;">Program ramowy. Kolejność może ulec zmianie.</p>

        <div class="grid-two">
            <div class="info-card">
                <h3>Propozycje noclegów</h3>
                <strong style="color: var(--accent); display: block; margin-bottom: 8px;">Okolice Riwiery Olimpijskiej</strong>
                <ul class="custom-list" style="margin-bottom: 20px;">
                    <li>ZOI Girni - Seaside Hotel – <a href="https://www.booking.com/Share-ZZDsIMr" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Olympus Mediterranean Boutique Hotel – <a href="https://www.booking.com/Share-t9Mc9h" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Xenios Dias Boutique Hotel – <a href="https://www.booking.com/Share-To5sOwj" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>

                <strong style="color: var(--accent); display: block; margin-bottom: 8px;">Okolice Sytonii</strong>
                <ul class="custom-list">
                    <li>Saint George Sithonia – <a href="https://www.booking.com/Share-5uigr8C" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Angelina Hotel – <a href="https://www.booking.com/Share-3t21ey" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Alegria Suites – <a href="https://www.booking.com/Share-jlo7am" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Casa Panorama Adults Only – <a href="https://www.booking.com/Share-Yk6ocX" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Assa Maris Beach Hotel – <a href="https://www.booking.com/Share-TIIhD9" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>

            <div class="info-card">
                <h3>Wynajęcie samochodu & Płatne atrakcje</h3>
                <strong style="color: var(--accent); display: block; margin-bottom: 8px;">Wynajęcie samochodu</strong>
                <p style="margin-bottom: 20px; font-size: 0.95rem;">
                    Rezerwacja pojazdu poprzez Potos Car Rentals – <a href="https://share.google/C06e8YoUTvZHIkLzN" target="_blank" rel="noopener">tu jestem</a>.
                </p>

                <strong style="color: var(--accent); display: block; margin-bottom: 8px;">Płatne atrakcje</strong>
                <ul class="custom-list">
                    <li>Klasztory w Meteorach – koszt wstępu wynosi około 3–5 EUR za osobę za wejście do jednego wybranego klasztoru. Bilety kupuje się bezpośrednio w kasie przy wejściu do danego obiektu.</li>
                    <li>Biała Wieża w Salonikach – koszt biletów wstępu wynosi około 6 EUR za osobę. Wejściówki można nabyć w kasie na miejscu.</li>
                    <li>Zamek Platamonas – wstęp kosztuje około 4 EUR za osobę. Bilety kupuje się w kasie przy wejściu do twierdzy.</li>
                    <li>Rejs łodzią na Wyspę Diaporos i Błękitną Lagunę – udział w wycieczce morskiej ze sternikiem kosztuje około 25–35 EUR za osobę. Wynajem prywatnej motorówki bez patentu na cały dzień to koszt od około 80–120 EUR plus paliwo. Rezerwacja wycieczek na platformie GetYourGuide – <a href="https://share.google/oLdcs7qHq0xC2eqUv" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="info-card" style="margin-bottom: 40px;">
            <h3>Uwagi praktyczne</h3>
            <ul class="custom-list">
                <li>Do podróży do Grecji dla obywateli polskich wymagany jest ważny dowód osobisty lub paszport.</li>
                <li>Warto posiadać Europejską Kartę Ubezpieczenia Zdrowotnego wydawaną bezpłatnie przez NFZ.</li>
                <li>Do zwiedzania obiektów sakralnych w Meteorach wymagany jest odpowiedni strój z zakrytymi ramionami oraz kolanami.</li>
                <li>Zalecamy zabranie wygodnego obuwia sportowego na szlaki wokół Olimpu.</li>
            </ul>
        </div>

    </div>

    <footer>
        &copy; 2026 Biuro Podróży Pacia Travel. Wszystkie prawa zastrzeżone. Program wycieczki poślubnej do Północnej Grecji.
    </footer>

    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script>
        const map = L.map('map').setView([40.35, 22.80], 8);

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; OpenStreetMap contributors'
        }).addTo(map);

        const locations = [
            { name: "Saloniki", type: "Miasto", lat: 40.6401, lng: 22.9444 },
            { name: "Litochoro", type: "Miasto", lat: 40.1057, lng: 22.5024 },
            { name: "Masyw Olimpu", type: "Atrakcja", lat: 40.0822, lng: 22.4061 },
            { name: "Meteory", type: "Atrakcja", lat: 39.7217, lng: 21.6306 },
            { name: "Edesa", type: "Wodospady", lat: 40.8030, lng: 22.0478 },
            { name: "Afytos", type: "Miasto", lat: 40.0984, lng: 23.4358 },
            { name: "Półwysep Sytonia", type: "Plaże", lat: 40.1888, lng: 23.7788 },
            { name: "Wyspa Diaporos", type: "Rejs", lat: 40.2185, lng: 23.7842 }
        ];

        locations.forEach(loc => {
            L.marker([loc.lat, loc.lng])
                .addTo(map)
                .bindPopup(`<b>${loc.name}</b><br>${loc.type}`);
        });
    </script>

</body>
</html>
