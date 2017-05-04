---
title: "Cenni preliminari sul servizio Information Rights Management e sulle estensioni di codice gestito | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documenti [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "Information Rights Management [sviluppo per Office in Visual Studio]"
  - "IRM [sviluppo per Office in Visual Studio]"
  - "documenti Office [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "Rights Management [sviluppo per Office in Visual Studio]"
  - "cartelle di lavoro [sviluppo per Office in Visual Studio], autorizzazioni limitate"
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Cenni preliminari sul servizio Information Rights Management e sulle estensioni di codice gestito
  In Microsoft Office Word e Microsoft Office Excel è disponibile la funzionalità Information Rights Management \(IRM\), che impedisce a utenti non autorizzati di visualizzare o modificare informazioni riservate.  Per informazioni dettagliate sul funzionamento di Information Rights Management, vedere la Guida dell'applicazione di Office specifica.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Esecuzione di codice sottostante documenti con autorizzazioni limitate  
 Se la soluzione contiene un documento o una cartella di lavoro che utilizza il servizio IRM, per impostazione predefinita Word ed Excel non consentono l'esecuzione di alcun codice.  L'autore del documento e gli utenti che dispongono dell'accesso completo possono modificare l'impostazione predefinita in modo che la soluzione funzioni.  Per ulteriori informazioni, vedere [Procedura: supportare l'esecuzione di codice sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 Il servizio IRM impedisce l'uso di <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> per il recupero o la modifica di dati memorizzati nella cache del documento.  
  
## Limitazione delle autorizzazioni dei documenti che utilizzano le estensioni di codice gestito da parte degli utenti finali  
 Gli utenti che dispongono dell'accesso completo al documento o alla cartella di lavoro di una soluzione possono utilizzare la funzionalità IRM per limitare le autorizzazioni.  Se ad esempio un utente finale del reparto contabilità utilizza una soluzione che popola automaticamente un foglio di lavoro con i dati di un database, tale utente può consentire l'accesso per la modifica solo agli utenti del proprio reparto e l'accesso in lettura agli altri.  Se l'utente decide di limitare le autorizzazioni, per impostazione predefinita non è possibile eseguire il code\-behind del foglio di lavoro, che non verrà pertanto popolato con i dati.  
  
 Per risolvere il problema, è necessario che un utente con accesso completo al documento o alla cartella di lavoro modifichi le impostazioni predefinite per le autorizzazioni, per consentire l'accesso al modello a oggetti a livello di codice.  Per ulteriori informazioni, vedere [Procedura: supportare l'esecuzione di codice sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## Vedere anche  
 [Sicurezza dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Sicurezza tramite password di documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  