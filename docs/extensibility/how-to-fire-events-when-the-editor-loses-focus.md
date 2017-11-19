---
title: 'Procedura: generare eventi quando l''Editor perde lo stato attivo | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a566d52dc1aabb9895e2f1f9751fdb37ae016d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Procedura: generare eventi quando l'Editor perde lo stato attivo
In alcuni casi è necessario sapere quando un editor perde lo stato attivo sulla cornice finestra. È ad esempio, potrebbe essere necessario estrarre codice da una finestra del codice dopo l'editor non è più incentrata su di esso. La procedura seguente fornisce i passaggi da seguire per ricevere la notifica dell'editor perde lo stato attivo.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Per generare un evento in risposta a un editor perde lo stato attivo  
  
1.  Monitorare gli eventi di selezione ottenendo un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> oggetto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e fornirlo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> oggetto.  
  
3.  Nella chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, cercare `elementid==SEID_WindowFrame`.  
  
4.  Test di `varValueNew` parametro per due scopi:  
  
    1.  Si sta cercando la cornice della finestra.  
  
    2.  Il punto in cui il programma perde la selezione verso la cornice della finestra.