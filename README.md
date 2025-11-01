<!doctype html>
<html lang="pl">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>List do Gwiazdora</title>
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&amp;family=Poppins:wght@400;600&amp;display=swap" rel="stylesheet">
  <script src="/_sdk/element_sdk.js"></script>
  <style>
    body {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      height: 100%;
      overflow-x: hidden;
    }

    html {
      height: 100%;
    }

    #loading-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #c41e3a 0%, #8b0000 100%);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      transition: opacity 0.5s ease-out;
    }

    #loading-screen.hidden {
      opacity: 0;
      pointer-events: none;
    }

    .title {
      font-family: 'Pacifico', cursive;
      font-size: 3.5rem;
      color: #2d5016;
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.8), 0 0 20px rgba(255, 255, 255, 0.6), 3px 3px 6px rgba(0, 0, 0, 0.3);
      margin-bottom: 3rem;
      text-align: center;
      padding: 0 1rem;
    }

    .loading-bar-container {
      width: 80%;
      max-width: 500px;
      height: 40px;
      background: white;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
      position: relative;
    }

    .loading-bar {
      height: 100%;
      width: 0%;
      background: repeating-linear-gradient(
        45deg,
        #ffffff,
        #ffffff 10px,
        #c41e3a 10px,
        #c41e3a 20px
      );
      transition: width 0.3s ease;
      border-radius: 20px;
    }

    .loading-text {
      color: white;
      font-size: 1.2rem;
      margin-top: 1.5rem;
      text-align: center;
      font-weight: 600;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    }

    #letter-screen {
      min-height: 100%;
      background: linear-gradient(135deg, #c41e3a 0%, #8b0000 100%);
      padding: 2rem 1rem;
      display: none;
    }

    #letter-screen.visible {
      display: block;
    }

    .letter-container {
      max-width: 600px;
      margin: 0 auto;
      background: #f5f5dc;
      border-radius: 15px;
      padding: 2.5rem;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
      position: relative;
    }

    .letter-container::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 30px;
      background: repeating-linear-gradient(
        90deg,
        #c41e3a,
        #c41e3a 20px,
        transparent 20px,
        transparent 40px
      );
      border-radius: 15px 15px 0 0;
    }

    .letter-intro {
      font-size: 1.3rem;
      color: #333;
      margin-bottom: 2rem;
      margin-top: 1rem;
      line-height: 1.6;
      font-style: italic;
    }

    .gift-item {
      background: white;
      border-radius: 12px;
      padding: 1.5rem;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    .gift-title {
      font-size: 1.4rem;
      color: #2d5016;
      font-weight: 600;
      margin-bottom: 1rem;
    }

    .gift-image-container {
      width: 100%;
      max-width: 300px;
      margin: 0 auto 1rem;
      aspect-ratio: 1;
      overflow: hidden;
      border-radius: 10px;
      background: #f9f9f9;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .gift-image {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .gift-price {
      font-size: 1.8rem;
      color: #c41e3a;
      font-weight: 600;
      margin-bottom: 1rem;
    }

    .gift-link {
      display: inline-block;
      background: #2d5016;
      color: white;
      padding: 0.8rem 1.5rem;
      border-radius: 8px;
      text-decoration: none;
      font-weight: 600;
      transition: background 0.3s ease;
    }

    .gift-link:hover {
      background: #1a3009;
    }

    @media (max-width: 768px) {
      .title {
        font-size: 2.5rem;
      }

      .letter-container {
        padding: 1.5rem;
      }

      .letter-intro {
        font-size: 1.1rem;
      }

      .gift-title {
        font-size: 1.2rem;
      }

      .gift-price {
        font-size: 1.5rem;
      }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <div id="loading-screen">
   <div class="title" id="main-title">
    List do Gwiazdora
   </div>
   <div class="loading-bar-container">
    <div class="loading-bar" id="loading-bar"></div>
   </div>
   <div class="loading-text" id="loading-text">
    Ładowanie Listu…
   </div>
  </div>
  <div id="letter-screen">
   <div class="letter-container">
    <p class="letter-intro" id="letter-intro">Drogi Gwiazdorze, z racji że byłem bardzo grzeczny chciałbym dostać kilka prezentów…</p>
    <div class="gift-item">
     <div class="gift-title" id="gift-title">
      Lalka Barbie Fashionistas nr. 240
     </div>
     <div class="gift-image-container"><img src="zdjęcie_1.png" alt="Lalka Barbie Fashionistas" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
     </div>
     <div class="gift-price" id="gift-price">
      59,90zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-fashionistas-nr-240-mattel-17660340186" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-2">
      Lalka Barbie Fashionistas nr. 144
     </div>
     <div class="gift-image-container"><img src="zdjęcie_2.png" alt="Lalka Barbie Fashionistas nr. 144" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
     </div>
     <div class="gift-price" id="gift-price-2">
      39,95zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-fashionistas-gyb00-nr-144-mattel-12318319017" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-2">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-3">
      Lalka Barbie Fashionistas Afro
     </div>
     <div class="gift-image-container"><img src="zdjęcie_3.png" alt="Lalka Barbie Fashionistas Afro" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
     </div>
     <div class="gift-price" id="gift-price-3">
      34,99zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-fashion-sukienka-wieczorowy-roz-barbie-65-30-cm-17182424645" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-3">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-4">
      Barbie w koku
     </div>
     <div class="gift-image-container"><img src="zdjęcie_4.png" alt="Barbie w koku" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
     </div>
     <div class="gift-price" id="gift-price-4">
      46,90zł
     </div><a href="https://allegro.pl/oferta/barbie-fjf40-lalka-modne-przyjaciolki-fashionistas-12577058239" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-4">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-5">
      Lalka Barbie Fashionistas z 2015 roku
     </div>
     <div class="gift-image-container" style="position: relative;"><img src="zdjęcie_5.png" alt="Lalka Barbie Fashionistas z 2015 roku" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
      <div style="position: absolute; top: 10px; right: 10px; background: #ff6b6b; color: white; padding: 8px 12px; border-radius: 20px; font-size: 0.8rem; font-weight: bold; text-shadow: none; box-shadow: 0 2px 8px rgba(0,0,0,0.3);">
       BARDZO BYM CHCIAŁ
      </div>
     </div>
     <div class="gift-price" id="gift-price-5">
      64,39zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-fashionistas-15-doll-mattel-3-17950313665" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-5">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-6">
      Barbie Fashionistas #215
     </div>
     <div class="gift-image-container" style="position: relative;"><img src="zdjęcie_6.png" alt="Barbie Fashionistas #215" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
      <div style="position: absolute; top: 10px; right: 10px; background: #ff6b6b; color: white; padding: 8px 12px; border-radius: 20px; font-size: 0.8rem; font-weight: bold; text-shadow: none; box-shadow: 0 2px 8px rgba(0,0,0,0.3);">
       BARDZO BYM CHCIAŁ
      </div>
     </div>
     <div class="gift-price" id="gift-price-6">
      45,00zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-fashionistas-215-hrh13-styl-rockowy-14963371131" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-6">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-7">
      Barbie z cukrzycą
     </div>
     <div class="gift-image-container" style="position: relative;"><img src="Zdjęcie_7.png" alt="Barbie z cukrzycą" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
      <div style="position: absolute; top: 10px; right: 10px; background: #ff6b6b; color: white; padding: 8px 12px; border-radius: 20px; font-size: 0.8rem; font-weight: bold; text-shadow: none; box-shadow: 0 2px 8px rgba(0,0,0,0.3);">
       BARDZO BYM CHCIAŁ
      </div>
     </div>
     <div class="gift-price" id="gift-price-7">
      59,99zł
     </div><a href="https://allegro.pl/oferta/barbie-lalka-z-cukrzyca-typu-1-hyt" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-7">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-8">
      Barbie z ubrankami
     </div>
     <div class="gift-image-container"><img src="zdjęcie_8.png" alt="Barbie z ubrankami" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
     </div>
     <div class="gift-price" id="gift-price-8">
      59,99zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-fashionistas-zestaw-ubranek-mattel-prezent-dla-dziecka-15144855234" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-8">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-9">
      Lalka Barbie ciemno skóra w koku
     </div>
     <div class="gift-image-container"><img src="zdjęcie_9.png" alt="Lalka Barbie ciemno skóra w koku" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
     </div>
     <div class="gift-price" id="gift-price-9">
      47,46zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-fashionistas-nr-198-mattel-hjr" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-9">Zobacz na Allegro</a>
    </div>
    <div class="gift-item" style="margin-top: 2rem;">
     <div class="gift-title" id="gift-title-10">
      Barbie Extra #19
     </div>
     <div class="gift-image-container"><img src="zdjęcie_10.png" alt="Barbie Extra #19" class="gift-image" onerror="this.src=''; this.alt='Zdjęcie prezentu'; this.style.display='none';">
     </div>
     <div class="gift-price" id="gift-price-10">
      59,90zł
     </div><a href="https://allegro.pl/oferta/lalka-barbie-extra-19-w-stroju-pop-punk-zwierzatko-panda-12928602178" target="_blank" rel="noopener noreferrer" class="gift-link" id="gift-link-10">Zobacz na Allegro</a>
    </div>
    <p class="letter-outro" id="letter-outro" style="font-size: 1.2rem; color: #333; margin-top: 2.5rem; line-height: 1.6; font-style: italic; text-align: center; padding: 1.5rem; background: rgba(255,255,255,0.7); border-radius: 10px;">Drogi Gwiazdorze, byłbym bardzo wdzięczny gdybyś wybrał którąś z tych lalek, zwłaszcza że byłem w tym roku mega grzeczny. Proszę abyś prezenty dostarczył pod adres Rychława 52 lub Świecie, ul. Bema 1. Pozdrawiam, Kacperek.</p>
    <p class="letter-ps" id="letter-ps" style="font-size: 1rem; color: #666; margin-top: 1.5rem; line-height: 1.5; text-align: center; padding: 1rem; background: rgba(255,255,255,0.5); border-radius: 8px; border-left: 4px solid #c41e3a;">P.S. Lista prezentów może się zmienić, a także ceny tych produktów mogą się zwiększyć lub zmniejszyć w zależności od ofert.</p>
   </div>
  </div>
  <script>
    const defaultConfig = {
      main_title: "List do Gwiazdora",
      letter_intro: "Drogi Gwiazdorze, z racji że byłem bardzo grzeczny chciałbym dostać kilka prezentów…",
      gift_title: "Lalka Barbie Fashionistas nr. 240",
      gift_price: "59,90zł",
      gift_link: "https://allegro.pl/oferta/lalka-barbie-fashionistas-nr-240-mattel-17660340186",
      gift_title_2: "Lalka Barbie Fashionistas nr. 144",
      gift_price_2: "39,95zł",
      gift_link_2: "https://allegro.pl/oferta/lalka-barbie-fashionistas-gyb00-nr-144-mattel-12318319017",
      gift_title_3: "Lalka Barbie Fashionistas Afro",
      gift_price_3: "34,99zł",
      gift_link_3: "https://allegro.pl/oferta/lalka-barbie-fashion-sukienka-wieczorowy-roz-barbie-65-30-cm-17182424645",
      gift_title_4: "Barbie w koku",
      gift_price_4: "46,90zł",
      gift_link_4: "https://allegro.pl/oferta/barbie-fjf40-lalka-modne-przyjaciolki-fashionistas-12577058239",
      gift_title_5: "Lalka Barbie Fashionistas z 2015 roku",
      gift_price_5: "64,39zł",
      gift_link_5: "https://allegro.pl/oferta/lalka-barbie-fashionistas-15-doll-mattel-3-17950313665",
      gift_title_6: "Barbie Fashionistas #215",
      gift_price_6: "45,00zł",
      gift_link_6: "https://allegro.pl/oferta/lalka-barbie-fashionistas-215-hrh13-styl-rockowy-14963371131",
      gift_title_7: "Barbie z cukrzycą",
      gift_price_7: "59,99zł",
      gift_link_7: "https://allegro.pl/oferta/barbie-lalka-z-cukrzyca-typu-1-hyt",
      gift_title_8: "Barbie z ubrankami",
      gift_price_8: "59,99zł",
      gift_link_8: "https://allegro.pl/oferta/lalka-barbie-fashionistas-zestaw-ubranek-mattel-prezent-dla-dziecka-15144855234",
      gift_title_9: "Lalka Barbie ciemno skóra w koku",
      gift_price_9: "47,46zł",
      gift_link_9: "https://allegro.pl/oferta/lalka-barbie-fashionistas-nr-198-mattel-hjr",
      gift_title_10: "Barbie Extra #19",
      gift_price_10: "59,90zł",
      gift_link_10: "https://allegro.pl/oferta/lalka-barbie-extra-19-w-stroju-pop-punk-zwierzatko-panda-12928602178",
      letter_outro: "Drogi Gwiazdorze, byłbym bardzo wdzięczny gdybyś wybrał którąś z tych lalek, zwłaszcza że byłem w tym roku mega grzeczny. Proszę abyś prezenty dostarczył pod adres Rychława 52 lub Świecie, ul. Bema 1. Pozdrawiam, Kacperek.",
      letter_ps: "P.S. Lista prezentów może się zmienić, a także ceny tych produktów mogą się zwiększyć lub zmniejszyć w zależności od ofert.",
      background_color: "#c41e3a",
      title_color: "#2d5016",
      text_color: "#333333",
      accent_color: "#2d5016",
      link_color: "#2d5016",
      font_family: "Poppins",
      font_size: 16
    };

    const loadingTexts = [
      "Ładowanie Listu…",
      "Dokładne Przetwarzanie każdego życzenia…",
      "Sprawdzanie listy grzecznych dzieci…",
      "Konsultacja z elfami…",
      "Pakowanie magii świątecznej…",
      "Dodawanie blasku gwiazdki…",
      "Prawie gotowe…"
    ];

    let currentTextIndex = 0;
    let progress = 0;
    const totalDuration = 12000;
    const updateInterval = 100;
    const progressPerUpdate = (100 / (totalDuration / updateInterval));

    const loadingBar = document.getElementById('loading-bar');
    const loadingText = document.getElementById('loading-text');
    const loadingScreen = document.getElementById('loading-screen');
    const letterScreen = document.getElementById('letter-screen');

    const loadingInterval = setInterval(() => {
      progress += progressPerUpdate;
      
      if (progress >= 100) {
        progress = 100;
        clearInterval(loadingInterval);
        
        setTimeout(() => {
          loadingScreen.classList.add('hidden');
          letterScreen.classList.add('visible');
        }, 500);
      }
      
      loadingBar.style.width = progress + '%';
      
      const textChangePoint = Math.floor(progress / (100 / loadingTexts.length));
      if (textChangePoint !== currentTextIndex && textChangePoint < loadingTexts.length) {
        currentTextIndex = textChangePoint;
        loadingText.textContent = loadingTexts[currentTextIndex];
      }
    }, updateInterval);

    async function onConfigChange(config) {
      const mainTitle = document.getElementById('main-title');
      const letterIntro = document.getElementById('letter-intro');
      const letterOutro = document.getElementById('letter-outro');
      const letterPs = document.getElementById('letter-ps');
      
      // Get all gift elements
      for (let i = 1; i <= 10; i++) {
        const suffix = i === 1 ? '' : `-${i}`;
        const giftTitle = document.getElementById(`gift-title${suffix}`);
        const giftPrice = document.getElementById(`gift-price${suffix}`);
        const giftLink = document.getElementById(`gift-link${suffix}`);
        
        if (giftTitle) giftTitle.textContent = config[`gift_title${suffix === '' ? '' : '_' + i}`] || defaultConfig[`gift_title${suffix === '' ? '' : '_' + i}`];
        if (giftPrice) giftPrice.textContent = config[`gift_price${suffix === '' ? '' : '_' + i}`] || defaultConfig[`gift_price${suffix === '' ? '' : '_' + i}`];
        if (giftLink) giftLink.href = config[`gift_link${suffix === '' ? '' : '_' + i}`] || defaultConfig[`gift_link${suffix === '' ? '' : '_' + i}`];
      }

      const backgroundColor = config.background_color || defaultConfig.background_color;
      const titleColor = config.title_color || defaultConfig.title_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const linkColor = config.link_color || defaultConfig.link_color;
      const customFont = config.font_family || defaultConfig.font_family;
      const baseSize = config.font_size || defaultConfig.font_size;

      mainTitle.textContent = config.main_title || defaultConfig.main_title;
      letterIntro.textContent = config.letter_intro || defaultConfig.letter_intro;
      if (letterOutro) letterOutro.textContent = config.letter_outro || defaultConfig.letter_outro;
      if (letterPs) letterPs.textContent = config.letter_ps || defaultConfig.letter_ps;

      loadingScreen.style.background = `linear-gradient(135deg, ${backgroundColor} 0%, #8b0000 100%)`;
      letterScreen.style.background = `linear-gradient(135deg, ${backgroundColor} 0%, #8b0000 100%)`;
      mainTitle.style.color = titleColor;
      document.querySelectorAll('.gift-title').forEach(el => el.style.color = titleColor);
      letterIntro.style.color = textColor;
      if (letterOutro) letterOutro.style.color = textColor;
      if (letterPs) letterPs.style.color = textColor;
      document.querySelectorAll('.gift-link').forEach(el => el.style.background = linkColor);

      const baseFontStack = 'sans-serif';
      document.body.style.fontFamily = `${customFont}, ${baseFontStack}`;
      
      mainTitle.style.fontSize = `${baseSize * 2.2}px`;
      loadingText.style.fontSize = `${baseSize * 1.2}px`;
      letterIntro.style.fontSize = `${baseSize * 1.3}px`;
      if (letterOutro) letterOutro.style.fontSize = `${baseSize * 1.2}px`;
      if (letterPs) letterPs.style.fontSize = `${baseSize * 1}px`;
      document.querySelectorAll('.gift-title').forEach(el => el.style.fontSize = `${baseSize * 1.4}px`);
      document.querySelectorAll('.gift-price').forEach(el => el.style.fontSize = `${baseSize * 1.8}px`);
      document.querySelectorAll('.gift-link').forEach(el => el.style.fontSize = `${baseSize}px`);
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => {
                config.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => config.title_color || defaultConfig.title_color,
              set: (value) => {
                config.title_color = value;
                window.elementSdk.setConfig({ title_color: value });
              }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => {
                config.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            },
            {
              get: () => config.link_color || defaultConfig.link_color,
              set: (value) => {
                config.link_color = value;
                window.elementSdk.setConfig({ link_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => config.font_family || defaultConfig.font_family,
            set: (value) => {
              config.font_family = value;
              window.elementSdk.setConfig({ font_family: value });
            }
          },
          fontSizeable: {
            get: () => config.font_size || defaultConfig.font_size,
            set: (value) => {
              config.font_size = value;
              window.elementSdk.setConfig({ font_size: value });
            }
          }
        }),
        mapToEditPanelValues: (config) => new Map([
          ["main_title", config.main_title || defaultConfig.main_title],
          ["letter_intro", config.letter_intro || defaultConfig.letter_intro],
          ["gift_title", config.gift_title || defaultConfig.gift_title],
          ["gift_price", config.gift_price || defaultConfig.gift_price],
          ["gift_link", config.gift_link || defaultConfig.gift_link],
          ["gift_title_2", config.gift_title_2 || defaultConfig.gift_title_2],
          ["gift_price_2", config.gift_price_2 || defaultConfig.gift_price_2],
          ["gift_link_2", config.gift_link_2 || defaultConfig.gift_link_2],
          ["gift_title_3", config.gift_title_3 || defaultConfig.gift_title_3],
          ["gift_price_3", config.gift_price_3 || defaultConfig.gift_price_3],
          ["gift_link_3", config.gift_link_3 || defaultConfig.gift_link_3],
          ["gift_title_4", config.gift_title_4 || defaultConfig.gift_title_4],
          ["gift_price_4", config.gift_price_4 || defaultConfig.gift_price_4],
          ["gift_link_4", config.gift_link_4 || defaultConfig.gift_link_4],
          ["gift_title_5", config.gift_title_5 || defaultConfig.gift_title_5],
          ["gift_price_5", config.gift_price_5 || defaultConfig.gift_price_5],
          ["gift_link_5", config.gift_link_5 || defaultConfig.gift_link_5],
          ["gift_title_6", config.gift_title_6 || defaultConfig.gift_title_6],
          ["gift_price_6", config.gift_price_6 || defaultConfig.gift_price_6],
          ["gift_link_6", config.gift_link_6 || defaultConfig.gift_link_6],
          ["gift_title_7", config.gift_title_7 || defaultConfig.gift_title_7],
          ["gift_price_7", config.gift_price_7 || defaultConfig.gift_price_7],
          ["gift_link_7", config.gift_link_7 || defaultConfig.gift_link_7],
          ["gift_title_8", config.gift_title_8 || defaultConfig.gift_title_8],
          ["gift_price_8", config.gift_price_8 || defaultConfig.gift_price_8],
          ["gift_link_8", config.gift_link_8 || defaultConfig.gift_link_8],
          ["gift_title_9", config.gift_title_9 || defaultConfig.gift_title_9],
          ["gift_price_9", config.gift_price_9 || defaultConfig.gift_price_9],
          ["gift_link_9", config.gift_link_9 || defaultConfig.gift_link_9],
          ["gift_title_10", config.gift_title_10 || defaultConfig.gift_title_10],
          ["gift_price_10", config.gift_price_10 || defaultConfig.gift_price_10],
          ["gift_link_10", config.gift_link_10 || defaultConfig.gift_link_10],
          ["letter_outro", config.letter_outro || defaultConfig.letter_outro],
          ["letter_ps", config.letter_ps || defaultConfig.letter_ps]
        ])
      });
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'997e64a236be7a98',t:'MTc2MjAzMTU3NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
