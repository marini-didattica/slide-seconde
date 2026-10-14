---
layout: cover
---

# Esercizi introduttivi
Liste e stringhe: scansione, ricerca e costruzione

<div class="pt-12">
  <span class="px-2 py-1 rounded bg-primary text-[#141418]">Marini Mattia - Informatica</span>
</div>

---
layout: two-cols-header
class: table-sm
---

# Esercizio 1 — Massimo e minimo
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista di interi, trova e stampa il valore **massimo** e il valore **minimo**.

::left::

| Input              | Output           |
| ------------------ | ---------------- |
| `[4, 2, 9, 1, 7]`  | `massimo = 9`<br>`minimo = 1` |

::right::

> **Pattern** Scansione con un *miglior candidato*: parti dal primo elemento e aggiorna massimo e minimo a ogni passo.

---

# Esercizio 1 — Massimo e minimo

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> Si parte dal primo elemento come candidato e si scorre la lista una sola volta.

```python
lista = [4, 2, 9, 1, 7]

massimo = lista[0]
minimo = lista[0]
i = 0
while i < len(lista):
    if lista[i] > massimo:
        massimo = lista[i]
    if lista[i] < minimo:
        minimo = lista[i]
    i = i + 1

print("massimo =", massimo)
print("minimo =", minimo)
```

> **Nota** Inizializzare con `lista[0]` (e non con `0`) è essenziale: così funziona anche con liste di soli numeri negativi.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 1 — Massimo e minimo

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [4, 2, 9, 1, 7]`

::left::

```python {1|3-5|7-9|10-11|12|7-9|10-11|12|7-9|10-11|12|7-9|10-11|12|7-9|10-11|12|7|14|15} {at: 1}
lista = [4, 2, 9, 1, 7]

massimo = lista[0]
minimo = lista[0]
i = 0
while i < len(lista):
    if lista[i] > massimo:
        massimo = lista[i]
    if lista[i] < minimo:
        minimo = lista[i]
    i = i + 1

print("massimo =", massimo)
print("minimo =", minimo)
```

::right::

<ListTracker
  :items="[4, 2, 9, 1, 7]"
  :trackers="{ i: { 1: 0, 4: 1, 7: 2, 10: 3, 13: 4, 16: 5 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>massimo</th>
      <th>minimo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-4>i = 0</template>
          <template #4-7>i = 1</template>
          <template #7-10>i = 2</template>
          <template #10-13>i = 3</template>
          <template #13-16>i = 4</template>
          <template #16-20>i = 5</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>massimo = —</template>
          <template #1-8>massimo = 4</template>
          <template #8-20>massimo = 9</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>minimo = —</template>
          <template #1-6>minimo = 4</template>
          <template #6-12>minimo = 2</template>
          <template #12-20>minimo = 1</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-18>—</template>
          <template #18-19>massimo = 9</template>
          <template #19-20>massimo = 9<br>minimo = 1</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 2 — Ricerca lineare
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista di interi e un valore `cercato`, trova l'indice della **prima occorrenza**. Se non c'è, l'indice vale `-1`.

::left::

| Input                     | Output          |
| ------------------------- | --------------- |
| `[4, 2, 9, 1]`, `9`       | `indice = 2`    |
| `[4, 2, 9, 1]`, `7`       | `indice = -1`   |

::right::

> **Pattern** Scansione + condizione + *terminazione anticipata*: appena trovato, il ciclo si ferma.

---

# Esercizio 2 — Ricerca lineare

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> Il ciclo continua solo finché `indice` è ancora `-1`.

```python
lista = [4, 2, 9, 1]
cercato = 9

indice = -1
i = 0
while i < len(lista) and indice == -1:
    if lista[i] == cercato:
        indice = i
    i = i + 1

print("indice =", indice)
```

> **Nota** Senza usare `.index()` né l'operatore `in`. La condizione `indice == -1` fa uscire il `while` alla prima occorrenza.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 2 — Ricerca lineare

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [4, 2, 9, 1]` — `cercato = 9`

::left::

