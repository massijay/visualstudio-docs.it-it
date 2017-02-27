---
title: "Fornisce l&#39;automazione per il codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Oggetto CodeModel"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Fornisce l&#39;automazione per il codice
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Creare un modello di automazione di per il codice non è obbligatorio.  L'ambiente SDK non fornisce un esempio per questa operazione.  Per visione dei modelli di codice, vedere l'oggetto di <xref:EnvDTE.CodeModel> .  
  
 Per applicare un modello di codice, è necessario implementare tutte le interfacce che sono determinate dalla struttura di dati interna.  Gli oggetti devono essere derivati dalla classe di `IDispatch`.  
  
 Gli oggetti che si estende, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, sono disponibili dall'oggetto di <xref:EnvDTE.Project> e simili alle seguenti:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 È possibile senza per implementare solo `CodeModel` o l'interfaccia di `FileCodeModel` nell'oggetto restituito dagli oggetti di <xref:EnvDTE.ProjectItem> e di `Project` .  Fornire tutte le funzionalità da questa interfaccia appropriata per il sistema del progetto.  
  
 Se si desidera aggiungere funzionalità, come metodi o proprietà, che non sono disponibili in `CodeModel` delle interfacce e standard di `FileCodeModel` , creare la propria interfaccia che eredita dallo standard.  Assicurarsi di documentarlo nel sistema del progetto in modo che gli utenti finali sapranno per trovarlo.  Restituire l'interfaccia standard, ma l'utente può chiamare il metodo o il cast di `QueryInterface` l'interfaccia se è noto che esistano.  
  
## Vedere anche  
 [Cenni preliminari sul modello di automazione](../../extensibility/internals/automation-model-overview.md)