# Calcolatore di Caffè ☕️

Crea un calcolatore per determinare la quantità totale di caffè in tazze e litri necessaria per il resto della tua vita.

## Istruzioni

1. Crea un componente `Calculator` che:

- contenga un input per inserire la tua età o la quantità di caffè giornaliera;
- contenga un button per calcolare la quantità totale di caffè necessaria;
- Mostri il risultato in tazze e in litri (arrotondati a numero intero).

🧐 Valuta con attenzione se e quali elementi possono diventare dei componenti;

2. Mantieni la logica di calcolo all’interno del componente `Calculator`;

3. L’app principale (`App`) deve importare il componente `Calculator` e renderizzarlo.

4. I campi di input devono essere di tipo `number` e accettare solo valori positivi. Se il valore inserito non è valido, deve comparire un messaggio di errore.

## Specifiche

- Stabiliamo che la vita massima sia di **99 anni**;
- Gli stati da gestire sono

  - età (in anni);
  - quantità di caffè giornaliera (in tazze);
  - risultati calcolati (in tazze e in litri);

- Le funzioni da implementare sono:

```js
// Calcola tazze
function calculateSupply(age, amountPerDay) {
  return Math.round((maxAge - age) * 365 * amountPerDay)
}

// Calcola litri
function calculateSupplyLiters(age, litersPerDay) {
  return Math.round((maxAge - age) * 365 * litersPerDay)
}
```

- Comportamento del pulsante: al click deve:
  - leggere i valori dell'input;
  - aggiornare lo stato dei risultati calcolati;
  - mostrare i risultati calcolati.

## Bonus

Mostrare entrambi i risultati (in tazze e in litri) in un unico click.
