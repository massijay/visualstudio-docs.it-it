---
title: "Procedura: supportare l&#39;esecuzione di codice sottostante i documenti con autorizzazioni limitate | Microsoft Docs"
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
  - "codice [sviluppo per Office in Visual Studio], esecuzione sotto documenti con restrizioni"
  - "documenti [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "Information Rights Management [sviluppo per Office in Visual Studio]"
  - "IRM [sviluppo per Office in Visual Studio]"
  - "documenti Office [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "autorizzazioni [sviluppo per Office in Visual Studio]"
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Procedura: supportare l&#39;esecuzione di codice sottostante i documenti con autorizzazioni limitate
  È possibile utilizzare la funzionalità Information Rights Management \(IRM\) di Microsoft Office per limitare le autorizzazioni per un documento o una cartella di lavoro.  Per impostazione predefinita, il codice di un documento di Microsoft Office Word o di una cartella di lavoro di Microsoft Office Excel con restrizioni non può essere eseguito.  È possibile modificare l'impostazione predefinita in modo che le estensioni di codice gestito siano in grado di accedere al modello a oggetti e la soluzione funzioni.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Possono modificare le impostazioni delle autorizzazioni solo l'autore del documento o della cartella di lavoro e gli utenti che dispongono dell'accesso completo.  
  
### Per supportare l'esecuzione del codice sottostante i documenti con autorizzazioni limitate  
  
1.  Aprire il documento o la cartella di lavoro in Word o Excel.  
  
2.  Fare clic sulla scheda **Il file**, scegliere **Prepara**, scegliere **Limita autorizzazioni**quindi scegliere **Accesso limitato**.  
  
    > [!NOTE]  
    >  Al primo utilizzo, viene chiesto di installare il client Windows Rights Management.  Dopo avere installato il client, potrebbe essere necessario ripetere la procedura.  
  
3.  Nella finestra di dialogo **Autorizzazione**, selezionare **Limita autorizzazioni per il documento**, quindi fare clic su **Altre opzioni**.  
  
4.  In **Autorizzazioni aggiuntive per gli utenti** selezionare **Accesso al contenuto a livello di codice**.  
  
 Word o Excel consentirà l'accesso al modello a oggetti a livello di codice.  
  
## Vedere anche  
 [Cenni preliminari sul servizio Information Rights Management e sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Sicurezza dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Sicurezza tramite password di documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  