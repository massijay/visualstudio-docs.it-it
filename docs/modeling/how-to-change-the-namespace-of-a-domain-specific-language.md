---
title: "Procedura: modificare lo spazio dei nomi di un linguaggio specifico di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, spazio dei nomi"
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
caps.handback.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Procedura: modificare lo spazio dei nomi di un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio.  È necessario apportare la modifica in **DSL Esplora Risorse**, nelle proprietà del progetto del pacchetto di Dsl e le informazioni dell'assembly.  
  
### Per modificare lo spazio dei nomi di un linguaggio specifico di dominio  
  
1.  in **DSL Esplora Risorse**, fare clic su  **Dsl** nodo.  
  
2.  in **proprietà** la finestra, modifica  **Spazio dei nomi** proprietà.  
  
3.  salvare la soluzione e trasformare i modelli.  
  
4.  In **progetto** menu, fare clic su  **proprietà di Dsl**.  
  
     Verranno visualizzate le proprietà per il progetto.  
  
5.  Fare clic sulla scheda **Applicazione**.  
  
6.  modificare **Per impostazione predefinita lo spazio dei nomi** proprietà al nuovo nome dello spazio dei nomi.  
  
7.  Se inoltre si desidera modificare il nome dell'assembly, modificare **Proprietà del nome assembly.**  
  
8.  Se si modifica il nome di assembly, DslPackage aperto \\Package .tt e aggiorna la riga seguente:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Se è stato scritto un codice personalizzato, assicurarsi di modificare lo spazio dei nomi e classificare i riferimenti nei file di codice.  
  
10. Reimpostare istanza sperimentale di Visual Studio.  
  
    1.  Eliminazione **\\Users\\***{nome}***\\AppData\\Local\\Microsoft\\VisualStudio\\\*Exp**  
  
    2.  In windows **inizio** il menu, selezionare  **Tutti i programmi**,  **Microsoft Visual Studio 2010 SDK**,  **strumenti**,  **reimpostare l'istanza sperimentale**.  
  
11. In **Compilazione** il menu, selezionare  **Soluzione di ricompilazione**.  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)