```python {1|2|4-5|6|7|9|6|7|9|6|7|8|9|6|11} {at: 1}
lista = [4, 2, 9, 1]
cercato = 9

indice = -1
i = 0
while i < len(lista) and indice == -1:
    if lista[i] == cercato:
        indice = i
    i = i + 1

print("indice =", indice)
```

::right::

<ListTracker
  :items="[4, 2, 9, 1]"
  :trackers="{ i: { 2: 0, 5: 1, 8: 2, 12: 3 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>indice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-2>i = —</template>
          <template #2-5>i = 0</template>
          <template #5-8>i = 1</template>
          <template #8-12>i = 2</template>
          <template #12-15>i = 3</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-2>indice = —</template>
          <template #2-11>indice = -1</template>
          <template #11-15>indice = 2</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-14>—</template>
          <template #14-15>indice = 2</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 2 — Ricerca lineare

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [4, 2, 9, 1]` — `cercato = 7`

::left::

```python {1|2|4-5|6|7|9|6|7|9|6|7|9|6|7|9|6|11} {at: 1}
lista = [4, 2, 9, 1]
cercato = 7

indice = -1
i = 0
while i < len(lista) and indice == -1:
    if lista[i] == cercato:
        indice = i
    i = i + 1

print("indice =", indice)
```

::right::

<ListTracker
  :items="[4, 2, 9, 1]"
  :trackers="{ i: { 2: 0, 5: 1, 8: 2, 11: 3, 14: 4 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>indice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-2>i = —</template>
          <template #2-5>i = 0</template>
          <template #5-8>i = 1</template>
          <template #8-11>i = 2</template>
          <template #11-14>i = 3</template>
          <template #14-17>i = 4</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-2>indice = —</template>
          <template #2-17>indice = -1</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-16>—</template>
          <template #16-17>indice = -1</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 3 — Somma e media
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista di numeri, calcola e stampa la **somma** e la **media** degli elementi.

::left::

| Input        | Output         |
| ------------ | -------------- |
| `[2, 4, 6]`  | `somma = 12`<br>`media = 4.0` |

::right::

> **Pattern** Accumulatore + conteggio: crea le variabili **prima** del ciclo e aggiornale dentro.

---

# Esercizio 3 — Somma e media

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> `somma` accumula i valori, la media si calcola alla fine dividendo per `len(lista)`.

```python
lista = [2, 4, 6]

somma = 0
i = 0
while i < len(lista):
    somma = somma + lista[i]
    i = i + 1

media = somma / len(lista)
print("somma =", somma)
print("media =", media)
```

> **Nota** L'operatore `/` restituisce sempre un numero con la virgola: `12 / 3` vale `4.0`. Per la media intera si usa `//`.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 3 — Somma e media

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [2, 4, 6]`

::left::

```python {1|3-4|5|6|7|5|6|7|5|6|7|5|9|10|11} {at: 1}
lista = [2, 4, 6]

somma = 0
i = 0
while i < len(lista):
    somma = somma + lista[i]
    i = i + 1

media = somma / len(lista)
print("somma =", somma)
print("media =", media)
```

::right::

<ListTracker
  :items="[2, 4, 6]"
  :trackers="{ i: { 1: 0, 4: 1, 7: 2, 10: 3 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>somma</th>
      <th>media</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-5>i = 0</template>
          <template #5-8>i = 1</template>
          <template #8-11>i = 2</template>
          <template #11-15>i = 3</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>somma = —</template>
          <template #1-3>somma = 0</template>
          <template #3-6>somma = 2</template>
          <template #6-9>somma = 6</template>
          <template #9-15>somma = 12</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-12>media = —</template>
          <template #12-15>media = 4.0</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-13>—</template>
          <template #13-14>somma = 12</template>
          <template #14-15>somma = 12<br>media = 4.0</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 4 — Contare con una condizione
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista di interi, conta quanti valori **pari** contiene e stampa il risultato.

::left::

| Input                | Output     |
| -------------------- | ---------- |
| `[1, 4, 7, 8, 10]`   | `pari = 3` |

::right::

> **Pattern** Conteggio condizionale: incrementa il contatore **solo** quando la condizione è vera.

---

# Esercizio 4 — Contare con una condizione

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> Si scorre la lista e si incrementa `conta` per ogni elemento pari.

```python
lista = [1, 4, 7, 8, 10]

