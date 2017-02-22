---
title: "Finestra di dialogo Impostazioni di sicurezza avanzate | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.err.debug_in_zone_no_hostproc"
  - "vs.err.debug_in_zone_no_hostproc:11310"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Finestra di dialogo Impostazioni di sicurezza avanzate"
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Finestra di dialogo Impostazioni di sicurezza avanzate
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di specificare le impostazioni di sicurezza relative all'esecuzione del debug in un'area di sicurezza.  
  
 Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni** e quindi scegliere **Proprietà** dal menu **Progetto**.  In **Progettazione progetti** fare clic sulla scheda **Sicurezza**.  Nella pagina **Sicurezza** selezionare **Attiva le impostazioni di sicurezza ClickOnce**, fare clic su **È un'applicazione parzialmente attendibile**, quindi fare clic su **Avanzate**.  
  
## Elenco UIElement  
 **Esegui debug dell'applicazione con il set di autorizzazioni selezionato**  
 Se si seleziona questa casella di controllo, il set di autorizzazioni selezionato nella pagina **Sicurezza** viene utilizzato durante l’esecuzione del debug.  Questa opzione è selezionata per impostazione predefinita.  
  
 Per garantire il funzionamento del debug in un'area di sicurezza, è necessario attivare sia questa opzione che l'opzione **Attiva il processo di hosting di Visual Studio**, disponibile nella pagina **Debug** di **Progettazione progetti**.  
  
 Per i progetti di applicazioni Web browser WPF, l'opzione **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** è selezionata e disabilitata.  
  
 **Concedi all'applicazione accesso al proprio sito di origine**  
 Se si seleziona questa casella di controllo, l'applicazione può accedere al sito Web o alla condivisione del server sulla quale è pubblicata.  Questa opzione è selezionata per impostazione predefinita.  
  
 **Esegui debug dell'applicazione come se fosse stata scaricata dal seguente URL**  
 Se è necessario consentire l'accesso dell'applicazione al sito Web o alla condivisione del server corrispondente all'**URL installazione** specificato nella pagina **Pubblica**, immettere l'URL.  Questa opzione è disponibile solo se viene selezionata l'opzione **Concedi all'applicazione accesso al proprio sito di origine**.  
  
## Vedere anche  
 [Pagina Sicurezza, Progettazione progetti](../../ide/reference/security-page-project-designer.md)