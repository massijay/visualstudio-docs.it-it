---
title: "Raccolta di dati di concorrenza di thread e processi | Microsoft Docs"
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
  - "profilatura della concorrenza (metodo)"
  - "strumenti per la profilatura, metodo di concorrenza"
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Raccolta di dati di concorrenza di thread e processi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo di profiling degli strumenti di profilatura concorrenti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di raccogliere dati sui conflitti di risorse che contengono informazioni su ogni evento di sincronizzazione che provoca una funzione nell'applicazione profilata per attendere l'accesso a una risorsa.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 È possibile specificare il metodo di profilo della concorrenza tramite una delle procedure riportate di seguito:  
  
-   Nella prima pagina della procedura guidata di profiling, fare clic su **Concorrenza**  
  
-   Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni, fare clic su **Campionamento**.  
  
-   Scegliere **Concorrenza** nell'elenco **Metodo** sulla barra degli strumenti **Esplora prestazioni**.  
  
## Attività comuni  
 È possibile specificare opzioni aggiuntive nella finestra di dialogo **Pagine delle proprietà** di *Performance Session* della sessione di prestazioni.  Per aprire questa finestra di dialogo:  
  
-   In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e scegliere **Proprietà**.  
  
 Le attività riportate nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo **Pagine delle proprietà** di *Performance Session* quando si esegue il profilo tramite il metodo di concorrenza.  
  
|Attività|Contenuto correlato|  
|--------------|-------------------------|  
|Nella pagina **Generale**, specificare i dettagli di denominazione per il file dei dati di profilo \(vsp\) generato.|-   [Procedura: impostare le opzioni relative ai nomi file dei dati di profilatura](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Nella pagina **Avvio**, specificare l'applicazione da avviare se si dispone di più progetti EXE nella soluzione del codice.|-   [Procedura: Specificare l'inizio del file binario](../profiling/how-to-specify-the-binary-to-start.md)|  
|Nella pagina **Interazione tra livelli**, aggiungere i dati di chiamata ADO.NET all'esecuzione di profilo.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Contatori Windows**, specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilo come contrassegni.|-   [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Nella pagina **Avanzate**, specificare la versione di runtime di .NET Framework di cui eseguire il profilo se i moduli dell'applicazione utilizzano più versioni.  Per impostazione predefinita, viene eseguito il profilo della prima versione caricata.|-   [Procedura: Specificare il runtime di .NET Framework da profilare negli scenari di esecuzione side\-by\-side](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|