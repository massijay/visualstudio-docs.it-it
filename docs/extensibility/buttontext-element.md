---
title: "Elemento ButtonText | Microsoft Docs"
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
  - "Elemento ButtonText (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, ButtonText"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento ButtonText
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo campo consente di specificare il testo visualizzato in diversi menu. Per impostazione predefinita, il `ButtonText` elemento compare in un controller di menu. Il `ButtonText` elemento diventa anche il valore predefinito se gli altri campi di testo sono vuoti. Il `ButtonText` elemento non può essere vuoto, anche se vengono specificati altri campi di testo.  
  
## Sintassi  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento di stringhe](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad esempio `ButtonText` e `CommandName`.|  
  
## Valore di testo  
 Il valore di testo il `ButtonText` elemento fornisce il testo visualizzato per le voci di menu, casella combinata e altri elementi dell'interfaccia utente contenenti testo visibile.  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)