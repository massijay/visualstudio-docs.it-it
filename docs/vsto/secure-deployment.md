---
title: "Distribuzione sicura"
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
  - "distribuzione ClickOnce [sviluppo per Office in Visual Studio], sicurezza"
  - "distribuzione di applicazioni [sviluppo per Office in Visual Studio], sicurezza"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], sicurezza"
  - "sviluppo per Office in Visual Studio, sicurezza"
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Distribuzione sicura
  Quando si crea una soluzione Office, il computer di sviluppo viene aggiornato automaticamente per consentire l'esecuzione del codice nel progetto.  Tuttavia, quando si distribuisce la soluzione, è necessario fornire l'evidenza su cui basare una decisione di attendibilità firmando la soluzione con un certificato o utilizzando la chiave di richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  Per ulteriori informazioni, vedere [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per le personalizzazioni a livello di documento, se si distribuisce il documento a un percorso della rete, è necessario aggiungere anche il percorso del documento all'elenco dei percorsi attendibili nel Centro protezione dell'applicazione di Office.  Per ulteriori informazioni su come impostare le autorizzazioni dei documenti nei computer degli utenti finali, vedere [Concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).  
  
## Impedire l'esecuzione di codice da parte di soluzioni Office  
 Gli amministratori possono utilizzare il Registro di sistema per impedire l'esecuzione di tutte le soluzioni Office in un computer.  Quando una soluzione Office contenente estensioni di codice gestito è aperta, il runtime di Visual Studio Tools per Office controlla se una voce con il nome `Disabled` presente in una delle seguenti chiavi del Registro di sistema sul computer:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Per impedire l'esecuzione di codice da parte di soluzioni Office, creare una voce `Disabled` in una o in entrambe queste chiavi del Registro di sistema e specificare uno dei tipi di dati e valori seguenti per `Disabled`:  
  
-   A REG\_SZ o REG\_EXPAND\_SZ impostato su qualsiasi stringa diversa da "0" \(zero\).  
  
-   A REG\_DWORD impostato su qualunque valore diverso da 0 \(zero\).  
  
 Per consentire l'esecuzione di codice da parte delle soluzioni Office, impostare entrambe le voci `Disabled` su 0 \(zero\) o eliminare le voci del Registro di sistema.  
  
## Vedere anche  
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Preparazione dei computer per l'esecuzione o l'hosting di soluzioni Office](http://msdn.microsoft.com/it-it/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  