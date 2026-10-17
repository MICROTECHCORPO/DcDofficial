# Certificate NFC — Phygital Authenticity Standard

## Cel
Każdy produkt fizyczny z linii DilloCrocodilo (bluzy, czapki, młynki, zapalniczki, karty, figurki) otrzymuje wbudowany, niepowtarzalny identyfikator phygital, który potwierdza autentyczność, śledzi historię własności i umożliwia przydzielenie nagród tokenowych (Memecoin / punkty lojalnościowe).

## Komponenty techniczne

- Tag NFC: NTAG213 lub NTAG215/NTAG216 zależnie od pojemności metadanych. Preferowany NTAG213 dla podstawowych UID i NTAG215 przy konieczności większej pamięci.
- Format zapisu: JSON-LD zoptymalizowany pod URL + podpis HMAC.
- UID: surowy UID chipu (UID) + produkcyjny serial (prod_serial) składają się na unikatowy product_hash.
- Off-chain certificate: JSON z polami: product_id, edition, serial, manufacture_date, maker_batch, auth_signature.

## Schemat danych (przykład)

{
  "@context": "https://schema.org/",
  "type": "ProductCertificate",
  "product_id": "dcd-APP-000123",
  "serial": "S-2026-000123",
  "uid": "04A1B2C3D4",
  "edition": "Genesis",
  "manufacture_date": "2026-10-01",
  "auth_signature": "BASE64(HMAC-SHA256(...))",
  "meta": {
    "material": "cotton-450gsm",
    "variant": "black-hoodie-3D-puff"
  }
}

## Proces weryfikacji (UX)
1. Użytkownik przykłada telefon (NFC) lub skanuje QR wygrawerowany na produkcie.
2. Aplikacja odczytuje UID/QR i pobiera zweryfikowany off-chain certificate z API projektu.
3. Backend weryfikuje auth_signature (HMAC lub ECDSA) i porównuje hash z rekordem produkcyjnym.
4. Po potwierdzeniu autentyczności domyślnie przydzielane są bonusy: darmowy memecoin (ilość zdefiniowana w produkcie) lub punkty lojalnościowe na konto użytkownika.

## Bezpieczeństwo
- Podpisy: stosować HMAC-SHA256 z kluczem serwisowym (przechowywany w tajnym vault).
- Rotacja kluczy: klucze podpisujące rotować co kwartał; zachować mapę starych kluczy w celu weryfikacji starszych certyfikatów.
- Nie zapisywać na tagu kluczy ani poufnych danych — jedynie UID i wskazanie na zasób off-chain (skrót lub URL).

## Warianty implementacyjne
- Lite: NTAG213 z UID i krótkim URL wskazującym na zasób certyfikatu.
- Full: NTAG215 z większym JSON-LD zapisanym bezpośrednio na tagu + podpis skrótu certyfikatu.

## Integracja z tokenami (Memecoin)
- Przy pierwszym odczycie i weryfikacji przypisać do konta użytkownika darmowy pakiet memecoinów lub punktów (np. 10 DDC/100 points).
- Zdarzenia odczytu logować do off-chain ledger (timestamp, device_id, buyer_id) w celu zapobiegania nadużyciom.

## Przydatne zasady operacyjne
- Ograniczyć liczbę darmowych nagród do 1 na serial, aby zapobiec nadużyciom.
- Implementować rate-limiting i CAPTCHA dla endpointów, które udostępniają link do aktywacji certyfikatu.

## Przykładowe endpointy API
- GET /v1/certificates/{serial} — zwraca certificate JSON + verification status
- POST /v1/certificates/{serial}/claim — powiąż nagrodę tokenową z kontem użytkownika

## Uwagi prawne
- Zapisuj minimalne dane osobowe do celów przyznawania nagród zgodnie z RODO; preferuj model „claim by wallet” zamiast wymagania podawania danych osobowych.
