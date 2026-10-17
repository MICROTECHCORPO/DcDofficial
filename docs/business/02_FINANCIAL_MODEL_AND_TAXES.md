# Financial Model and Taxes — dokładny podział przy marce DilloCrocodilo

Poniżej przedstawiono precyzyjny rozdział kosztów i podatków dla przykładowej sprzedaży karty kolekcjonerskiej o cenie detalicznej 100 PLN.

## Założenia
- Cena sprzedaży (brutto): 100.00 PLN
- VAT: 23% (Polska)
- COGS (koszt produkcji): 20.00 PLN
- Prowizje płatności: 2.30 PLN (przykładowo 2.3%)
- Bonus klienta (Memecoin / lojalności): 15.00 PLN (wartość przypisana)
- Buyback & burn (DDC token): 5.00 PLN

## Obliczenia
1) Obowiązek VAT (23% od ceny netto)
   - Cena netto = Cena brutto / (1 + VAT) = 100 / 1.23 ≈ 81.30 PLN
   - VAT do odprowadzenia = 100 - 81.30 = 18.70 PLN

2) Rozbicie pozycji kosztowych (odliczane od ceny netto)
   - Cena netto: 81.30 PLN
   - COGS: 20.00 PLN
   - Prowizje płatności: 2.30 PLN
   - Bonus klienta (Memecoin): 15.00 PLN
   - Buyback & burn: 5.00 PLN

3) Zysk brutto marki (przed innymi kosztami operacyjnymi)
   - Zysk brutto = Cena netto - (COGS + Prowizje + Bonus + Buyback)
   - Zysk brutto = 81.30 - (20 + 2.30 + 15 + 5) = 39.00 PLN

4) Prowizje na rynku wtórnym (P2P)
   - Marka pobiera 5% od każdej odsprzedaży na tablicy ogłoszeń; z tego 3% zostaje bezpośrednio jako zysk operacyjny, 2% idzie na pule buyback DDC.

## Dalsze uwagi podatkowe i księgowe
- VAT: odprowadzać zgodnie z lokalnymi przepisami; przy sprzedaży zagranicznej możliwe ZW lub różne stawki VAT — zautomatyzować rozpoznawanie kraju kupującego.
- CIT: zysk netto podlega opodatkowaniu CIT (stawka zależna od formy prawnej); wczesna faza: optymalizacja kosztów operacyjnych i ulg.
- Tokenomics: wartość przyznawanych memecoinów należy traktować jako koszt marketingowy/zwrotu wartości; skonsultować rachunkowość tokenów z księgowym.

## Przykładowa księgowość przy sprzedaży 100 sztuk miesięcznie
- Przychód brutto: 100 * 100 = 10,000 PLN
- VAT odprowadzony (23% z ceny netto ~8130) = 1,870 PLN
- COGS: 100 * 20 = 2,000 PLN
- Prowizje płatnicze: 230 PLN
- Bonusy Memecoin: 1,500 PLN
- Buyback (on-sales): 500 PLN
- Zysk brutto: 3,900 PLN

## Rekomendacje operacyjne
- Automatyzować księgowanie VAT per transakcja i eksportować raporty do księgowego.
- Zachować audytowalność wszystkich operacji tokenowych (mint/airdrop/burn) w off-chain ledger.
- Rozważyć przydział części zysku na fundusz zabezpieczający zwroty i reklamacje.
