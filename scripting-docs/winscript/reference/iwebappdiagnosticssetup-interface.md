---
title: "Interfaccia IWebAppDiagnosticsSetup | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IWebAppDiagnosticsSetup"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IWebAppDiagnosticsSetup
L'interfaccia viene implementata da un'applicazione di debug di PDM creare oggetti COM nel processo sottoposto a debug e abilitare la diagnostica Web.  Se [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)viene implementata dall'oggetto applicazione di debug di PDM, chiamate [Funzione SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) di Internet Explorer su dopo essere stato creato e passa un riferimento a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449).  Le chiamate [Funzione SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) e le sessioni di un'applicazione di WWA in WWA interfaccia IWebApplicationHost anziché.  Se [Funzione SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) viene chiamato con un valore non Null, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce true.  In caso contrario, restituisce false e le chiamate a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) non superati.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` implementato da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ottiene i documenti di testo che sono invisibili al filtro specificato.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|