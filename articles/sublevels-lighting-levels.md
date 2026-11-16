id: sublevels-lighting-levels
kind: recipe
title: Subníveis e Lighting Levels empilháveis | Sublevels and stackable Lighting Levels
keys: subnivel, subniveis, sublevel, sublevels, painel levels, levels panel, janela niveis, window levels, nivel persistente, persistent level, nivel atual, current level, make current, tornar atual, mover atores para o nivel, move actors to level, travar nivel, lock level, carregado no inicio, initially loaded, adicionar existente, add existing, criar novo nivel, create new level, lighting level, lighting levels, light level, cenario de iluminacao, lighting scenario, varios lighting levels, multiple lighting scenarios, iluminacao somada, added lighting, dia e noite, day and night, luzes da rua, street lights, build lighting por nivel, set lighting level visible, is lighting level visible, load stream level, rlevels
--- pt
**Janela > Níveis** é o painel Levels da Unreal: o **Nível Persistente** (o arquivo aberto) e os **subníveis**, outros níveis do projeto carregados no mesmo mundo, cada um salvo no próprio `.rlevel` (bom para dividir o trabalho: a arte num, a jogabilidade noutro, a iluminação noutro).
- **Adicionar Existente...** escolhe um nível do projeto; **Criar Novo...** cria um vazio ao lado e já o torna o atual.
- Cada linha: o **olho** (mostra/esconde no editor), a cor, o nome (`*` = alterado), **Lighting**, **Carregado no Início** e **Travar** (não seleciona nem move). Clique duas vezes num nível para torná-lo o **atual**: os atores novos (colocados, arrastados, colados) vão para ele. Botão direito: Tornar Atual, Mover Atores Selecionados para o Nível, Selecionar Atores, Salvar Nível, Remover.
- **Salvar** (Ctrl+S) grava o persistente sem os atores dos subníveis, cada subnível alterado no arquivo dele e a lista `<nível>.rlevels`.
- **Play e jogo**: entram só os subníveis **Carregados no Início**; os outros entram por **Load Stream Level** com o nome deles (e saem por Unload Stream Level).
- **Lighting Levels** (o diferencial): marque **Lighting** num subnível e as luzes dele viram uma iluminação baked própria. O **Build Lighting** faz um bake do nível persistente e depois um de cada Lighting Level sozinho; a iluminação mostrada é a **soma** dos que estão visíveis. Na Unreal só um Lighting Scenario fica ligado por vez; aqui quantos quiser ao mesmo tempo (o dia + os postes da rua + o letreiro da loja), porque a luz é linear e a soma dos bakes é exata.
- **Blueprint**: **Set Lighting Level Visible** (nome, ligado) liga ou desliga um Lighting Level no jogo — as luzes e a parte baked dele — e **Is Lighting Level Visible** diz se está ligado.
- Mudou malhas Static de lugar? Faça o Build Lighting de novo: um bake feito com outras malhas fica de fora da soma (o Output Log avisa).

```diagram steps
Janela > Níveis | Criar Novo... "Lighting_Noite" | marque Lighting | coloque as luzes nele | Build > Build Lighting | o olho liga e desliga a noite
```
```blueprint
Event Begin Play -> Set Lighting Level Visible ( Level Name = "Lighting_Noite", Visible = false )
Event Key N -> Set Lighting Level Visible ( Level Name = "Lighting_Noite", Visible = true )
Event Key L -> Set Lighting Level Visible ( Level Name = "Lighting_Postes", Visible = true )
```
--- en
**Window > Levels** is Unreal's Levels panel: the **Persistent Level** (the file you opened) and its **sublevels**, other levels of the project loaded into the same world, each saved to its own `.rlevel` (good for splitting the work: art in one, gameplay in another, lighting in another).
- **Add Existing...** picks a level of the project; **Create New...** makes an empty one beside it and makes it the current one.
- Each row: the **eye** (show/hide in the editor), its color, its name (`*` = changed), **Lighting**, **Initially Loaded** and **Lock** (not selected or moved). Double-click a level to make it **current**: new actors (placed, dragged, pasted) go into it. Right-click: Make Current, Move Selected Actors to Level, Select Actors, Save Level, Remove.
- **Save** (Ctrl+S) writes the persistent level without the sublevels' actors, each changed sublevel to its own file and the list `<level>.rlevels`.
- **Play and the game**: only the **Initially Loaded** sublevels come in; the others come in with **Load Stream Level** by their name (and leave with Unload Stream Level).
- **Lighting Levels** (the difference): tick **Lighting** on a sublevel and its lights become a baked lighting of their own. **Build Lighting** bakes the persistent level, then each Lighting Level alone; the lighting shown is the **sum** of the visible ones. In Unreal only one Lighting Scenario is on at a time; here as many as you like at once (daylight + the street lamps + the shop sign), because light is linear and the sum of the bakes is exact.
- **Blueprint**: **Set Lighting Level Visible** (name, on) turns a Lighting Level on or off in the game — its lights and its baked share — and **Is Lighting Level Visible** tells whether it is on.
- Moved Static meshes? Build Lighting again: a bake made with other meshes is left out of the sum (the Output Log says so).

```diagram steps
Window > Levels | Create New... "Lighting_Night" | tick Lighting | put its lights in it | Build > Build Lighting | the eye turns the night on and off
```
```blueprint
Event Begin Play -> Set Lighting Level Visible ( Level Name = "Lighting_Night", Visible = false )
Event Key N -> Set Lighting Level Visible ( Level Name = "Lighting_Night", Visible = true )
Event Key L -> Set Lighting Level Visible ( Level Name = "Lighting_StreetLamps", Visible = true )
```