conta = 0
i = 0
while i < len(lista):
    if lista[i] % 2 == 0:
        conta = conta + 1
    i = i + 1

print("pari =", conta)
```

> **Nota** Un numero è pari quando `lista[i] % 2 == 0`. La condizione può diventare `> 0`, `> soglia`, ecc.: cambia solo l'`if`.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 4 — Contare con una condizione

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [1, 4, 7, 8, 10]`

::left::

```python {1|3-4|5-6|8|5-6|7|8|5-6|8|5-6|7|8|5-6|7|8|5|10} {at: 1}
lista = [1, 4, 7, 8, 10]

conta = 0
i = 0
while i < len(lista):
    if lista[i] % 2 == 0:
        conta = conta + 1
    i = i + 1

print("pari =", conta)
```

::right::

<ListTracker
  :items="[1, 4, 7, 8, 10]"
  :trackers="{ i: { 1: 0, 3: 1, 6: 2, 8: 3, 11: 4, 14: 5 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>conta</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-3>i = 0</template>
          <template #3-6>i = 1</template>
          <template #6-8>i = 2</template>
          <template #8-11>i = 3</template>
          <template #11-14>i = 4</template>
          <template #14-17>i = 5</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>conta = —</template>
          <template #1-5>conta = 0</template>
          <template #5-10>conta = 1</template>
          <template #10-13>conta = 2</template>
          <template #13-17>conta = 3</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-16>—</template>
          <template #16-17>pari = 3</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 5 — Invertire una lista
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista, costruisci una **nuova lista** con gli elementi in ordine inverso. Poi, in una variante, inverti la lista **sul posto** con due puntatori.

::left::

| Input          | Output               |
| -------------- | -------------------- |
| `[1, 2, 3, 4]` | `[4, 3, 2, 1]`       |

::right::

> **Pattern** Aritmetica sugli indici: parti dall'ultimo e scendi fino a `0`. La variante usa due puntatori e lo scambio.

---

# Esercizio 5 — Invertire una lista (nuova lista)

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione 1/2</span> Si scorre la lista a ritroso e si aggiunge ogni elemento alla nuova lista.

```python
lista = [1, 2, 3, 4]

invertita = []
i = len(lista) - 1
while i >= 0:
    invertita.append(lista[i])
    i = i - 1

print(invertita)
```

> **Nota** L'ultimo indice è `len(lista) - 1`. La condizione `i >= 0` (non `i > 0`) serve a includere anche il primo elemento.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 5 — Invertire una lista (nuova lista)

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [1, 2, 3, 4]`

::left::

```python {1|3-4|5|6|7|5|6|7|5|6|7|5|6|7|5|9} {at: 1}
lista = [1, 2, 3, 4]

invertita = []
i = len(lista) - 1
while i >= 0:
    invertita.append(lista[i])
    i = i - 1

print(invertita)
```

::right::

<ListTracker
  :items="[1, 2, 3, 4]"
  :trackers="{ i: { 1: 3, 4: 2, 7: 1, 10: 0, 13: -1 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>invertita</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-4>i = 3</template>
          <template #4-7>i = 2</template>
          <template #7-10>i = 1</template>
          <template #10-13>i = 0</template>
          <template #13-16>i = -1</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>invertita = —</template>
          <template #1-3>invertita = []</template>
          <template #3-6>invertita = [4]</template>
          <template #6-9>invertita = [4, 3]</template>
          <template #9-12>invertita = [4, 3, 2]</template>
          <template #12-16>invertita = [4, 3, 2, 1]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-15>—</template>
          <template #15-16>[4, 3, 2, 1]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---

# Esercizio 5 — Invertire una lista (sul posto)

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione 2/2</span> Due puntatori partono dagli estremi, si scambiano gli elementi e si avvicinano.

```python
lista = [1, 2, 3, 4]

