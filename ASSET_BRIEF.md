# Бриф генерации ассетов — «Арабский с Аишей Умм Ханиф»

Все промпты — на английском (модели точнее следуют инструкциям на английском, даже когда просим арабскую вязь). Каждый ассет обязан использовать только цвета из `palette.md`. Выполняется локально через `higgsfield` CLI, залогиненный на вашей машине.

Общий синтаксис (замените на актуальные флаги вашей версии CLI, если отличаются):
```
higgsfield generate --model <model> --prompt "<prompt>" --negative "<negative>" --aspect <ratio> --out <path>
```

Рекомендуемая структура папок в проекте сайта:
```
assets/
  logo/
  photography/
  textures/
  patterns/
  icons/
  overlays/
  motion/
```

⚠️ Важно про арабский текст: генеративные модели часто искажают буквы арабской вязи (лишние точки, разорванные соединения). Для логотипа — генерируем ЧИСТУЮ ФОРМУ/монограм без читаемого текста, а точный вордмарк «أميرة اللغة العربية مع عائشة أم حنيف» / имя добавляем потом вручную в векторе (Illustrator/Figma) поверх сгенерированной формы. Не полагайтесь на модель в вопросе орфографии.

---

## БАЗА

### 1. Логотип — монограм (gpt_image_2)
**Назначение:** favicon, аватар, водяной знак.
**Prompt:**
> Minimal single continuous ink-brush stroke forming an abstract calligraphic monogram inspired by the Arabic letter Ha (ح), the curve echoing a desert dune silhouette. Clean vector-style linework, deep warm ink black (#1C1B17) on transparent background, no other text, no readable words, elegant and restrained, modern Islamic calligraphy aesthetic, centered composition, high contrast, crisp edges suitable for a logomark.
**Negative:** photorealistic, 3d render, gradient, multiple colors, clutter, readable Latin or Arabic text, mosque silhouette, green color, cartoonish
**Out:** `assets/logo/monogram.png` (transparent PNG, 2000x2000)

### 2. Логотип — горизонтальный лок-ап (gpt_image_2)
**Назначение:** шапка сайта.
**Prompt:**
> Elegant horizontal logo lockup: on the left, a minimal single-stroke ink calligraphic monogram (dune-curve abstract shape), on the right empty clean space reserved for a wordmark to be added manually. Warm ink black (#1C1B17) linework on transparent background, generous negative space, refined and quiet, editorial minimalism, no readable text anywhere in the image.
**Negative:** text, letters, words, gradients, clutter, photorealism
**Out:** `assets/logo/lockup-mark-only.png`

*(Вордмарк «Аиша» / бренд-нейм добавляется поверх вручную в векторном редакторе шрифтом, который вы выберете отдельно — современный, не "восточный клише" шрифт, как вы просили избегать.)*

### 3. Hero-фотография пустыни (nano_banana_pro)
**Назначение:** фон главного экрана.
**Prompt:**
> Cinematic wide desert landscape at golden sunrise, soft rolling sand dunes with long warm shadows, empty and serene, a single distant silhouette of a walking figure or camel caravan far on the ridge line suggesting a journey toward knowledge, warm cream and sand tones (#F5EEE0, #D8B48C, #8C5A34), deep teal-tinted shadows (#2F5D5A), soft golden light (#B8924A) grazing the dune crests, tranquil and spiritual atmosphere, no text, no people close-up, ultra-detailed, editorial travel photography style, 16:9.
**Negative:** oversaturated, tourist snapshot, harsh midday light, modern buildings, vehicles, text overlay, people in modern clothing close-up
**Out:** `assets/photography/hero-dunes-sunrise.jpg`

### 4. Базовая текстура пергамента (nano_banana_pro)
**Назначение:** фон под секции с текстом.
**Prompt:**
> Seamless flat-lay texture of aged cream parchment paper, subtle fiber grain, warm ivory tone (#F5EEE0), very faint sepia stains at edges, no text, no illustrations, soft even lighting, high resolution, suitable as a website section background, tileable.
**Negative:** torn edges, burnt paper, dark vignette, illustrations, text, stamps
**Out:** `assets/textures/parchment-base.jpg`

---

## ДОПОЛНИТЕЛЬНЫЕ АССЕТЫ

### 5. Оверлей — песчаная пыль на чёрном (nano_banana_pro)
**Назначение:** плавные переходы между секциями (blend mode screen/lighten).
**Prompt:**
> Fine drifting sand dust particles floating and swirling gently, photographed against pure solid black background, warm sand-gold color (#D8B48C, #B8924A) particles catching light, wispy and airy, no other elements, high contrast for easy screen-blend compositing, studio macro photography style.
**Negative:** smoke, fog, snow, colored lighting other than warm gold, people, objects
**Out:** `assets/overlays/sand-dust-on-black.png`

### 6. Оверлей — тёплое марево на белом (nano_banana_pro)
**Назначение:** лёгкое наложение на hero-фото для эффекта зноя.
**Prompt:**
> Subtle heat-haze shimmer texture, soft warm translucent waves, photographed against pure solid white background, faint golden-sand tint (#D8B48C), extremely soft and diffuse, no particles, no text, suitable for overlay blending on photographs.
**Negative:** hard edges, colored smoke, dark tones, objects
**Out:** `assets/overlays/heat-haze-on-white.png`

### 7-10. Текстур-пак фонов секций (nano_banana_pro, 4 шт.)
**Назначение:** разные фоны под разные секции (курсы, отзывы, о нас, контакты).

- **7. Макро-зерно песка дюны** — `assets/textures/sand-macro.jpg`
> Extreme macro close-up of fine desert sand dune surface, ripple patterns from wind, warm tones (#D8B48C, #8C5A34), soft directional light, shallow depth of field, no footprints, no objects, seamless-feel texture.

- **8. Чернильная растяжка** — `assets/textures/ink-wash.jpg`
> Abstract ink wash texture on cream paper, deep warm ink black (#1C1B17) diffusing softly into ivory parchment (#F5EEE0), organic flowing edges, calligraphic energy without forming letters, minimal and elegant, no text.

- **9. Состаренная бумага манускрипта** — `assets/textures/manuscript-paper.jpg`
> Aged manuscript paper texture, warm cream tone (#F5EEE0), faint foxing spots, soft deckled edge visible at one corner, no text, no illustrations, subtle and refined, suitable as website section background.

- **10. Тёмный чернильный фон** — `assets/textures/ink-dark.jpg`
> Deep warm ink-black textured background (#1C1B17), subtle brushed paper grain, very soft vignette, minimal and calm, no text, no objects, suitable for a dark website section.

### 11. Геометрический исламский паттерн (nano_banana_pro)
**Назначение:** тонкие разделители, бордюры, низкая непрозрачность.
**Prompt:**
> Seamless tileable geometric Islamic star pattern line-art, thin single-weight lines only, warm ink black (#1C1B17) on transparent background, restrained and minimal geometric star-and-polygon lattice, no color fill, no thick borders, elegant and quiet, vector-flat style.
**Negative:** thick lines, colorful, ornate filigree, 3d, gradient
**Out:** `assets/patterns/geometric-star-line.png`

### 12. Иконки-линии (gpt_image_2, набор из 5)
**Назначение:** значки для карточек курсов/фич.
**Prompt (для каждой, менять объект):**
> Minimal single-line icon of [open book / reed pen (qalam) / crescent moon / hourglass / date palm tree], continuous thin ink stroke, warm ink black (#1C1B17) on transparent background, no fill, no shading, consistent with a refined calligraphic monogram style, centered, simple geometric reduction.
**Out:** `assets/icons/{book,qalam,crescent,hourglass,palm}.png`

### 13. Макро-детали (nano_banana_pro)
**Назначение:** декоративные вставки в блоке "О курсе".
**Prompt:**
> Close-up macro photograph of a reed pen (qalam) resting on cream parchment paper with a single dark ink droplet beside it, warm natural light, shallow depth of field, warm ink black and cream tones only, no readable text visible, elegant and quiet still-life composition.
**Out:** `assets/photography/macro-qalam-ink.jpg`

### 14. Кадры окружения — силуэт пальмы (nano_banana_pro)
**Назначение:** фон блока "О преподавателе" / разделитель.
**Prompt:**
> Silhouette of a single date palm tree on a desert dune ridge against a warm sunset sky, gradient from deep teal (#2F5D5A) at top to warm gold (#B8924A) and sand (#D8B48C) near horizon, minimal and serene, no people, no text, cinematic wide composition.
**Out:** `assets/photography/palm-silhouette-sunset.jpg`

### 15. Кадры окружения — караван на гребне дюны (nano_banana_pro)
**Назначение:** фон hero альтернативный / блок "Наш путь".
**Prompt:**
> Small distant silhouette of a camel caravan walking along a desert dune ridge at dusk, vast empty sand landscape, warm muted tones (#D8B48C, #8C5A34, #2F5D5A shadows), sense of quiet journey and pilgrimage toward knowledge, no text, cinematic wide 21:9 composition.
**Out:** `assets/photography/caravan-ridge-dusk.jpg`

### 16. Движение — дрейф песка по дюне (seedance_2_0)
**Назначение:** зацикленное фоновое видео hero-секции.
**Prompt:**
> Slow, gentle drift of fine sand grains blowing along the crest of a desert dune at golden hour, seamless loopable motion, warm cream and sand tones, calm and meditative pace, no people, no camera cuts, soft cinematic light, subtle continuous wind movement only.
**Params:** loop: true, duration: 6-8s, aspect: 16:9
**Out:** `assets/motion/sand-drift-loop.mp4`

### 17. Движение — растекание чернил в воде (seedance_2_0)
**Назначение:** метафора распространения знания — переход между секциями / прелоадер.
**Prompt:**
> Macro shot of dark ink slowly diffusing and blooming in clear water against a plain cream background, organic swirling tendrils, warm ink black (#1C1B17) spreading softly, calm meditative pace, no text, no other objects, seamless loop potential.
**Params:** duration: 5-6s, aspect: 1:1 or 16:9
**Out:** `assets/motion/ink-diffusion.mp4`

### 18. Круглая печать-эмблема (gpt_image_2)
**Назначение:** блок отзывов/сертификатов.
**Prompt:**
> Minimal circular seal emblem in the style of an antique wax stamp, containing the abstract dune-curve monogram at center, thin decorative ring border with small geometric star motifs, single warm ink black (#1C1B17) color on transparent background, no readable text, refined and restrained, not gaudy.
**Out:** `assets/logo/seal-emblem.png`

### 19. Орнамент-разделитель (gpt_image_2)
**Назначение:** тонкая линия-разделитель между секциями.
**Prompt:**
> Minimal horizontal ornamental divider line, thin ink stroke with a small centered eight-pointed star or crescent flourish, warm ink black (#1C1B17) on transparent background, elegant and quiet, no other elements, wide and thin composition suitable as a website section divider.
**Out:** `assets/patterns/divider-ornament.png`

---

## Порядок работы
1. Прогоняете промпты через `higgsfield` локально, по 2-3 варианта на промпт.
2. Отбираете лучшие варианты, складываете в структуру папок выше внутри «Сайт - обучение арабскому».
3. Присылаете мне финальные файлы (или путь к папке) — я вошью их в код сайта (CSS/HTML/фреймворк — какой у вас используется).
4. Логотип с реальным арабским/русским текстом добираем вручную поверх сгенерированной формы в векторе — модели не гарантируют точность арабской орфографии.
