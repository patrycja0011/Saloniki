<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Słoneczna Macedonia i Półwysep Chalkidiki – Grecka Podróż Poślubna</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Playfair+Display:ital,wght@0,600;0,700;1,400&display=swap" rel="stylesheet">
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

        header {
            background: linear-gradient(rgba(10, 37, 64, 0.85), rgba(0, 119, 145, 0.8)), url('https://images.unsplash.com/photo-1533105079780-92b9be482077?auto=format&fit=crop&w=1920&q=80') center/cover no-repeat;
            color: #FFFFFF;
            padding: 80px 20px;
            text-align: center;
        }

        .header-content {
            max-width: 900px;
            margin: 0 auto;
        }

        .badge {
            display: inline-block;
            background-color: var(--gold);
            color: var(--primary);
            padding: 6px 16px;
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
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(8px);
            padding: 12px 24px;
            border-radius: 12px;
            font-size: 0.95rem;
            border: 1px solid rgba(255, 255, 255, 0.2);
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
            margin-bottom: 40px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
        }

        .titles-box h3 {
            color: var(--primary);
            margin-bottom: 15px;
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

        .highlights-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 50px;
        }

        .highlight-card {
            background: var(--card-bg);
            padding: 24px;
            border-radius: 12px;
            border: 1px solid var(--border);
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.03);
            transition: transform 0.2s ease;
        }

        .highlight-card:hover {
            transform: translateY(-3px);
        }

        .highlight-card h4 {
            color: var(--accent);
            margin-bottom: 8px;
            font-size: 1.1rem;
        }

        .viewpoints-section {
            background: linear-gradient(135deg, #0A2540 0%, #007791 100%);
            color: #FFFFFF;
            padding: 40px;
            border-radius: 16px;
            margin-bottom: 50px;
            box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
        }

        .viewpoints-section h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: var(--gold);
            text-align: center;
        }

        .viewpoints-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 15px;
            list-style: none;
        }

        .viewpoint-item {
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.15);
            font-size: 0.9rem;
        }

        .viewpoint-item strong {
            color: #FFFFFF;
            display: block;
            margin-bottom: 4px;
        }

        .day-card {
            background: var(--card-bg);
            border-radius: 12px;
            border: 1px solid var(--border);
            padding: 30px;
            margin-bottom: 25px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.03);
        }

        .day-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--light-bg);
            padding-bottom: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .day-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.4rem;
            color: var(--primary);
        }

        .day-body {
            font-size: 0.98rem;
            color: var(--text-dark);
            margin-bottom: 20px;
        }

        .day-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 12px;
            background-color: var(--light-bg);
            padding: 15px;
            border-radius: 8px;
            font-size: 0.88rem;
        }

        .detail-item {
            display: flex;
            flex-direction: column;
        }

        .detail-label {
            font-weight: 700;
            color: var(--text-muted);
            text-transform: uppercase;
            font-size: 0.75rem;
            margin-bottom: 2px;
        }

        .detail-value {
            color: var(--primary);
            font-weight: 600;
        }

        .practical-box, .pricing-box {
            background: var(--card-bg);
            border-radius: 12px;
            border: 1px solid var(--border);
            padding: 35px;
            margin-bottom: 30px;
        }

        .custom-list {
            list-style: none;
        }

        .custom-list li {
            position: relative;
            padding-left: 25px;
            margin-bottom: 12px;
            font-size: 0.95rem;
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

        .price-split {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
        }

        .price-column {
            background: var(--light-bg);
            padding: 25px;
            border-radius: 8px;
            border-top: 4px solid var(--accent);
        }

        .price-column.not-included {
            border-top-color: #E11D48;
        }

        .price-column h4 {
            font-family: 'Playfair Display', serif;
            font-size: 1.3rem;
            margin-bottom: 15px;
            color: var(--primary);
        }

        footer {
            background-color: var(--primary);
            color: #FFFFFF;
            text-align: center;
            padding: 30px 20px;
            font-size: 0.85rem;
            opacity: 0.9;
        }

        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .day-header { flex-direction: column; align-items: flex-start; }
            .viewpoints-section { padding: 25px; }
        }
    </style>
