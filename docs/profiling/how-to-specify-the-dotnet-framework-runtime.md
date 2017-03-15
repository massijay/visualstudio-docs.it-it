---
title: "Procedura: Specificare il runtime di .NET Framework da profilare negli scenari di esecuzione side-by-side | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, versioni di .NET Framework"
  - "versioni di .NET Framework, profilatura"
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Specificare il runtime di .NET Framework da profilare negli scenari di esecuzione side-by-side
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con la versione [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], le applicazioni possono essere composte da moduli compilati utilizzando versioni diverse del runtime di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilano il primo runtime caricato dall'applicazione.  È possibile specificare il runtime di cui eseguire il profilo quando si avvia un'applicazione con il profiler e quando si connette il profiler a un'applicazione già in esecuzione.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Per specificare il runtime di .NET Framework di cui eseguire il profilo quando si avvia un'applicazione con il profiler  
  
1.  In **Esplora prestazioni**, fare clic con il pulsante destro del mouse sulla sessione di prestazioni, fare clic su **Proprietà**, quindi scegliere **Avanzate**.  
  
     Nella casella di riepilogo **Versione CLR di destinazione** viene visualizzato **Automatico** e le versioni del runtime di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installate nel computer.  
  
2.  Effettuare uno dei passaggi riportati di seguito:  
  
    -   Fare clic sulla versione del CLR di cui si desidera eseguire il profilo.  
  
    -   Scegliere **Automatico** per eseguire il profilo della prima versione caricata dall'applicazione.  
  
### Per specificare il runtime di .NET Framework di cui eseguire il profilo quando si connette il profiler a un'applicazione  
  
1.  Scegliere Profiler dal menu Analizza, quindi fare clic su Connetti\/Disconnetti.  
  
2.  Nella finestra di dialogo Connettere profiler a processo, fare clic sul processo di cui si desidera eseguire il profilo.  
  
     Nella casella di riepilogo **Versione CLR di destinazione** viene visualizzato **Automatico** e le versioni del runtime di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installate nel computer.  
  
3.  Effettuare uno dei passaggi riportati di seguito:  
  
    -   Fare clic sulla versione del CLR di cui si desidera eseguire il profilo.  
  
    -   Scegliere **Automatico** per eseguire il profilo della prima versione caricata quando il profiler viene connesso all'applicazione.