---
title: "Attributi condizionali dello Schema XML VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, attributi condizionali"
  - "attributi condizionali (VSCT XML schema)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Attributi condizionali dello Schema XML VSCT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Attributi condizionali possono essere applicati a tutti gli elementi e gli elenchi. Simbolo espansione espressioni e operatori logici restituiscono true o false. Se true, l'elenco associato o l'elemento è incluso nell'output risultante.  
  
 È possibile testare le espansioni token con altri token espansioni o costanti. La funzione Defined\(\) viene utilizzata per verificare se è stato definito un determinato nome, anche se non ha alcun valore.  
  
 Quando un attributo di condizione viene applicato a un elenco, la condizione viene applicata a ogni elemento figlio nell'elenco. Se un elemento figlio contiene un attributo Condition, la condizione viene combinata con l'espressione padre da un'operazione di AND.  
  
 I valori 1, '1' e 'true' vengono valutati come true e 0, '0' e 'false' vengono valutate come false.  
  
## Operatori  
 Possono utilizzare i seguenti operatori per valutare le espressioni condizionali.  
  
|Operatore|Definizione|  
|---------------|-----------------|  
|\(,\)|Raggruppamento|  
|\!|NOT logico|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|Relazionale e uguaglianza|  
|e|Booleano|  
|oppure|Booleano|  
  
## Esempi  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)