</head>
<body>

    <header>
        <div class="header-content">
            <span class="badge">Grecka Podróż Poślubna 2026</span>
            <h1>Słoneczna Macedonia i Półwysep Chalkidiki</h1>
            <p class="subtitle">Mityczny Olimp, Klasztory Meteorów, Rejs na Wyspę Diaporos oraz Relaks w Dwu Bazach Noclegowych</p>
            
            <div class="quick-stats">
                <div class="stat-card">✈️ Wylot z Warszawy (LOT)</div>
                <div class="stat-card">🚗 Wynajęty Samochód w Cenie</div>
                <div class="stat-card">🏨 2 Komfortowe Bazy BB (3*/4*)</div>
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
            <p><strong>Warszawa – Saloniki – Litochoro – Masyw Olimpu – Meteory – Edesa – Półwysep Sytonia – Rejs na Diaporos – Saloniki – Warszawa</strong></p>
        </div>

        <div class="info-foreign">
            Osoby mieszkające poza granicami Polski, serdecznie zapraszamy do kontaktu z naszym biurem. Z przyjemnością przygotujemy indywidualną kalkulację przelotu z dowolnego portu lotniczego na świecie.
        </div>

        <h2 class="section-title">Wstęp Prosprzedażowy i SEO</h2>
        <p class="section-subtitle">
            Zapraszamy na wyjątkową grecką wyprawę łączącą fascynującą historię, mityczne krajobrazy oraz beztroski wypoczynek nad brzegiem Morza Egejskiego z zachowaniem pełnego komfortu dwóch baz noclegowych. Podczas tego wyjazdu odkryjemy tajemnice mitycznego Masywu Olimpu, przejdziemy urokliwymi szlakami w Litochoro oraz zachwycimy się słynnymi klasztorami w Meteorach wzniesionymi na skałach zawieszonych między niebem a ziemią. Odbędziemy romantyczny rejs łodzią po turkusowych zatokach wyspy Diaporos, spędzimy klimatyczny wieczór przy dźwiękach greckiej muzyki na żywo i zregenerujemy siły na najpiękniejszych piaszczystych plażach Półwyspu Sytonia. To idealnie wyważony program stworzony z myślą o osobach poszukujących zachwycających widoków, urokliwych kawiarni oraz wygody bez konieczności częstej zmiany hoteli.
        </p>

        <h2 class="section-title">Dlaczego warto? (Highlighty)</h2>
        <div class="highlights-grid">
            <div class="highlight-card">
                <h4>🏨 Dwie Bazy Noclegowe</h4>
                <p>Wygodne zakwaterowanie oparte na zaledwie dwóch komfortowych bazach noclegowych na całej trasie wyjazdu.</p>
            </div>
            <div class="highlight-card">
                <h4>🏔️ Mityczny Olimp</h4>
                <p>Wyprawa u stóp mitycznego Masywu Olimpu oraz spacer spektakularnym wąwozem Enipeas w Litochoro.</p>
            </div>
            <div class="highlight-card">
                <h4>🏛️ Monastery w Chmurach</h4>
                <p>Jednodniowa wycieczka do unikalnych w skali świata klasztorów w Meteorach usytuowanych na monumentalnych skałach.</p>
            </div>
            <div class="highlight-card">
                <h4>💧 Szumiące Wodospady</h4>
                <p>Odkrywanie orzeźwiającego parku wodospadów w Edesie oraz panoramiczne widoki ze starego miasta Ano Poli w Salonikach.</p>
            </div>
            <div class="highlight-card">
                <h4>⛵ Rejs po Błękitnej Lagunie</h4>
                <p>Romantyczny rejs łodzią wokół wyspy Diaporos z kąpielą w lazurowych wodach archipelagu Vourvourou.</p>
            </div>
            <div class="highlight-card">
                <h4>🎶 Wieczór z Muzyką na Żywo</h4>
                <p>Magiczny wieczór w tradycyjnej tawernie w Salonikach przy dźwiękach greckiej muzyki na żywo na buzuki.</p>
            </div>
        </div>

        <div class="viewpoints-section">
            <h3>📸 Wyselekcjonowane Punkty Widokowe na Trasie</h3>
            <div class="viewpoints-list">
                <div class="viewpoint-item">
                    <strong>Punkt Psaropetra (Meteory)</strong>
                    Spektakularna panorama całej doliny i klasztorów zawieszonych na skałach o zachodzie słońca.
                </div>
                <div class="viewpoint-item">
                    <strong>Ano Poli i Twierdza (Saloniki)</strong>
                    Najwyższe wzgórze starego miasta z widokiem na całe Saloniki, port i Zatokę Termajską.
                </div>
                <div class="viewpoint-item">
                    <strong>Balkon Kasandry (Afytos)</strong>
                    Urokliwa promenada na klifie z widokiem na lazurową taflę morza z dużej wysokości.
                </div>
                <div class="viewpoint-item">
                    <strong>Palaios Panteleimonas</strong>
                    Tradycyjna wieś na zboczu góry z widokiem na całe wybrzeże i Zamek Platamonas.
                </div>
                <div class="viewpoint-item">
                    <strong>Punkt Prionia (Olimp)</strong>
                    Wysokość 1100 m n.p.m. z widokiem na potężne szczyty Olimpu i głęboki Wąwóz Enipeas.
                </div>
                <div class="viewpoint-item">
                    <strong>Górska Wieś Parthenonas</strong>
                    Tradycyjna osada w gajach oliwnych z najpiękniejszym zachodem słońca nad Zatoką Toroneos.
                </div>
            </div>
        </div>

        <h2 class="section-title">Dzienny Program Wyjazdu</h2>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 1. Przylot do Salonik i przejazd na Riwierę Olimpijską</div>
            </div>
            <div class="day-body">
                Spotykamy się na lotnisku w Warszawie, skąd odlatujemy bezpośrednim rejsem do Salonik. Po przylocie na lotnisko i odbiorze samochodu z wypożyczalni rozpoczynamy naszą grecką przygodę. Udamy się w trasę przejazdową w stronę pierwszej bazy noclegowej u stóp Masywu Olimpu. W trakcie drogi zatrzymamy się w kameralnej kawiarni nadmorskiej na pierwszą grecką kawę frapu. Zasiądziemy do wspólnej kolacji w lokalnej tawernie Kyma na wybrzeżu, gdzie skosztujemy tradycyjnych greckich mezedes i świeżych ryb. Przejdziemy na kolację i nocleg w okolicy Riwiery Olimpijskiej.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Nocleg BB</span><span class="detail-value">Baza 1 – Okolice Litochoro (Mythic Valley / Olympus Med.)</span></div>
                <div class="detail-item"><span class="detail-label">Kawa & Deser</span><span class="detail-value">Kawiarnia nadmorska przy plaży w Gritsa</span></div>
                <div class="detail-item"><span class="detail-label">Gdzie zjeść</span><span class="detail-value">Tawerna Kyma nad brzegiem morza</span></div>
            </div>
        </div>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 2. Mityczny Masyw Olimpu, Wąwóz Enipeas i malownicze Litochoro</div>
            </div>
            <div class="day-body">
                Po śniadaniu wyruszymy w stronę mitycznego Masywu Olimpu. Rozpoczniemy od spaceru po urokliwym miasteczku Litochoro z tradycyjną zabudową, gdzie wstąpimy na kawę do klimatycznej kawiarni Navagios na głównym rynku. Udamy się na przyjemny trekking ścieżką wzdłuż malowniczego wąwozu Enipeas, docierając do punktu Prionia. Miniemy po drodze dawny Monastyr św. Dionizego. Po południu odwiedzimy ruiny zamku Platamonas górującego nad wybrzeżem lub zabytkową wieś Palaios Panteleimonas. Wieczorem wybierzemy się do cenionej restauracji Gastrodromio En Olympo w Litochoro. Przejdziemy na kolację i nocleg w okolicy Riwiery Olimpijskiej.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Nocleg BB</span><span class="detail-value">Baza 1 – Okolice Litochoro</span></div>
                <div class="detail-item"><span class="detail-label">Punkt widokowy</span><span class="detail-value">Punkt Prionia (1100 m n.p.m.) oraz Palaios Panteleimonas</span></div>
                <div class="detail-item"><span class="detail-label">Gdzie zjeść</span><span class="detail-value">Restauracja Gastrodromio En Olympo</span></div>
            </div>
        </div>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 3. Wycieczka do Słynnych Klasztorów w Meteorach</div>
            </div>
            <div class="day-body">
                Po śniadaniu wyruszymy z naszej bazy na jednodniową wyprawę do słynnych Meteorów. Odkryjemy majestatyczne monastery wybudowane na pionowych skałach piaskowcowych i zwiedzimy wybrane wnętrza klasztorne. Zapoznamy się z tradycją pisania ikon w lokalnej pracowni, a w ciągu dnia zatrzymamy się na kawę w kawiarni Eagle's Nest z panoramicznym widokiem na skały. Przed wieczornym powrotem obejrzymy zachód słońca nad doliną z punktu Psaropetra, a na kolację udamy się do tawerny Gardenia w urokliwej miejscowości Kastraki. Po kolacji powrócimy na nocleg do naszej pierwszej bazy w okolicy Riwiery Olimpijskiej.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Nocleg BB</span><span class="detail-value">Baza 1 – Okolice Riwiery Olimpijskiej</span></div>
                <div class="detail-item"><span class="detail-label">Punkt widokowy</span><span class="detail-value">Punkt Psaropetra nad skałami Meteorów</span></div>
                <div class="detail-item"><span class="detail-label">Gdzie zjeść</span><span class="detail-value">Tawerna Gardenia w Kastraki</span></div>
            </div>
        </div>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 4. Wodospady Edesy, Wieczór w Salonikach i Przejazd na Sytonię</div>
            </div>
            <div class="day-body">
                Po śniadaniu wykwaterujemy się z pierwszej bazy i przejedziemy do malowniczej Edesy, aby podziwiać słynny park przyrodniczy oraz szumiące wodospady. Wypijemy kawę w kawiarni Katarraktes usytuowanej tuż obok kaskad wodnych. Następnie przejedziemy do Salonik i wjedziemy na wzgórze Ano Poli, skąd rozpościera się panorama całego miasta. Popołudnie spędzimy na spacerze po historycznej dzielnicy Ladadika. Wieczorem zasiądziemy w tradycyjnej greckiej tawernie na wyjątkową kolację połączoną z koncertem muzyki na żywo na buzuki. Po kolacji przejedziemy do naszej drugiej bazy noclegowej w okolicy Półwyspu Sytonia.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Nocleg BB</span><span class="detail-value">Baza 2 – Półwysep Sytonia (Serenity Suites / Lily Ann)</span></div>
                <div class="detail-item"><span class="detail-label">Punkt widokowy</span><span class="detail-value">Wzgórze Ano Poli w Salonikach & Klif w Edesie</span></div>
                <div class="detail-item"><span class="detail-label">Gdzie zjeść</span><span class="detail-value">Tawerna Full tou Meze (muzyka na żywo)</span></div>
            </div>
        </div>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 5. Urokliwe Afytos i Wjazd na Półwysep Sytonia</div>
            </div>
            <div class="day-body">
                Po śniadaniu w naszej nowej bazie wyruszymy na krótką wycieczkę do zabytkowej miejscowości Afytos na Półwyspie Kasandra, słynnej z kamiennej zabudowy. Zatrzymamy się na kawę i deser w kawiarni Notos All Day Bar położonej na klifie z niesamowitym widokiem na morze. Po południu powrócimy na Półwysep Sytonia, słynący z piniowych lasów oraz ukrytych zatoczek. Na wieczorną kolację wybierzemy się do tawerny rybnej Aristos w miejscowości Ormos Panagias, gdzie zjemy owoce morza przy samej wodzie. Przejdziemy na kolację i nocleg w okolicy Półwyspu Sytonia.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Nocleg BB</span><span class="detail-value">Baza 2 – Półwysep Sytonia</span></div>
                <div class="detail-item"><span class="detail-label">Punkt widokowy</span><span class="detail-value">Promenada na klifie w Afytos</span></div>
                <div class="detail-item"><span class="detail-label">Gdzie zjeść</span><span class="detail-value">Tawerna rybna Aristos w Ormos Panagias</span></div>
            </div>
        </div>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 6. Słoneczny Relaks i Kąpiele na Lazurowych Plażach Sytonii</div>
            </div>
            <div class="day-body">
                Po śniadaniu rozpoczynamy czas przeznaczony na pełny, stacjonarny wypoczynek. Oddamy się relaksowi na piaszczystych plażach Sytonii, takich jak Karidi czy Vourvourou, słynących z krystalicznie czystej wody. W ciągu dnia wstąpimy do klimatycznego baru przy plaży na chłodzone napoje i lekkie przekąski. Wieczorem zrobimy spacer po urokliwym portowym miasteczku i zasiądziemy do kolacji w tradycyjnej tawernie Paris bezpośrednio na piaszczystym brzegu. Przejdziemy na kolację i nocleg w okolicy Półwyspu Sytonia.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Nocleg BB</span><span class="detail-value">Baza 2 – Półwysep Sytonia</span></div>
                <div class="detail-item"><span class="detail-label">Plaże</span><span class="detail-value">Karidi Beach, Vourvourou, Lagonisi</span></div>
                <div class="detail-item"><span class="detail-label">Gdzie zjeść</span><span class="detail-value">Tawerna Paris bezpośrednio na plaży</span></div>
            </div>
        </div>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 7. Kameralny Rejs Łodzią na Wyspę Diaporos i Grecki Styl Życia</div>
            </div>
            <div class="day-body">
                Po śniadaniu czeka nas wyjątkowa morska przygoda. Wyruszymy w kameralny rejs łodzią wokół wyspy Diaporos oraz bezludnych wysepek archipelagu Vourvourou. Będziemy kąpać się w słynnej Błękitnej Lagunie i odkrywać ukryte plaże dostępne wyłącznie od strony morza. W południe odpoczniemy przy kawie w uroczej kawiarence nadmorskiej w Toroni, a na wyśmienitą kolację ze świeżo złowioną rybą wyruszymy do tawerny Panos Fish Taverna. Przejdziemy na kolację i nocleg w okolicy Półwyspu Sytonia.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Nocleg BB</span><span class="detail-value">Baza 2 – Półwysep Sytonia</span></div>
                <div class="detail-item"><span class="detail-label">Atrakcja morska</span><span class="detail-value">Rejs na wyspę Diaporos & Błękitna Laguna</span></div>
                <div class="detail-item"><span class="detail-label">Gdzie zjeść</span><span class="detail-value">Panos Fish Taverna w Toroni</span></div>
            </div>
        </div>

        <div class="day-card">
            <div class="day-header">
                <div class="day-title">Dzień 8. Perły Salonik i Powrót do Polski</div>
            </div>
            <div class="day-body">
                Po śniadaniu i wymeldowaniu z drugiej bazy przejedziemy do serca Salonik. Zwiedzimy reprezentacyjny plac Arystotelesa oraz zobaczymy słynną Białą Wieżę stojącą przy nadmorskim bulwarze. Wypijemy pożegnalną kawę w kawiarni Kitchen Bar przy starym porcie z widokiem na całe miasto. Zrobimy ostatnie zakupy greckich specjałów, oliwy oraz przypraw na tradycyjnym targu Kapani. Następnie przejedziemy na lotnisko w Salonikach, zwrócimy samochód i odlecimy do Warszawy.
            </div>
            <div class="day-details">
                <div class="detail-item"><span class="detail-label">Punkt widokowy</span><span class="detail-value">Taras widokowy na Białej Wieży</span></div>
                <div class="detail-item"><span class="detail-label">Pożegnalna kawa</span><span class="detail-value">Kitchen Bar w Starym Porcie</span></div>
                <div class="detail-item"><span class="detail-label">Wylot</span><span class="detail-value">Godzina 18:25 z lotniska Saloniki (SKG)</span></div>
            </div>
        </div>

        <p style="text-align: center; font-style: italic; color: var(--text-muted); margin-bottom: 40px;">Program ramowy. Kolejność może ulec zmianie.</p>

        <div class="practical-box">
            <h3 class="section-title" style="font-size: 1.6rem; text-align: left; margin-bottom: 20px;">Uwagi praktyczne</h3>
            <ul class="custom-list">
                <li>Do podróży do Grecji dla obywateli polskich wymagany jest ważny dowód osobisty lub paszport.</li>
                <li>Warto posiadać Europejską Kartę Ubezpieczenia Zdrowotnego (EKUZ) wydawaną bezpłatnie przez NFZ.</li>
                <li>W Grecji obowiązują standardowe gniazdka elektryczne typu C i F, zatem adaptery prądu nie są wymagane.</li>
                <li>Do zwiedzania obiektów sakralnych w Meteorach wymagany jest odpowiedni strój z zakrytymi ramionami oraz kolanami.</li>
                <li>Zalecamy zabranie wygodnego obuwia sportowego na szlaki wokół Olimpu oraz obuwia do wody na rejs i plaże.</li>
                <li>Systemy słuchawkowe Audio Tour Guide. Każdy uczestnik otrzyma zestaw słuchawkowy, który pozwoli na wyraźne słuchanie informacji przekazywanych przez przewodnika. Zestaw Audio Tour Guide rozda i zbierze od Państwa pilot wyjazdu.</li>
                <li>Możliwość zgłoszenia diet specjalnych (np. wegetariańskiej, bezglutenowej) podczas dokonywania rezerwacji.</li>
            </ul>
        </div>

        <div class="pricing-box">
            <h3 class="section-title" style="font-size: 1.6rem; text-align: left; margin-bottom: 25px;">Zestawienie Świadczeń</h3>
            
            <div class="price-split">
                <div class="price-column">
                    <h4>Cena zawiera</h4>
                    <ul class="custom-list">
                        <li>Przelot na trasie Polska – Saloniki – Polska z bagażem podręcznym 40x20x30 cm.</li>
                        <li>7 noclegów w hotelach o standardzie 3* lub 4* w dwóch bazach noclegowych w pokojach 2/3-osobowych z łazienkami.</li>
                        <li>Wyżywienie wg programu.</li>
                        <li>Wynajem samochodu na cały okres pobytu z podstawowym pakietem ubezpieczeń.</li>
                        <li>Ubezpieczenie Signal Iduna KL z chorobami przewlekłymi 30 000 EUR, NNW 15 000 PLN, BP 1000 PLN.</li>
                        <li>Opiekę pilota wycieczek.</li>
                    </ul>
                </div>

                <div class="price-column not-included">
                    <h4>Cena nie zawiera</h4>
                    <ul class="custom-list">
                        <li>Bagażu rejestrowanego 23 kg (możliwość dopłaty podczas rezerwacji).</li>
                        <li>Paliwa, opłat drogowych oraz parkingów (szacowany koszt ok. 520–600 PLN na samochód).</li>
                        <li>Biletów wstępu do zwiedzanych obiektów (Meteory, Biała Wieża, Zamek Platamonas).</li>
                        <li>Kosztów udziału w rejsie łodzią oraz kolacji z muzyką na żywo.</li>
                        <li>Napojów do kolacji oraz wydatków własnych.</li>
                    </ul>
                </div>
            </div>
        </div>

    </div>

    <footer>
        &copy; 2026 Biuro Podróży. Wszystkie prawa zastrzeżone. Program wycieczki poślubnej do Północnej Grecji.
    </footer>

</body>
</html>
