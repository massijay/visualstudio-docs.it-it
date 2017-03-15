---
title: "How to: Include a Data File in a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ClickOnce deployment, data"
  - "deploying applications [ClickOnce], data files"
  - "data access, ClickOnce applications"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Include a Data File in a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A ogni applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installata viene assegnata una directory per la gestione dei dati sul disco locale del computer di destinazione.  Tra i file di dati possono essere inclusi file di qualsiasi tipo: file di testo, file XML e persino file di database di Microsoft Access \(mdb\).  Nelle procedure riportate di seguito viene illustrato come aggiungere un file di dati di qualsiasi tipo nell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Per includere un file di dati utilizzando Mage.exe  
  
1.  Aggiungere il file di dati nella directory dell'applicazione insieme agli altri file dell'applicazione.  
  
     Il nome della directory corrisponde in genere alla versione corrente della distribuzione, ad esempio v1.0.0.0.  
  
2.  Aggiornare il manifesto dell'applicazione in modo che il file risulti incluso nell'elenco.  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     Per effetto di questa attività verrà ricreato l'elenco dei file nel manifesto dell'applicazione e verranno generate automaticamente le firme di hash.  
  
3.  Aprire il manifesto dell'applicazione nell'editor di testo o XML preferito e individuare l'elemento `file` relativo al file che è stato appena aggiunto.  
  
     Se è stato aggiunto un file XML denominato `Data.xml`, questo sarà simile all'esempio di codice riportato di seguito.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Aggiungere l'attributo `type` all'elemento, quindi assegnare il valore `data` all'attributo.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Firmare nuovamente il manifesto dell'applicazione utilizzando la coppia di chiavi o il certificato, quindi firmare nuovamente il manifesto di distribuzione.  
  
     È necessario applicare una nuova firma anche al manifesto di distribuzione perché il relativo hash del manifesto dell'applicazione è cambiato.  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### Per includere un file di dati utilizzando MageUI.exe  
  
1.  Aggiungere il file di dati nella directory dell'applicazione insieme agli altri file dell'applicazione.  
  
2.  Il nome della directory corrisponde in genere alla versione corrente della distribuzione, ad esempio v1.0.0.0.  
  
3.  Scegliere **Apri** dal menu **File** per aprire il manifesto dell'applicazione.  
  
4.  Fare clic sulla scheda **File**.  
  
5.  Nella casella di testo nella parte superiore della scheda immettere la directory contenente i file dell'applicazione, quindi scegliere il pulsante **Popola**.  
  
     Il file di dati verrà visualizzato nella griglia.  
  
6.  Impostare il valore **Tipo file** del file di dati su **Dati**.  
  
7.  Salvare il manifesto dell'applicazione, quindi firmare nuovamente il file.  
  
     Verrà chiesto di applicare una nuova firma al file.  
  
8.  Firmare nuovamente il manifesto di distribuzione.  
  
     È necessario applicare una nuova firma anche al manifesto di distribuzione perché il relativo hash del manifesto dell'applicazione è cambiato.  
  
## Vedere anche  
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)