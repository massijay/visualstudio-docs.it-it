---
title: "Ordinamento, filtro e raggruppamento (XML Schema Explorer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Ordinamento, filtro e raggruppamento (XML Schema Explorer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono descritte le opzioni disponibili tramite il menu **Opzioni di ordinamento, filtro e raggruppamento** nella barra degli strumenti di XML Schema Explorer.  
  
## Opzioni del filtro  
 Sono disponibili le seguenti opzioni del filtro.Le opzioni **Mostra spazi dei nomi** e **Mostra file di schema** sono selezionate per impostazione predefinita.  
  
-   **Mostra spazi dei nomi**.  
  
-   **Mostra file di schema**.  
  
-   **Mostra compositor \(sequence\/choice\/all\)**.  
  
## Opzioni di ordinamento  
 Sono disponibili le seguenti opzioni di ordinamento.L'opzione predefinita è **Ordina per tipo**.Le opzioni Ordina per non si applicano ai file e agli spazi dei nomi.  
  
-   **Ordina per tipo**.  
  
-   **Ordina per nome**.  
  
-   **Ordine del documento**.  
  
### Ordina per tipo  
 Quando è selezionata l'opzione **Ordina per tipo**, i nodi globali vengono ordinati nell'ordine seguente.All'interno di ciascun gruppo i nodi vengono ordinati alfabeticamente.  
  
1.  Nodi `import`.  
  
2.  Nodi `include`.  
  
3.  Nodi `redefine`.  
  
4.  Nodi `attribute`.  
  
5.  Nodi `attributeGroup`.  
  
6.  Nodi `complexType`.  
  
7.  Nodi `simpleType`.  
  
8.  Nodi `element`.  
  
9. Nodi `group`.  
  
### Ordina per nome  
 Quando è selezionata l'opzione **Ordina per nome**, i nodi globali vengono ordinati nell'ordine seguente:  
  
1.  Nodi `import` \(in ordine alfabetico degli spazi dei nomi\).  
  
2.  Nodi `include` \(in ordine alfabetico degli attributi `schemaLocation`\).  
  
3.  Nodi `redefine` \(in ordine alfabetico degli attributi `schemaLocation`\).  
  
4.  Altri nodi globali in ordine alfabetico.  
  
### Ordine documenti  
 L'opzione **Ordine documenti** è disponibile quando viene selezionata l'opzione **Mostra file di schema**.Selezionando l'opzione **Ordine documenti**, i nodi globali vengono visualizzati nell'ordine nel quale sono presenti nel file di schema.  
  
## Persistenza delle opzioni di ordinamento e filtro  
 Le opzioni di ordinamento, filtro e raggruppamento vengono salvate nel Registro di sistema per ogni utente, indipendentemente dalla soluzione o dai file aperti quando sono state modificate le impostazioni.