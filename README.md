# Wow_Macros

Tabla de contenidos

- [Wow_Macros](#wow_macros)
   * [Dps](#dps)
   * [Raciales Mercenario Pvp](#raciales-mercenario-pvp)
   * [Healer](#healer)
   * [Utilidad](#utilidad)
      + [Poción(Dragonflight) + piedra de warlock](#pocióndragonflight-piedra-de-warlock)
      + [N Habilidades en secuencia](#n-habilidades-en-secuencia)
      + [Casteo de hechizos en objetivos y anuncios por chat](#casteo-de-hechizod-en-objetivos-y-anuncios-por-chat)
         - [Como alternativa podemos tirar la habilidad al `@mouseover` y anunciar un mensaje con el objetivo a quien va dirigido](#como-alternativa-podemos-tirar-la-habilidad-al-mouseover-y-anunciar-un-mensaje-con-el-objetivo-a-quien-va-dirigido)
      + [Botón para montura adecuada a cada situación en este orden y supuesto](#botón-para-montura-adecuada-a-cada-situación-en-este-orden-y-supuesto)
      + [Resetear el sonido para que pille el cambio de salida de audio](#resetear-el-sonido-para-que-pille-el-cambio-de-salida-de-audio)
      + [Notificar en el chat donde y que rare está activo y con que vida](#notificar-en-el-chat-donde-y-que-rare-está-activo-y-con-que-vida)
      + [Habilidades de redirección de aggro (Rogue y Hunter)](#habilidades-de-redirección-de-aggro-rogue-y-hunter)
         - [Parte 1](#parte-1)
         - [Parte 2](#parte-2)
      + [Ver el descanso que tienes en el chat](#ver-el-descanso-que-tienes-en-el-chat)

## Dps

Podemos tirar nuestro hechizo a un enemigo si le tenemos el puntero encima sino lo casteará sobre el objetivo que tengamos marcado
```
#showtooltip Corrupción
/cast [@mouseover,harm][harm] Corrupción
```

Podemos omitir el segundo parámetro [harm] para si no tenemos a ningún enemigo bajo el puntero del ratón no lance nada
Adicionalmente [target=mouseover] es una variante de [@mouseover]
```
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

Podemos tener una macro para no tener que andar cambiando la barra de habilidades cuando cambiamos los talentos que compartan el mismo slot es decir los que o sabes 1 o sabes el otro como por ejemplo en el caso del brujo aflicción
Podemos usar los modificadores anteriores 
```
#showtooltip
/cast [@mouseover,harm][harm] [known: Singularidad fantasma] Singularidad fantasma; [@cursor] [known: Mácula vil] [@cursor] Mácula vil
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

### Poción(Dragonflight) + piedra de warlock

Si queremos tener un botón para tener las potis de dragonflight y la piedra de lock con condición de reset de 5 minutos para cuando nos venga el cd de la poción si no hemos usado la piedra de lock
Adicionalmente si somos warlock podremos presionar `shift` para hacer uso de la habilidad quemar alma y potenciar la piedra de lock

- 5512: Piedra de lock
- 191380: poción de sanación refrescante (tier 3)

```
#showtooltip
/cast [mod:shift] Quemar Alma
/castsequence reset=300 item:191380, item:5512
```

y si lo queremos al revés:

```
#showtooltip
/cast [mod:shift] Quemar Alma
/castsequence reset=combat item:5512, item:191380
```

### N Habilidades en secuencia

N habilidades en secuencia en el mismo boton (con condicion de reset ya sea segundos, por termino de combate etc) 
Independientemente de que se haya cumplido la condición o no si presionamos en el caso de la siguiente macro, la misma 2 veces se reseteará al principio
Si tuviera mas hechizos tendríamos que presionar la macro tantas veces como hechizos hayamos definido

```
#showtooltip 
/castsequence reset=combat Transcendencia, Transcendencia: Transferencia
```
- reset=<number> - número de segundos desde que presionaste el botón
- reset=target - Has cambiado objetivo
- reset=combat - Has entrado o salido de combate
- reset=alt - Alt ha sido presionado
- reset=shift - Shift ha sido presionado
- reset=ctrl - Ctrl ha sido presionado

### Casteo de hechizos en objetivos y anuncios por chat

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

#### Como alternativa podemos tirar la habilidad al `@mouseover` y anunciar un mensaje con el objetivo a quien va dirigido

```
#showtooltip
/cast [@mouseover] Piedra de alma
/gritar Casting Soulstone to %t, dont release !!!!!
```

### Botón para montura adecuada a cada situación en este orden y supuesto

- si tenemos presionado shift sacaremos el yak para poder reparar/transfigurar
- si estamos en un contenido `indoor` como una mazmorra o banda y somos chamanes nos transformaremos en el lobo espectral
- si estamos en dragonflight en las afueras sacaremos el dragón azul
- si estamos en las afueras y podemos volar sacaremos un montura voladora
- si estamos en las afueras y no se puede volar o en una instancia en la que se pueda sacar montura voladora, sacaremos una terrestre

```
#showtooltip Señor Faldomero
/cast [mod:shift] Yak de gran expedición; [advflyable] vermis arbórea auspiciosa; [flyable] colmimédula; [indoors] lobo fantasmal; [noflyable] Señor Faldomero
```
Con esta macro es importante saber que en la pelea de Tyndral en Amirdrasil Season 3 no podrás usarla para despues de coger la pluma subirte al dragonriding

### Resetear el sonido para que pille el cambio de salida de audio
```
/run Sound_GameSystem_RestartSoundSystem()
```

### Notificar en el chat donde y que rare está activo y con que vida

`/run local c,p,t,m=C_Map,"player","target"m=c.GetBestMapForUnit(p)c.SetUserWaypoint{uiMapID=m,position=c.GetPlayerMapPosition(m,p)}SendChatMessage(format("%%t (%d%%)%s",UnitHealth(t)/UnitHealthMax(t)*100,c.GetUserWaypointHyperlink()),"CHANNEL",nil,1)`

### Habilidades de redirección de aggro (Rogue y Hunter)

Tambien te valdría para cualquier otra habilidad que quieras echarle a un healer o tanque por ejemplo la que da mana al healer del evoker

#### Parte 1

Con esta primera macro la tendremos que ejecutar cuando entramos a un nuevo grupo para definir tendremos que cambiar `Misdirection` por el nombre de la habilidad que necesitemos
y en el caso de que esa habilidad sea para healer tendremos que cambiar `TANK` por `HEALER`

`/run for i=1,5 do local role=UnitGroupRolesAssigned("party"..i) if role=="TANK" then local name=GetUnitName("party"..i, true) local str="#showtooltip Misdirection\n/cast [@"..name.."] Misdirection" EditMacro("Misdirection",nil,nil,str,1,1) end end`

#### Parte 2

Una vez hayamos ejecutado la macro de la parte 1, ya tendremos lista esta macro para echar la habilidad que queramos al tanque con solo darle a la macro sin nada mas
es importante revisar los nombres de las habilidades para que coincidan y en el caso de que esta macro sea dirigida a los healer cambiar `Tank` por `Healer`

```
#showtooltip Misdirection
/cast [@Tank-Server] Misdirection
```

### Ver el descanso que tienes en el chat

Para poder ver el descanso que tienes acumulado para la experiencia podemos usar esta macro para imprimir el % que tenemos en el chat (no se envía a nadie solo a ti)

```
/run local restXP, nextlevelXP, PercentRest = GetXPExhaustion(), UnitXPMax("player"), 0 if restXP then PercentRest = math.floor(restXP / nextlevelXP * 100) end print(restXP and format("Porcentaje de descanso: %%%s",PercentRest) or "No tienes descanso!")
```
