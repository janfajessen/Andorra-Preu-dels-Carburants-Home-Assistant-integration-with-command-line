# Andorra Fuel Prices, "integration" of Home Assistant with command_line 


###### Andorra Preu dels Carburants, "integració" de Home Assistant amb command_line 
###### Andorra Precio de los Carburantes, "integración" de Home Assistant con command_line
###### Prix ​​​​des carburants d'Andorre, "intégration" de Home Assistant avec command_line


<details>
<summary> Català </summary>
Perquè és difícil scrapejar la única web del Principat d'Andorra (https://sig.govern.ad/IPE/PreusCarburants) sobre el preu dels carburants ja que té diferents selectors he aconseguit amb un sensor de command line el preu dels carburants en benzineres de cada parròquia (gràcies a maniattico del canal de telegram Domoticaencasa.es).
Crea un fitxer nou anomenat command_line.yaml, al fitxer configuration.yaml escriu commmand_line: !include command_line.yaml 
  i copia el següent en un arxiu command_line.yaml:
</details>

<details>
<summary> Español </summary>
  Porque es dificil scrapear la unica web del Principado de Andorra (https://sig.govern.ad/IPE/PreusCarburants) sobre el precio de los carburantes ya que tiene diferentes selectores he conseguido con un sensor de command line el precio de los carburantes en gasolineras de cada parroquia (gracias a maniattico del canal de telegram Domoticaencasa.es).
Crea un archivo nuevo llamado command_line.yaml, en el archivo configuration.yaml escribe commmand_line: !include command_line.yaml 
  y copia  lo siquiente en el archivo command_line.yaml:
</details>

<details>
<summary> Français </summary>
Parce qu'il est difficile de gratter le seul site de la Principauté d'Andorre (https://sig.govern.ad/IPE/PreusCarburants) sur le prix du carburant car il a des sélecteurs différents, j'ai obtenu avec un capteur en ligne de commande le prix du carburant dans les stations-service de chaque paroisse (merci au maniaque de Domoticaencasa canal de télégramme est).
Créez un nouveau fichier appelé command_line.yaml, dans le fichier configuration.yaml, écrivez commmand_line : !include command_line.yaml 
  et copiez ce qui suit sur une ligne de commande :
</details>

<details>
<summary> English </summary>
Because it is difficult to scrape the only website in the Principality of Andorra (https://sig.govern.ad/IPE/PreusCarburants) on fuel prices as it has different selectors, I have managed to obtain the fuel prices at gas stations in each parish with a command line sensor (thanks to maniattico from the Domoticaencasa.es telegram channel).
Create a new file called command_line.yaml, in the configuration.yaml file write commmand_line: !include command_line.yaml 
and copy the following into a command_line.yaml file:
</details>


```
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=6\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=5 | grep -i 'Andorracing Experience' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: AndorRacing Andorra la Vella gasoil
      unique_id: andorracing_gasoil
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=5\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=5 | grep -i 'Andorracing Experience' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: AndorRacing Andorra la Vella sp98
      unique_id: andorracing_sp98
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=5 | grep -i 'Andorracing Experience' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: AndorRacing Andorra la Vella sp95
      unique_id: andorracing_sp95
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=5 | grep -i 'CEPSA Auto-Centre' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: Cepsa Unnic sp95
      unique_id: cepsa_unnic_sp96
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=7 | grep -i 'TotalEnergies - ARTAL 1 ' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: Escaldes Engordany TotalEnergies Artal1 sp95
      unique_id: totalenergies_escaldes_sp95
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=2 | grep -i 'Shell Encamp' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: Shell Encamp sp95
      unique_id: shell_encamp_sp95
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=2 | grep -i 'BP Encamp Centre I ' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: BP Encamp Centre I sp95
      unique_id: bp_emcamp_centre_sp95
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=1 | grep -i 'BP Sant Marc' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: BP Sant Marc Canillo sp95
      unique_id: bp_santmarc_canillo_sp95
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=6 | grep -i 'TotalEnergies - SANT ELOI' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: TotalEnergies Sant Eloi Sant Julià de Lòria sp95
      unique_id: totalenergies_santeloi_sp95
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=5 | grep -i 'Repsol Pont de Madrid' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: Repsol Pont de Madrid sp95
      unique_id: repsol_pontmadrid_sp95
      scan_interval: 86400
  - sensor:
      command: curl -Lsk https://sig.govern.ad/IPE/PreusCarburants/GetPreus\?idProducte\=4\&data\=$(date '+%Y-%m-%d')%2023%3A59%3A59\&idParroquia\=3 | grep -i 'Elf Ordino' -A10 | grep '€/l' | cut -d '>' -f2 | cut -d ' ' -f1
      name: Elf Ordino sp95
      unique_id: elf_ordino_sp95
      scan_interval: 86400
```





<details>
<summary> Català </summary>




Amb aquest codi s'obtenen els € per litre d'algunes de les benzineres d'Andorra, inclou els preus més barats i de diferents gasolineres del país.


En aquest exemple s'obtenen els preus de <strong>gasolina sense plom 95</strong> que té el codi 4 a:

```curl -Lsk https://si... ...?idProducte\=4```

si vols canviar a <strong>gasolina sense plom 98</strong> canvia el 4 per un 5:

```curl -Lsk https://si... ...?idProducte\=5```

si vols canviar a <strong>Diesel</strong> canvia el 4 per un 6:

```curl -Lsk https://si... ...?idProducte\=6```

si vols canviar a <strong>Diesel super</strong> canvia el 4 per un 8:

```curl -Lsk https://si... ...?idProducte\=8```

o si vols canviar a <strong>Gasoil calefacció</strong> canvia el 4 per un 7:

```curl -Lsk https://si... ...?idProducte\=7```





Si vols obtindre qualsevol altra benzinera que està a la web has d'escriure el nom exactament igual que està escrit aquí i segons on estigui canviar el número de parròquia:

```curl -Lsk https://si... ...&idParròquia\=1``` = Canillo

```curl -Lsk https://si... ...&idParròquia\=2``` = Encamp

```curl -Lsk https://si... ...&idParròquia\=3``` = Ordino

```curl -Lsk https://si... ...&idParròquia\=4``` = La Massana

```curl -Lsk https://si... ...&idParròquia\=5``` = Andorra la Vella

```curl -Lsk https://si... ...&idParròquia\=6``` = Sant Julià de Lòria

```curl -Lsk https://si... ...&idParròquia\=7``` = Escaldes-Engordany

</details>


<details>
<summary> Español </summary>



  
Con este código se obtienen los € por litro de algunas de las Gasolineras de Andorra, incluye los precios más baratos y de diferentes Gasolineras del pais.


En este ejemplo se obtiene los precios de <strong>gasolina sin plomo 95</strong> que tiene el codigo 4 en: 

```curl -Lsk https://si... ...?idProducte\=4```

si quieres cambiar a <strong>gasolina sin plomo 98</strong> cambia el 4 por un 5:

```curl -Lsk https://si... ...?idProducte\=5```

si quieres cambiar a <strong>Diesel</strong> cambia el 4 por un 6:

```curl -Lsk https://si... ...?idProducte\=6```

si quieres cambiar a <strong>Diesel super</strong> cambia el 4 por un 8:

```curl -Lsk https://si... ...?idProducte\=8```

o si quieres cambiar a <strong>Gasoil calefacción</strong> cambia el 4 por un 7:

```curl -Lsk https://si... ...?idProducte\=7```





Si quieres obtener cualquier otra gasolinera que está en la web debes escribir el nombre exactamente igual que está escrito ahi y según donde esté cambiar el número de parroquia:

```curl -Lsk https://si... ...&idParroquia\=1``` = Canillo

```curl -Lsk https://si... ...&idParroquia\=2``` = Encamp

```curl -Lsk https://si... ...&idParroquia\=3``` = Ordino

```curl -Lsk https://si... ...&idParroquia\=4``` = La Massana

```curl -Lsk https://si... ...&idParroquia\=5``` = Andorra la Vella

```curl -Lsk https://si... ...&idParroquia\=6``` = Sant Julià de Lòria

```curl -Lsk https://si... ...&idParroquia\=7``` = Escaldes-Engordany

</details>

<details>
<summary> Français </summary>




Avec ce code, vous obtenez des € par litre dans certaines stations-service d'Andorre, il comprend les prix les moins chers et dans différentes stations-service du pays.


Dans cet exemple, les prix de l'<strong>essence sans plomb 95</strong> portant le code 4 sont obtenus dans :

```curl -Lsk https://si... ...?idProducte\=4```

Si vous souhaitez passer à l'<strong>essence sans plomb 98</strong>, remplacez le 4 par un 5 :

```curl -Lsk https://si... ...?idProducte\=5```

Si vous souhaitez passer au <strong>Diesel</strong>, remplacez le 4 par un 6 :

```curl -Lsk https://si... ...?idProducte\=6```

Si vous souhaitez passer au <strong>Super Diesel</strong>, remplacez le 4 par un 8 :

```curl -Lsk https://si... ...?idProducte\=8```

ou si vous souhaitez passer au <strong>Chauffage fioul</strong> remplacez le 4 par un 7 :

```curl -Lsk https://si... ...?idProducte\=7```





Si vous souhaitez obtenir une autre station-service présente sur le site Web, vous devez écrire le nom exactement de la même manière qu'il y est écrit et selon l'endroit où elle se trouve, changer le numéro de paroisse :

```curl -Lsk https://si... ...&idParroquia\=1``` = Canillo

```curl -Lsk https://si... ...&idParroquia\=2``` = Encamp

```curl -Lsk https://si... ...&idParroquia\=3``` = Ordino

```curl -Lsk https://si... ...&idParroquia\=4``` = La Massana

```curl -Lsk https://si... ...&idParroquia\=5``` = Andorre-la-Vieille

```curl -Lsk https://si... ...&idParroquia\=6``` = Sant Julià de Lòria

```curl -Lsk https://si... ...&idParroquia\=7``` = Escaldes-Engordany

</détails>


<details>
<summary> English </summary>

With this code you can get the € per litre for some of the gas stations in Andorra, including the cheapest prices from different gas stations in the country.

In this example you get the prices for <strong>95 unleaded gasoline</strong> which has the code 4 in:

```curl -Lsk https://si... ...?idProducte\=4```

if you want to change to <strong>98 unleaded gasoline</strong> change the 4 for a 5:

```curl -Lsk https://si... ...?idProducte\=5```

if you want to change to <strong>Diesel</strong> change the 4 for a 6:

```curl -Lsk https://si... ...?idProducte\=6```

if you want to change to <strong>Super Diesel</strong> change the 4 for an 8:

```curl -Lsk https://si... ...?idProducte\=8```

or if you want to change to <strong>Heating diesel</strong> change the 4 for a 7:

```curl -Lsk https://si... ...?idProducte\=7```

If you want to get any other gas station that is on the web you must write the name exactly as it is written there and depending on where it is, change the parish number:

```curl -Lsk https://si... ...&idParroquia\=1``` = Canillo

```curl -Lsk https://si... ...&idParroquia\=2``` = Encamp

```curl -Lsk https://si... ...&idParroquia\=3``` = Ordino

```curl -Lsk https://si... ...&idParroquia\=4``` = La Massana

```curl -Lsk https://si... ...&idParroquia\=5``` = Andorra la Vella

```curl -Lsk https://si... ...&idParroquia\=6``` = Sant Julià de Loria

```curl -Lsk https://si... ...&idParroquia\=7``` = Escaldes-Engordany

</details>

Home Assistant Grid card:
```
square: false
columns: 2
type: grid
cards:
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/AndoRRacing.png
          - type: markdown
            content: |
              **Av Príncep Benlloch,84**
      - type: entity
        icon: mdi:gas-station-in-use-outline
        name: " sp95"
        entity: sensor.andorracing_andorra_la_vella_sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/AndoRRacing.png
          - type: markdown
            content: |-
              **A. la Vella**
              *8-22h*
      - type: entity
        icon: mdi:gas-station
        name: " sp98"
        entity: sensor.andorracing_andorra_la_vella_sp98
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/totalenergies.png
          - type: markdown
            content: |-
              **Sant Eloi, 
              St Julià de Lòria**
              *24h*
      - type: entity
        icon: mdi:gas-station-outline
        name: " sp95"
        unit: €/l
        entity: sensor.totalenergies_sant_eloi_sant_julia_de_loria_sp95
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/repsol.png
          - type: markdown
            content: |-
              **Av Enclar,1 
              A. la Vella**
              *24h*
      - type: entity
        icon: mdi:gas-station-outline
        state_color: false
        name: sp95
        entity: sensor.repsol_pont_de_madrid_sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/cepsa.png
          - type: markdown
            content: |-
              **C/Prat de la Creu,45 
              A. la Vella** 
              *24h*
      - type: entity
        icon: mdi:gas-station-outline
        name: " sp95"
        entity: sensor.cepsa_unnic_sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/totalenergies.png
          - type: markdown
            content: |-
              **Av del Fener,13 
              Escaldes-Engordany**
              *7-23h*
      - type: entity
        icon: mdi:gas-station-outline
        name: " sp95"
        entity: sensor.escaldes_engordany_totalenergies_artal1_sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/shell.png
          - type: markdown
            content: |-
              **Av La Bartra, bloc1 
              Encamp**
              *7-22h*
      - type: entity
        icon: mdi:gas-station-outline
        name: " sp95"
        unit: €/l
        entity: sensor.shell_encamp_sp95
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/bp.png
          - type: markdown
            content: |-
              **Av François Mitterrand, 84
              Encamp**
              *7-23h*
      - type: entity
        entity: sensor.bp_encamp_centre_i_sp95
        icon: mdi:gas-station-outline
        state_color: false
        name: sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/repsol.png
          - type: markdown
            content: |-
              **Av François Miterrand,
              Encamp**
              *24h*
      - type: entity
        icon: mdi:gas-station-outline
        state_color: false
        name: sp95
        entity: sensor.repsol_pont_de_madrid_sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/bp.png
          - type: markdown
            content: |-
              **CG2, 
              Canillo**
              *7'30-22h*
      - type: entity
        entity: sensor.bp_sant_marc_canillo_sp95
        icon: mdi:gas-station-outline
        name: sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/elf.png
          - type: markdown
            content: |-
              **CG3, 
              Ordino** 
              *7'30-21h*
      - type: entity
        icon: mdi:gas-station-outline
        name: " sp95"
        entity: sensor.elf_ordino_sp95
        unit: €/l
  - type: vertical-stack
    cards:
      - type: horizontal-stack
        cards:
          - type: picture
            tap_action:
              action: none
            hold_action:
              action: none
            image: /local/AndoRRacing.png
          - type: markdown
            content: |
              *8-22h*
      - type: entity
        icon: mdi:fuel
        name: " gasoil"
        entity: sensor.andorracing_andorra_la_vella_gasoil
        unit: €/l
title: Preus Carburants d'Andorra
```
