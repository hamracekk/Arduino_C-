# Arduino_C-

Napište program pro Arduino UNO s připojeným Funshieldem, který bude animovat níže popsaný vzor na čtyřech vertikálních LED diodách. 
V každém okamžiku svítí právě jedna dioda ze 4, na počátku je to LED umístěná nejvýše. V každém kroku animace se aktivní LED posune o jedna níže. 
Když dorazí na spodek, odrazí se a vrací se krok za krokem zpět nahoru. Nahoře se opět odrazí a celý cyklus se opakuje do nekonečna.

Jeden krok animace trvá přesně 300ms. Ve vašem řešení, ale nesmíte používat funkci delay(), ani delayMicroseconds(), ani jinak 
blokovat hlavní smyčku. K měření uplynulého času použijte funkci millis().
