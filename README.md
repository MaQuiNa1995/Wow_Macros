# Wow_Macros

## Dps

Podemos tirar nuestro hechizo a un enemigo si le tenemos el puntero encima sino lo casteará sobre el objetivo que tengamos marcado
```
#showtooltip Corrupción
/cast [@mouseover,harm][harm] Corrupción

#showtooltip Helada mental
/cast [target=mouseover]  Helada mental
```

Tirar efecto de area sobre nuestro cursor como por ejemplo areas 
```
#showtooltip Portal demoníaco
/cast [@cursor] Portal demoníaco
```

Podemos castear muchas habilidades a la vez como por ejemplo bufos de daño etc pero estos no deben activar el GCD sino no podremos llevar a cabo todas las acciones
```
#showtooltip Dominación Vil
/cast Dominación Vil
/cast Invocar Manáfago
```

Tambien vale para trinkets por ejemplo en este caso se usarán los abalorios (se especifica la posición)
Destacar que si en ese momento no conocemos alguno de los hechizos se ignorarán y se lanzaran de manera normal los demás
```
#showtooltip Furia Sangrienta
/cast Levantar muerto
/cast Furia Sangrienta
/cast Potenciar arma de runas
/use 13
/use 14
```

## Raciales Mercenario Pvp

Tener en 1 mismo botón las 2 raciales horda/alianza para cuando somos mercenarios en este caso la de un goblin/gnomo
```
#showtooltip
/cast Salto con cohete
/cast Artista Del Escape
/run local G=GetSpellInfo SetMacroSpell(GetRunningMacro(), G"Salto con cohete" or G"Artista Del Escape")
```

## Healer

Tirar hechizo de curación sobre un aliado en mouse over y si no tenemos a nadie bajo nuestro ratón echarnoslo a nosotros
```
#showtooltip Niebla reconfortante
/cast [@mouseover,help,nodead][@player] Niebla reconfortante

#showtooltip Crisálida vital
/cast [@mouseover,help,nodead] [] Crisálida vital
```


## Utilidad

2 habilidades en secuencia en el mismo boton (con condicion de reset ya sea segundos, por termino de combate etc)
```
#showtooltip 
/castsequence reset=combat Transcendencia, Transcendencia: Transferencia
```

Podemos hacer que al pulsar la macro definamos un objetivo predeterminado y tambien hacer uso del chat en todas sus variantes
- estancia
- hermandad
- general
- gritar
- grupo
```
#showtooltip Piedra de Alma
/cast [target=nombreJugador] Piedra de alma
/gritar Tirando piedra de alma a nombreJugador
```

1 botón para montura adecuada a cada situación en este orden y supuesto

- si tenemos presionado shift sacaremos el yak para poder reparar/transfigurar
- si tenemos presionado alt y somos chamanes nos transformaremos en el lobo
- si estamos en dragonflight en las afueras sacaremos el dragón azul
- si estamos en las afueras y podemos volar sacaremos un montura voladora
- si estamos en las afueras y no se puede volar o en una instancia en la que se pueda sacar montura, sacaremos una terrestre

```
#showtooltip Trepador de Corredores
/cast [mod:shift] Yak de gran expedición; [mod:alt] lobo fantasmal;Draco de las Tierras Altas
/cast [flyable] Atracador del tiempo infinito;[noflyable] Rinoceronte blindado de pedrisca
```

Resetear el sonido para que pille el cambio de salida de audio
```
/run Sound_GameSystem_RestartSoundSystem()
```

