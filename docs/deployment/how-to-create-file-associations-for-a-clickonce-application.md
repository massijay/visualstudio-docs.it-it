---
title: "How to: Create File Associations For a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "file associations, ClickOnce applications"
  - "ClickOnce deployment, file associations"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create File Associations For a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] possono essere associate a una o più estensioni di file, in modo che, all'apertura di un file di un tipo specificato, venga avviata automaticamente l'applicazione desiderata.  L'aggiunta del supporto delle estensioni di file a un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è molto semplice.  
  
### Per creare associazioni di file per un'applicazione ClickOnce  
  
1.  Creare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o utilizzarne una esistente.  
  
2.  Aprire il manifesto dell'applicazione con un editor di testo o XML, quale il Blocco note.  
  
3.  Trovare l'elemento `assembly`.  Per ulteriori informazioni, vedere [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
4.  Aggiungere un elemento `fileAssociation` come figlio dell'elemento `assembly`.  L'elemento `fileAssociation` dispone di quattro attributi.  
  
    -   `extension`: estensione di file da associare all'applicazione.  
  
    -   `description`: descrizione del tipo di file che verrà visualizzata nella shell di Windows.  
  
    -   `progid`: stringa che identifica in modo univoco il tipo di file, per contrassegnarlo nel Registro di sistema.  
  
    -   `defaultIcon`: icona da utilizzare per questo tipo di file.  L'icona deve essere aggiunta come risorsa di file nel manifesto dell'applicazione.  Per ulteriori informazioni, vedere [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Per un esempio degli elementi `file` e `fileAssociation`, vedere [\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Se si desidera associare più tipi di file all'applicazione, aggiungere altri elementi `fileAssociation`.  Notare che l'attributo `progid` deve essere diverso per ognuno.  
  
6.  Una volta ultimate le modifiche nel manifesto dell'applicazione, firmare nuovamente il manifesto.  È possibile effettuare questa operazione eseguendo Mage.exe dalla riga di comando.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Per ulteriori informazioni, vedere [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
## Vedere anche  
 [\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)