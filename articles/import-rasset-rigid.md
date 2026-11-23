id: import-rasset-rigid
kind: howto
title: .rasset e rigs rígidos (peças presas a ossos) | .rasset and rigid rigs (pieces parented to bones)
keys: rasset, empacotado, packed, normalroughnessmetallic, basecolor, emissive, exportar para a real engine, export to real engine, formato de troca, exchange format, osso pai, bone parent, parent to bone, rig rigido, rigid rig, robo, robot, capsula, maquina, machine, skeletal mesh nao criado, no skeletal mesh, controles do rig, rig widgets, custom shape, textura borrada, blurry texture, 4k, 4096
--- pt
```diagram steps
Tlender: Exportar > Real Engine (.rasset) | Arquivo > Importar ou arrastar o .rasset | Malhas, materiais, esqueleto, animações | Skeletal Mesh no nível
```
## O .rasset
- O **.rasset** é o formato de troca com o Tlender (Exportar > Real Engine). **Arquivo > Importar** ou arraste o arquivo: viram malhas, materiais PBR com as imagens que vêm dentro dele, o esqueleto, a malha com skin como **Skeletal Mesh**, as animações, morph targets, luzes e câmeras. [Mostrar onde](show:File>Import Into Level...)
- Um .rasset que já está no Content Browser: arraste-o para o viewport e ele é importado e colocado.
- Pesos de morph animados viram curvas de morph da animação.
- As trilhas de objeto (um objeto que se move, não um osso) ainda não entram: o Relatório de Importação avisa.

## Rigs rígidos: peças presas a ossos
- Robôs, cápsulas e máquinas costumam ter cada peça **presa a um osso** (Parent > Bone), sem modificador Armature. Essas peças viram partes de um **Skeletal Mesh**: cada uma segue o osso inteira, e as animações da armature movem as peças.
- As formas de controle do rig (os "cs_" do Auto-Rig Pro e os widgets do Rigify) e as malhas em coleções desligadas no render **não** são importadas: o relatório conta quantas ficaram de fora.

## Texturas 4K e o conjunto empacotado
- O material é assado no tamanho da maior textura que ele lê, até 4096: uma textura 4K (UDIM ou não) não perde detalhe.
- Texturas exportadas pelo Tlender no preset **Real Engine (empacotado)**: clique direito na `_BaseColor` > Criar > **Material**; a `_NormalRoughnessMetallic` e a `_Emissive` da mesma pasta entram ligadas sozinhas.

--- en
```diagram steps
Tlender: Export > Real Engine (.rasset) | File > Import or drag the .rasset | Meshes, materials, skeleton, animations | Skeletal Mesh in the level
```
## The .rasset
- The **.rasset** is the exchange format with the Tlender (Export > Real Engine). **File > Import** or drag the file: it becomes meshes, PBR materials with the images it carries, the skeleton, the skinned mesh as a **Skeletal Mesh**, animations, morph targets, lights and cameras. [Show me where](show:File>Import Into Level...)
- A .rasset already in the Content Browser: drag it into the viewport and it is imported and placed.
- Animated morph weights become the animation's morph curves.
- Object tracks (an object that moves, not a bone) don't come in yet: the Import Report says so.

## Rigid rigs: pieces parented to bones
- Robots, capsules and machines often have each piece **parented to a bone** (Parent > Bone), with no Armature modifier. Those pieces become parts of a **Skeletal Mesh**: each one follows its bone whole, and the armature's animations move them.
- The rig's control shapes (Auto-Rig Pro's "cs_" objects, Rigify's widgets) and meshes in collections turned off in render are **not** imported: the report counts how many were left out.

## 4K textures and the packed set
- The material is baked at the size of the largest texture it reads, up to 4096: a 4K texture (UDIM or not) keeps its detail.
- Textures the Tlender exported with the **Real Engine (packed)** preset: right-click the `_BaseColor` > Create > **Material**; the `_NormalRoughnessMetallic` and the `_Emissive` in the same folder come wired in.