sinistra = 0
destra = len(lista) - 1
while sinistra < destra:
    temp = lista[sinistra]
    lista[sinistra] = lista[destra]
    lista[destra] = temp
    sinistra = sinistra + 1
    destra = destra - 1

print(lista)
```

> **Nota** Lo scambio usa una variabile temporanea `temp`. Il ciclo si ferma quando i due puntatori si incontrano (`sinistra < destra`).

---
layout: two-cols-header
class: table-sm
---

# Esercizio 5 — Invertire una lista (sul posto)

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [1, 2, 3, 4]`

::left::

```python {1|3-4|5|6|7|8|9|10|5|6|7|8|9|10|5|12} {at: 1}
lista = [1, 2, 3, 4]

sinistra = 0
destra = len(lista) - 1
while sinistra < destra:
    temp = lista[sinistra]
    lista[sinistra] = lista[destra]
    lista[destra] = temp
    sinistra = sinistra + 1
    destra = destra - 1

print(lista)
```

::right::

<ListTracker
  :items="[1, 2, 3, 4]"
  :trackers="[
    { name: 'sinistra', values: { 1: 0, 6: 1, 12: 2 } },
    { name: 'destra', values: { 1: 3, 7: 2, 13: 1 } },
  ]"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>sinistra</th>
      <th>destra</th>
      <th>temp</th>
      <th>lista</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-6>0</template>
          <template #6-12>1</template>
          <template #12-16>2</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-7>3</template>
          <template #7-13>2</template>
          <template #13-16>1</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-3>—</template>
          <template #3-9>1</template>
          <template #9-16>2</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-4>[1, 2, 3, 4]</template>
          <template #4-5>[4, 2, 3, 4]</template>
          <template #5-10>[4, 2, 3, 1]</template>
          <template #10-11>[4, 3, 3, 1]</template>
          <template #11-16>[4, 3, 2, 1]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-15>—</template>
          <template #15-16>[4, 3, 2, 1]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 6 — Una stringa è palindroma?
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una stringa, stabilisci se si legge uguale nei due versi (palindroma).

::left::

| Input     | Output          |
| --------- | --------------- |
| `"radar"` | `palindromo`    |
| `"hello"` | `non palindromo`|

::right::

> **Pattern** Confronti simmetrici con due puntatori: `parola[sinistra]` e `parola[destra]` si avvicinano.

---

# Esercizio 6 — Una stringa è palindroma?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> Si confrontano i caratteri simmetrici finché i due puntatori non si incontrano.

```python
parola = "radar"

palindromo = True
sinistra = 0
destra = len(parola) - 1
while sinistra < destra:
    if parola[sinistra] != parola[destra]:
        palindromo = False
    sinistra = sinistra + 1
    destra = destra - 1

if palindromo == True:
    print("palindromo")
else:
    print("non palindromo")
```

> **Nota** Su una stringa l'accesso è `parola[i]`, esattamente come per una lista. Basta un confronto diverso per dire che **non** è palindroma.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 6 — Una stringa è palindroma?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `parola = "radar"`

::left::

```python {1|3-5|6|7|9|10|6|7|9|10|6|11|12} {at: 1}
parola = "radar"

palindromo = True
sinistra = 0
destra = len(parola) - 1
while sinistra < destra:
    if parola[sinistra] != parola[destra]:
        palindromo = False
    sinistra = sinistra + 1
    destra = destra - 1
if palindromo == True:
    print("palindromo")
else:
    print("non palindromo")
```

::right::

<ListTracker
  :items="['r', 'a', 'd', 'a', 'r']"
  :trackers="[
    { name: 'sinistra', values: { 1: 0, 4: 1, 8: 2 } },
    { name: 'destra', values: { 1: 4, 5: 3, 9: 2 } },
  ]"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>sinistra</th>
      <th>destra</th>
      <th>palindromo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-4>0</template>
          <template #4-8>1</template>
          <template #8-13>2</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-5>4</template>
          <template #5-9>3</template>
          <template #9-13>2</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-13>True</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-12>—</template>
          <template #12-13>palindromo</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 6 — Una stringa è palindroma?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `parola = "hello"`

