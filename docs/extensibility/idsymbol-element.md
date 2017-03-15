---
title: "Elemento IDSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento IDSymbol (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, IDSymbol"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Elemento IDSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il `IDSymbol` elemento contiene l'ID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. Il GUID fornito dall'elemento padre `GuidSymbol` elemento. Il `IDSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per l'ID, che è contenuto nel `value` attributo.  
  
## Sintassi  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|nome|Obbligatorio. Nome del simbolo ID.|  
|valore|Obbligatorio. Valore ID numerico del simbolo ID.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene il GUID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. Raggruppa gli elementi `IDSymbol`.|  
  
## Note  
 Ogni `IDSymbol` elemento in un determinato `GuidSymbol` elemento deve essere univoco `value`. Tuttavia, `IDSymbol` possono essere presenti elementi che hanno valori identici in un pacchetto, purché dispongano di diversi elementi padre.  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)