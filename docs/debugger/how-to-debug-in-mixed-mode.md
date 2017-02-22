---
title: "Procedura: eseguire il debug in modalit&#224; mista | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], modalità mista"
  - "debug di DLL"
  - "debug in modalità mista"
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: eseguire il debug in modalit&#224; mista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nelle procedure riportate di seguito viene spiegato come eseguire il debug in modalità mista, ovvero sia di codice gestito che di codice nativo.  Gli scenari possibili sono due, a seconda che la DLL o l'applicazione sia scritta in codice nativo:  
  
-   L'applicazione che chiama la DLL è scritta in codice nativo.  In tal caso, la DLL è gestita ed è necessario attivare sia il debugger del codice gestito sia quello del codice nativo per eseguire il debug di entrambi.  È possibile eseguire questa verifica nella finestra di dialogo **Pagine delle proprietà di \<Progetto\>**.  L'esecuzione di questa operazione varia a seconda che il debug venga avviato dal progetto della DLL o da quello dell'applicazione chiamante.  
  
-   L'applicazione che chiama la DLL è scritta in codice gestito e la DLL è scritta in codice nativo.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per abilitare il debug in modalità mista  
  
1.  Selezionare il progetto in **Esplora soluzioni**.  
  
2.  Scegliere **Pagine delle proprietà** dal menu **Visualizza**.  
  
3.  Nella finestra di dialogo **Pagine delle proprietà di \<Progetto\>** espandere il nodo **Proprietà di configurazione** e selezionare **Debug**.  
  
4.  Impostare **Tipo debugger** su **Misto** o **Automatico**.  
  
## Vedere anche  
 [Procedura: eseguire il debug da un progetto di DLL](../debugger/how-to-debug-from-a-dll-project.md)