::left::

```python {1|3-5|6|7|8|9|10|6|7|8|9|10|6|11|14} {at: 1}
parola = "hello"

palindromo = True
sinistra = 0
destra = len(parola) - 1
while sinistra < destra:
    if parola[sinistra] != parola[destra]:
        palindromo = False
    sinistra = sinistra + 1
    destra = destra - 1
if palindromo == True:
    print("palindromo")
else:
    print("non palindromo")
```

::right::

<ListTracker
  :items="['h', 'e', 'l', 'l', 'o']"
  :trackers="[
    { name: 'sinistra', values: { 1: 0, 5: 1, 10: 2 } },
    { name: 'destra', values: { 1: 4, 6: 3, 11: 2 } },
  ]"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>sinistra</th>
      <th>destra</th>
      <th>palindromo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-5>0</template>
          <template #5-10>1</template>
          <template #10-15>2</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-6>4</template>
          <template #6-11>3</template>
          <template #11-15>2</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-4>True</template>
          <template #4-15>False</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-14>—</template>
          <template #14-15>non palindromo</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 7 — Filtrare una lista
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista, costruisci una **nuova lista** con i soli elementi che soddisfano una condizione (qui: i pari). In una variante, la stessa idea su una stringa: togli gli spazi.

::left::

| Input                | Output         |
| -------------------- | -------------- |
| `[1, 4, 7, 8, 10]`   | `[4, 8, 10]`   |

::right::

> **Pattern** Copia condizionale: si scorre l'ingresso e si fa `append` **solo** quando la condizione vale.

---

# Esercizio 7 — Filtrare una lista

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione 1/2</span> Si aggiungono i pari a una nuova lista, scartando tutti gli altri.

```python
lista = [1, 4, 7, 8, 10]

filtrata = []
i = 0
while i < len(lista):
    if lista[i] % 2 == 0:
        filtrata.append(lista[i])
    i = i + 1

print(filtrata)
```

> **Nota** `append` aggiunge in fondo alla nuova lista: l'ordine degli elementi non cambia, si saltano solo quelli che non ci interessano.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 7 — Filtrare una lista

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [1, 4, 7, 8, 10]`

::left::

```python {1|3-4|5-6|8|5-6|7|8|5-6|8|5-6|7|8|5-6|7|8|5|10} {at: 1}
lista = [1, 4, 7, 8, 10]

filtrata = []
i = 0
while i < len(lista):
    if lista[i] % 2 == 0:
        filtrata.append(lista[i])
    i = i + 1

print(filtrata)
```

::right::

<ListTracker
  :items="[1, 4, 7, 8, 10]"
  :trackers="{ i: { 1: 0, 3: 1, 6: 2, 8: 3, 11: 4, 14: 5 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>filtrata</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-3>i = 0</template>
          <template #3-6>i = 1</template>
          <template #6-8>i = 2</template>
          <template #8-11>i = 3</template>
          <template #11-14>i = 4</template>
          <template #14-17>i = 5</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>filtrata = —</template>
          <template #1-5>filtrata = []</template>
          <template #5-10>filtrata = [4]</template>
          <template #10-13>filtrata = [4, 8]</template>
          <template #13-17>filtrata = [4, 8, 10]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-16>—</template>
          <template #16-17>[4, 8, 10]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---

# Esercizio 7 — Filtrare una stringa

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione 2/2</span> Stessa idea sui caratteri: si tiene un carattere solo se **non** è uno spazio.

```python
frase = "ab c"

senza_spazi = ""
i = 0
while i < len(frase):
    if frase[i] != " ":
        senza_spazi = senza_spazi + frase[i]
    i = i + 1

print(senza_spazi)
```

> **Nota** La stringa di output parte vuota (`""`) e cresce con `+`. L'`if` tiene i caratteri utili e scarta gli spazi.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 7 — Filtrare una stringa

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `frase = "ab c"`

::left::

```python {1|3-4|5-6|7|8|5-6|7|8|5-6|8|5-6|7|8|5|10} {at: 1}
frase = "ab c"

