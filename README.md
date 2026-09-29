# ♿ code-along-accessibility-260930

Fem sidor från en simklubb, en tillgänglighetsbrist i taget. Vi lagar dem tillsammans under passet.

Sidorna **ser helt normala ut**. Det är hela poängen: ingen av bristerna märks om man har mus, ser bra och tittar med ögat. Alla märks direkt om man inte har det.

Greppen är desamma som ni behöver på **torsdagens workshop**, och kraven är desamma som i **u01**. Varje avsnitt säger vilken ticket det hör till.

Facit ligger i `code-along-accessibility-260930-solution`. Titta där efter att vi gått igenom avsnittet.

---

## 🏗️ 1-semantik

Sidan är en påse `div`. Noll landmärken, ingen `h1`, och två element som bara ser ut som rubriker.

1. Öppna den. Den ser normal ut.
2. Byt ut `div`-arna mot `header`, `nav`, `main` och `footer`.
3. Rätta rubrikhierarkin. En `h1` per sida, sedan i ordning utan hopp.
4. Kontrollera i DevTools → Elements → Accessibility.

Rubriknivån väljs efter **struktur**, aldrig efter hur stor texten ska se ut. Storleken sätter ni i CSS.

→ Ticket **A11Y-6**

## 🖼️ 2-alt-texter

Tre bilder, tre olika fel: logotypen har en lång beskrivning trots att namnet står i text bredvid, fotot har `alt="bild"`, och skiljelinjen saknar `alt` helt.

Fråga er för varje bild: **bär den information som inte redan finns i texten?**

Tom `alt=""` är inte samma sak som inget `alt`. Tom säger åt skärmläsaren att hoppa över bilden. Saknas attributet läser många i stället upp filnamnet.

→ Ticket **A11Y-9**

## 🎨 3-kontrast

Listan visar vilka grupper som har platser kvar. Två fel:

1. Statusen syns **bara** som en färgad prick.
2. Ingressen och ramarna har för svag kontrast.

Mät med DevTools färgväljare. Gissa inte. 4,5:1 för brödtext, 3:1 för ramar och ikoner.

**Lighthouse hittar fel 2 men inte fel 1.** Färg som enda bärare kräver att en människa tittar. Det är därför ni aldrig kan lita på att ett grönt Lighthouse betyder att sidan är tillgänglig.

→ Ticket **A11Y-7** och **A11Y-8**

## ⌨️ 4-tangentbord

Lägg undan musen och tabba. Ni kommer **ingenstans** — sidan har noll fokuserbara element.

1. Räkna tabbstoppen. Svaret är noll.
2. Byt ut `div`-arna. Fråga för varje: **utför** den något, eller **leder** den någonstans? Det första är en `button`, det andra en `a href`.
3. Sätt tillbaka fokusmarkeringen med `:focus-visible`.
4. Lägg till en "hoppa till innehållet"-länk som första tabbstopp.
5. Tabba igenom igen.

→ Ticket **A11Y-2** och **A11Y-3**

## 📝 5-formular

Sex fel: inga labels, alla fält är `type="text"`, radioknapparna är inte grupperade, texterna bredvid dem är `span`, felrutan är en tom röd remsa, och skicka-knappen är en `div`.

**Testa så här:** fyll i hela formuläret utan mus. Piltangenter i radiogruppen, mellanslag på kryssrutan. Klicka sedan på varje etikett — hamnar markören i fältet sitter kopplingen.

Ett stavfel i `for` eller `id` bryter kopplingen **tyst**. Inget felmeddelande, allt ser rätt ut, men skärmläsaren säger bara "textfält".

→ Ticket **A11Y-1**, **A11Y-4** och **A11Y-5**

---

## 🎯 Efter passet

- Testa **er egen u01-sida** med enbart tangentbord. Kommer ni åt allt? Ser ni var fokus ligger?
- [learn-a11y.netlify.app](https://learn-a11y.netlify.app/) — praktisk guide för utvecklare
- [WCAG 2.2 quickref](https://www.w3.org/WAI/WCAG22/quickref/) — alla kriterier, filtrerbara

Fråga i kanalen om något krånglar!
