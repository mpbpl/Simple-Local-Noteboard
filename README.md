# Simple Local Noteboard

English | [Polski](#polski)

A single-file, offline kanban-style noteboard. Open one HTML file in your browser: no installation, no server, no dependencies, no network access.

Columns hold cards; cards hold any number of text blocks (descriptions) and lists; list items hold free-form fields (name, price, link, deadline, anything you define).

<img width="1752" height="877" alt="screen noteboard" src="https://github.com/user-attachments/assets/efc7acb9-9ac8-408f-a3e7-573425db3607" />


## Features

- Dark theme, kanban layout with user-defined columns
- Cards with an unlimited number of blocks: descriptions (multi-line text) and lists, in any order
- List items with free fields added per item (label + value), laid out left to right
- Links (values starting with `http://` or `https://`) get a clickable arrow `↗`
- Done status per item (struck through and dimmed) and deletion with confirmation
- Drag and drop with the `⠿` handle: columns, cards (also between columns), blocks within a card, items (within a list and between lists of the same card)
- Collapsible cards
- Optional block header: hide or show the title with the `T−` / `T+` button
- `Enter` in an item field creates a new item directly below
- Text fields grow automatically, so the whole content is always visible
- Autosave to the browser (`localStorage`) plus JSON export and import

Not included: search, sorting, undo.

## Quick start

1. Download `index.html` (or clone the repository).
2. Open it in a browser (developed and used in Firefox; other modern browsers should work, not verified).
3. Add a column, a card, then blocks and items.

## Data and backup

- Data is stored in the browser's `localStorage` under the key `nb`. It never leaves your machine.
- `localStorage` is tied to the browser profile and, for local files, may be tied to the file's path. Moving the file, changing a drive letter, clearing site data, or private mode can leave you with an empty board.
- **Use `Export JSON` regularly** and keep the exported file next to the HTML file. `Import JSON` replaces the current board after confirmation.
- Do not commit your exported JSON files to a public repository if they contain personal data.

### JSON format

```json
{
  "cols": [
    {
      "id": "a1", "name": "Column",
      "cards": [
        {
          "id": "b2", "title": "Card", "collapsed": false,
          "blocks": [
            { "id": "c3", "title": "Description", "text": "Free text" },
            {
              "id": "d4", "title": "List", "hh": false,
              "items": [
                { "id": "e5", "done": false,
                  "fields": [ { "k": "name", "v": "Hiking boots" },
                              { "k": "price", "v": "499" },
                              { "k": "link", "v": "https://example.com" } ] }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

A block with `items` is a list, a block with `text` is a description. `hh: true` hides the block title. Ids are arbitrary unique strings.

## Run online with GitHub Pages (optional)

The app works locally; Pages only gives you a URL.

1. Keep the file named `index.html` in the repository root.
2. Repository **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`, Save.
3. After a short build the page is available at `https://<your-user>.github.io/<repository>/`.

Note: data on the Pages address is stored separately from the local copy (different origin). To move a board, use Export JSON and Import JSON.

## Development

One file, vanilla HTML/CSS/JS, no build step. The whole state is a single object `S` rendered by `R()`; changes go through a small action table and are saved on every edit.

## License

MIT. Use it however you like, modify and share it; just keep the copyright notice and license text, which credits the original author. See [LICENSE](LICENSE).

Original project by MPBPL.

---

## Polski

Jednoplikowy, offline'owy noteboard w układzie kanban. Wystarczy otworzyć jeden plik HTML w przeglądarce: bez instalacji, serwera, zależności i dostępu do sieci.

Kolumny zawierają karty; karty zawierają dowolną liczbę bloków tekstowych (opisów) i list; pozycje list mają dowolne pola (nazwa, cena, link, termin, cokolwiek zdefiniujesz).

<img width="1752" height="877" alt="screen noteboard" src="https://github.com/user-attachments/assets/2a8cbf84-529f-452a-932e-3a42c8abe8f5" />


### Funkcje

- Ciemny motyw, układ kanban z kolumnami definiowanymi przez użytkownika
- Karty z dowolną liczbą bloków: opisów (tekst wieloliniowy) i list, w dowolnej kolejności
- Pozycje list z polami dodawanymi osobno dla każdej pozycji (etykieta + wartość), układanymi w poziomie
- Linki (wartości zaczynające się od `http://` lub `https://`) dostają klikalną strzałkę `↗`
- Status wykonania pozycji (przekreślenie i przyciemnienie) oraz usuwanie z potwierdzeniem
- Przeciąganie uchwytem `⠿`: kolumny, karty (także między kolumnami), bloki w obrębie karty, pozycje (w liście i między listami tej samej karty)
- Zwijanie kart
- Opcjonalny nagłówek bloku: ukrywanie i pokazywanie tytułu przyciskiem `T−` / `T+`
- `Enter` w polu pozycji tworzy nową pozycję bezpośrednio poniżej
- Pola tekstowe rozszerzają się automatycznie, cała treść jest zawsze widoczna
- Autozapis w przeglądarce (`localStorage`) oraz eksport i import JSON

Brak: wyszukiwania, sortowania, cofania zmian.

### Szybki start

1. Pobierz `index.html` (lub sklonuj repozytorium).
2. Otwórz w przeglądarce (rozwijany i używany w Firefoxie; inne nowoczesne przeglądarki powinny działać, nie zweryfikowano).
3. Dodaj kolumnę, kartę, następnie bloki i pozycje.

### Dane i kopia zapasowa

- Dane są zapisywane w `localStorage` przeglądarki pod kluczem `nb` i nie opuszczają Twojego komputera.
- `localStorage` jest związany z profilem przeglądarki, a dla plików lokalnych może zależeć od ścieżki pliku. Przeniesienie pliku, zmiana litery dysku, czyszczenie danych witryn lub tryb prywatny mogą skutkować pustą tablicą.
- **Regularnie używaj `Eksport JSON`** i trzymaj wyeksportowany plik obok pliku HTML. `Import JSON` zastępuje bieżącą tablicę po potwierdzeniu.
- Nie dodawaj wyeksportowanych plików JSON do publicznego repozytorium, jeśli zawierają dane osobiste.

#### Format JSON

```json
{
  "cols": [
    {
      "id": "a1", "name": "Kolumna",
      "cards": [
        {
          "id": "b2", "title": "Karta", "collapsed": false,
          "blocks": [
            { "id": "c3", "title": "Opis", "text": "Dowolny tekst" },
            {
              "id": "d4", "title": "Lista", "hh": false,
              "items": [
                { "id": "e5", "done": false,
                  "fields": [ { "k": "nazwa", "v": "Buty turystyczne" },
                              { "k": "cena", "v": "499" },
                              { "k": "link", "v": "https://example.com" } ] }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

Blok z `items` jest listą, blok z `text` jest opisem. `hh: true` ukrywa tytuł bloku. Identyfikatory to dowolne unikalne ciągi znaków.

### Uruchomienie online przez GitHub Pages (opcjonalnie)

Aplikacja działa lokalnie; Pages daje tylko adres URL.

1. Zachowaj plik o nazwie `index.html` w katalogu głównym repozytorium.
2. Repozytorium **Settings → Pages → Build and deployment → Source: Deploy from a branch**, gałąź `main`, folder `/ (root)`, Save.
3. Po krótkiej budowie strona jest dostępna pod `https://<twoj-uzytkownik>.github.io/<repozytorium>/`.

Uwaga: dane pod adresem Pages są przechowywane oddzielnie od lokalnej kopii (inne źródło). Aby przenieść tablicę, użyj Eksport JSON i Import JSON.

### Rozwój

Jeden plik, czysty HTML/CSS/JS, bez budowania. Cały stan to jeden obiekt `S` renderowany przez `R()`; zmiany przechodzą przez małą tablicę akcji i zapisują się przy każdej edycji.

### Licencja

MIT. Używaj, modyfikuj i udostępniaj dowolnie; zachowaj tylko informację o prawach autorskich i tekst licencji, który wskazuje oryginalnego autora. Zobacz [LICENSE](LICENSE).

Oryginalny projekt: MPBPL

[↑ English](#simple-local-noteboard)