senza_spazi = ""
i = 0
while i < len(frase):
    if frase[i] != " ":
        senza_spazi = senza_spazi + frase[i]
    i = i + 1

print(senza_spazi)
```

::right::

<ListTracker
  :items="['a', 'b', '␣', 'c']"
  :trackers="{ i: { 1: 0, 4: 1, 7: 2, 10: 3, 13: 4 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>senza_spazi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-4>i = 0</template>
          <template #4-7>i = 1</template>
          <template #7-10>i = 2</template>
          <template #10-13>i = 3</template>
          <template #13-15>i = 4</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>senza_spazi = —</template>
          <template #1-3>senza_spazi = ""</template>
          <template #3-6>senza_spazi = "a"</template>
          <template #6-11>senza_spazi = "ab"</template>
          <template #11-15>senza_spazi = "abc"</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-14>—</template>
          <template #14-15>abc</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 8 — Due stringhe sono anagrammi?
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Date due stringhe, stabilisci se contengono gli **stessi caratteri** con le **stesse quantità**.

::left::

| Input              | Output           |
| ------------------ | ---------------- |
| `"roma"`, `"amor"` | `anagrammi`      |
| `"ciao"`, `"cane"` | `non anagrammi`  |

::right::

> **Pattern** Conteggio delle frequenze con cicli annidati: per ogni lettera si contano le occorrenze in **entrambe** le stringhe.

---

# Esercizio 8 — Due stringhe sono anagrammi?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> Per ogni lettera della prima stringa si conta quante volte compare in ciascuna delle due.

```python {maxHeight:'80%'}
parola_A = "roma"
parola_B = "amor"

anagrammi = True
if len(parola_A) != len(parola_B):
    anagrammi = False

i = 0
while i < len(parola_A) and anagrammi == True:
    conta_A = 0
    conta_B = 0
    j = 0
    while j < len(parola_A):
        if parola_A[j] == parola_A[i]:
            conta_A = conta_A + 1
        j = j + 1
    j = 0
    while j < len(parola_B):
        if parola_B[j] == parola_A[i]:
            conta_B = conta_B + 1
        j = j + 1
    if conta_A != conta_B:
        anagrammi = False
    i = i + 1

if anagrammi == True:
    print("anagrammi")
else:
    print("non anagrammi")
```

> **Nota** Se sono anagrammi, ogni lettera deve comparire lo stesso numero di volte nelle due stringhe. Il controllo di lunghezza esclude subito i casi impossibili.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 8 — Due stringhe sono anagrammi?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `parola_A = "roma"` — `parola_B = "amor"`

::left::

```python {1|2|4|5|8|9|10-21|22|24|9|10-21|22|24|9|10-21|22|24|9|10-21|22|24|9|26|27}{maxHeight:'40vh'} {at: 1}
parola_A = "roma"
parola_B = "amor"

anagrammi = True
if len(parola_A) != len(parola_B):
    anagrammi = False

i = 0
while i < len(parola_A) and anagrammi == True:
    conta_A = 0
    conta_B = 0
    j = 0
    while j < len(parola_A):
        if parola_A[j] == parola_A[i]:
            conta_A = conta_A + 1
        j = j + 1
    j = 0
    while j < len(parola_B):
        if parola_B[j] == parola_A[i]:
            conta_B = conta_B + 1
        j = j + 1
    if conta_A != conta_B:
        anagrammi = False
    i = i + 1

if anagrammi == True:
    print("anagrammi")
else:
    print("non anagrammi")
```

::right::

<ListTracker
  :items="['r', 'o', 'm', 'a']"
  :trackers="{ i: { 4: 0, 8: 1, 12: 2, 16: 3, 20: 4 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>conta_A</th>
      <th>conta_B</th>
      <th>anagrammi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-4>—</template>
          <template #4-8>0</template>
          <template #8-12>1</template>
          <template #12-16>2</template>
          <template #16-20>3</template>
          <template #20-24>4</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-6>—</template>
          <template #6-24>1</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-6>—</template>
          <template #6-24>1</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-2>—</template>
          <template #2-24>True</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-23>—</template>
          <template #23-24>anagrammi</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

> **Nota** Nel passo `10-21` il conteggio delle due lettere è raggruppato in un unico stato, per mantenere la traccia leggibile.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 8 — Due stringhe sono anagrammi?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `parola_A = "ciao"` — `parola_B = "cane"`

::left::

```python {1|2|4|5|8|9|10-21|22|24|9|10-21|22|23|24|9|26|29}{maxHeight:'40vh'} {at: 1}
parola_A = "ciao"
parola_B = "cane"

