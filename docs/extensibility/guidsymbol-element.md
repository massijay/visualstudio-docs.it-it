---
title: "Elemento GuidSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, GuidSymbol"
  - "Elemento GuidSymbol (VSCT XML schema)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Elemento GuidSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il `GuidSymbol` elemento contiene il GUID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. L'ID provenienza da un `IDSymbol` elemento il `GuidSymbol` elemento. Il `GuidSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per il GUID, che è contenuto nel `value` attributo.  
  
## Sintassi  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|nome|Obbligatorio. Nome del simbolo GUID.|  
|valore|Obbligatorio. GUID del simbolo GUID.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene l'ID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento di simboli](../extensibility/symbols-element.md)|Gruppi `GuidSymbol` elementi in un file vsct.|  
  
## Note  
 In genere, un file vsct contiene tre `GuidSymbol` elementi relativo `Symbols` sezione, uno per il pacchetto stesso, uno per il set di comandi \(l'insieme di menu, gruppi e i comandi che rende disponibile il pacchetto\) e uno per le bitmap che forniscono le icone per i pulsanti e altri componenti visivi. Ogni `IDSymbol` elemento in un determinato `GuidSymbol` elemento deve essere univoco `value`. Tuttavia, `IDSymbol` possono essere presenti elementi che hanno valori identici in un pacchetto, purché dispongano di diversi elementi padre.  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)