---
title: "Riferimento (acquisizione a livello di codice) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Riferimento (acquisizione a livello di codice)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diagnostica grafica supporta il controllo a livello di programmazione sulle funzionalità di acquisizione, tramite l'API di acquisizione a livello di programmazione.  È possibile utilizzare questa API per attivare o disattivare e aggiungere messaggi alla diagnostica grafica HUD \(Head\-Up Display\), inizializzare e creare file di log di grafica e acquisire informazioni grafiche.  
  
## API di acquisizione a livello di programmazione  
  
### Classi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Classe VsgDbg](../debugger/vsgdbg-class.md)|Rappresenta l'interfaccia attraverso cui il componente in\-app di diagnostica grafica è controllato a livello di programmazione.|  
  
### Simboli del preprocessore  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.|  
|[VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)|Definisce il nome file predefinito del file di log di grafica.|  
|[VSG\_NODEFAULT\_INSTANCE](../debugger/vsg-nodefault-instance.md)|Quando presente, definisce se viene fornita un'istanza predefinita della classe `VsgDbg`.|  
  
## Articoli correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Cattura informazioni grafica](../debugger/capturing-graphics-information.md)|Viene indicato come acquisire informazioni grafiche dall'app basata su DirectX per poter usare gli strumenti di diagnostica grafica [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per diagnosticare problemi di rendering.|  
|[Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Viene indicato come la diagnostica grafica consente di eseguire il debug degli errori di rendering nei giochi e nelle app DirectX.|