anagrammi = True
if len(parola_A) != len(parola_B):
    anagrammi = False

i = 0
while i < len(parola_A) and anagrammi == True:
    conta_A = 0
    conta_B = 0
    j = 0
    while j < len(parola_A):
        if parola_A[j] == parola_A[i]:
            conta_A = conta_A + 1
        j = j + 1
    j = 0
    while j < len(parola_B):
        if parola_B[j] == parola_A[i]:
            conta_B = conta_B + 1
        j = j + 1
    if conta_A != conta_B:
        anagrammi = False
    i = i + 1

if anagrammi == True:
    print("anagrammi")
else:
    print("non anagrammi")
```

::right::

<ListTracker
  :items="['c', 'i', 'a', 'o']"
  :trackers="{ i: { 4: 0, 8: 1, 13: 2 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>conta_A</th>
      <th>conta_B</th>
      <th>anagrammi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-4>—</template>
          <template #4-8>0</template>
          <template #8-13>1</template>
          <template #13-17>2</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-6>—</template>
          <template #6-17>1</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-6>—</template>
          <template #6-10>1</template>
          <template #10-17>0</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-2>—</template>
          <template #2-12>True</template>
          <template #12-17>False</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-16>—</template>
          <template #16-17>non anagrammi</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 9 — La lista è ordinata?
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista, stabilisci se è **ordinata** in modo crescente (ogni elemento maggiore o uguale al precedente).

::left::

| Input          | Output          |
| -------------- | --------------- |
| `[1, 3, 5, 7]` | `ordinata`      |
| `[1, 3, 2, 7]` | `non ordinata`  |

::right::

> **Pattern** Confronti adiacenti: si guarda la coppia `lista[i]` / `lista[i - 1]` e si segnala la prima violazione.

---

# Esercizio 9 — La lista è ordinata?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> Si parte da `i = 1` e si confronta ogni elemento con quello precedente.

```python
lista = [1, 3, 5, 7]

ordinata = True
i = 1
while i < len(lista):
    if lista[i] < lista[i - 1]:
        ordinata = False
    i = i + 1

if ordinata == True:
    print("ordinata")
else:
    print("non ordinata")
```

> **Nota** Si parte da `i = 1` perché il primo elemento non ha un precedente. `lista[i - 1]` è l'elemento appena prima di `lista[i]`.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 9 — La lista è ordinata?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [1, 3, 5, 7]`

::left::

```python {1|3-4|5|6|8|5|6|8|5|6|8|5|10|11} {at: 1}
lista = [1, 3, 5, 7]

ordinata = True
i = 1
while i < len(lista):
    if lista[i] < lista[i - 1]:
        ordinata = False
    i = i + 1

if ordinata == True:
    print("ordinata")
else:
    print("non ordinata")
```

::right::

<ListTracker
  :items="[1, 3, 5, 7]"
  :trackers="{ i: { 1: 1, 4: 2, 7: 3, 10: 4 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>ordinata</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-4>i = 1</template>
          <template #4-7>i = 2</template>
          <template #7-10>i = 3</template>
          <template #10-14>i = 4</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>ordinata = —</template>
          <template #1-14>ordinata = True</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-13>—</template>
          <template #13-14>ordinata</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 9 — La lista è ordinata?

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [1, 3, 2, 7]`

::left::

```python {1|3-4|5|6|8|5|6|7|8|5|6|8|5|10|12} {at: 1}
lista = [1, 3, 2, 7]

ordinata = True
i = 1
while i < len(lista):
    if lista[i] < lista[i - 1]:
        ordinata = False
    i = i + 1

