---
title: "Prerequisiti per la distribuzione di applicazioni a 64 bit | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 bit [Visual Studio]"
  - "64 bit (applicazioni) [Visual Studio]"
  - "64 bit (programmazione) [Visual Studio]"
  - "distribuzione di applicazioni [Visual Studio], 64 bit"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Prerequisiti per la distribuzione di applicazioni a 64 bit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La distribuzione ClickOnce supporta l'installazione di applicazioni su piattaforme a 64 bit.  Le piattaforme di destinazione sono **x86** per le piattaforme a 32 bit, **x64** per i computer che supportano i set di istruzioni AMD64 ed EM64T e **Itanium** per il processore Itanium a 64 bit.  
  
## Prerequisiti  
 La tabella seguente elenca i componenti ridistribuibili che è possibile usare come prerequisiti per l'installazione dell'applicazione a 64 bit.  
  
 Se si seleziona un prerequisito che non ha componenti a 64 bit, è possibile che venga visualizzato un avviso che indica che i pacchetti selezionati non sono disponibili per la piattaforma a 64 bit.  
  
|Componente ridistribuibile|Supporto x64|Supporto IA64|  
|--------------------------------|------------------|-------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Sì|No|  
|Librerie di runtime di Visual C\+\+ 2010 \(IA64\)|No|Sì|  
|Librerie di runtime di Visual C\+\+ 2010 \(x64\)|Sì|No|  
|Microsoft .NET Framework 4 \(x86 e x64\)|Sì||  
|Microsoft .NET Framework 4 Client Profile \(x86 e x64\)|Sì||  
  
## Vedere anche  
 [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Applicazioni a 64 bit](../Topic/64-bit%20Applications.md)