if ordinata == True:
    print("ordinata")
else:
    print("non ordinata")
```

::right::

<ListTracker
  :items="[1, 3, 2, 7]"
  :trackers="{ i: { 1: 1, 4: 2, 7: 3, 11: 4 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>ordinata</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>i = —</template>
          <template #1-4>i = 1</template>
          <template #4-7>i = 2</template>
          <template #7-11>i = 3</template>
          <template #11-15>i = 4</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>ordinata = —</template>
          <template #1-7>ordinata = True</template>
          <template #7-15>ordinata = False</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-14>—</template>
          <template #14-15>non ordinata</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

---
layout: two-cols-header
class: table-sm
---

# Esercizio 10 — Rimuovere i duplicati
<span class="px-2 py-1 rounded bg-primary text-[#141418]">Testo</span> Data una lista, costruisci una **nuova lista senza duplicati**, mantenendo l'ordine di prima comparsa. Più avanti lo stesso problema si potrà risolvere con gli **insiemi** (`set`).

::left::

| Input            | Output         |
| ---------------- | -------------- |
| `[3, 1, 3, 2]`   | `[3, 1, 2]`    |

::right::

> **Pattern** Controllo di appartenenza + costruzione del risultato: prima di aggiungere, verifica che l'elemento **non** ci sia già.

---

# Esercizio 10 — Rimuovere i duplicati

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Soluzione</span> Per ogni elemento si cerca se è già nella lista risultato; se non c'è, lo si aggiunge.

```python
lista = [3, 1, 3, 2]

senza_duplicati = []
i = 0
while i < len(lista):
    trovato = False
    j = 0
    while j < len(senza_duplicati) and trovato == False:
        if senza_duplicati[j] == lista[i]:
            trovato = True
        else:
            j = j + 1
    if trovato == False:
        senza_duplicati.append(lista[i])
    i = i + 1

print(senza_duplicati)
```

> **Nota** Senza usare `in` né `set`. Il ciclo interno è una *ricerca lineare* nella lista che stiamo costruendo; `trovato` ci dice se l'elemento è già presente.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 10 — Rimuovere i duplicati

<span class="px-2 py-1 rounded bg-primary text-[#141418]">Traccia</span> `lista = [3, 1, 3, 2]`

::left::

```python {1|3-4|5|6-12|13|14|15|5|6-12|13|14|15|5|6-12|13|15|5|6-12|13|14|15|5|17} {at: 1}
lista = [3, 1, 3, 2]

senza_duplicati = []
i = 0
while i < len(lista):
    trovato = False
    j = 0
    while j < len(senza_duplicati) and trovato == False:
        if senza_duplicati[j] == lista[i]:
            trovato = True
        else:
            j = j + 1
    if trovato == False:
        senza_duplicati.append(lista[i])
    i = i + 1

print(senza_duplicati)
```

::right::

<ListTracker
  :items="[3, 1, 3, 2]"
  :trackers="{ i: { 1: 0, 6: 1, 11: 2, 15: 3, 20: 4 } }"
  highlight
/>

<table>
  <thead>
    <tr>
      <th>i</th>
      <th>trovato</th>
      <th>senza_duplicati</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-6>0</template>
          <template #6-11>1</template>
          <template #11-15>2</template>
          <template #15-20>3</template>
          <template #20-23>4</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-3>—</template>
          <template #3-13>False</template>
          <template #13-17>True</template>
          <template #17-23>False</template>
        </v-switch>
      </td>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-1>—</template>
          <template #1-5>[]</template>
          <template #5-10>[3]</template>
          <template #10-19>[3, 1]</template>
          <template #19-23>[3, 1, 2]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <v-switch at="1" class="font-mono">
          <template #0-22>—</template>
          <template #22-23>[3, 1, 2]</template>
        </v-switch>
      </td>
    </tr>
  </tbody>
</table>

::bottom::

<ClicksSlider class="mt-2" />

> **Nota** Nel passo `6-12` la ricerca nella lista risultato è raggruppata in un unico stato, per mantenere la traccia leggibile.
