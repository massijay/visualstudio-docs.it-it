---
title: "Implementazione delle interfacce helper Smart Host | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfacce helper Smart Host, implementazione"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Implementazione delle interfacce helper Smart Host
L'interfaccia [Interfaccia IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) semplifica notevolmente l'attività di creazione di uno SmartHost per il debug attivo, in quanto fornisce le implementazioni di interfacce necessarie per l'hosting intelligente.  
  
 Per essere uno SmartHost utilizzando `IDebugDocumentHelper`, un'applicazione host deve essere eseguita solo tre operazioni:  
  
1.  `CoCreate` l'amministratore del processo di debug e utilizza l'interfaccia [Interfaccia IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) per aggiungere l'applicazione all'elenco di applicazioni sottoponibili a debug.  
  
2.  Creare un supporto del documento di debug per ogni oggetto script, utilizzando il metodo [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  Assicurarsi che il nome del documento, il documento padre, il testo e i blocchi di script siano definiti.  
  
3.  Implementare l'interfaccia [Interfaccia IActiveScriptSiteDebug Interface](../winscript/reference/iactivescriptsitedebug-interface.md) sull'oggetto che implementa l'interfaccia [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) \(necessarie per lo scripting attivo.  L'unico metodo non comune nei delegati dell'interfaccia `IActiveScriptSiteDebug` semplicemente di supporto.  
  
 Facoltativamente, l'host può implementare l'interfaccia [Interfaccia IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) se è necessario un controllo maggiore sul colore di sintassi, la creazione di contesto del documento e altre funzionalità estese.  
  
 La limitazione principale di supporto dello SmartHost è in grado di gestire solo i documenti del contenuto vengono modificati o riduce dopo che sono stati aggiunti sebbene i documenti possono essere espanso\).  Per molti SmartHost, tuttavia, la funzionalità che fornisce è esattamente gli elementi necessari.  
  
 Nelle sezioni seguenti vengono descritte più dettagliatamente ogni passaggio.  
  
## Creare un oggetto applicazione  
 Prima che il supporto di SmartHost possa essere utilizzato, è necessario creare un oggetto [Interfaccia IDebugApplication](../winscript/reference/idebugapplication-interface.md) per rappresentare l'applicazione nel debugger.  
  
#### Per creare un oggetto applicazione  
  
1.  Creare un'istanza dell'amministratore del processo di debug utilizzando `CoCreateInstance`.  
  
2.  Chiamare il metodo [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Impostare il nome sull'applicazione utilizzando [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Aggiungere l'oggetto l'elenco di applicazioni sottoponibili a debug utilizzando [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Il codice nelle strutture il processo, ma non include il controllo degli errori o altre tecniche di programmazione robusti.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## Utilizzando IDebugDocumentHelper  
  
#### Per utilizzare il supporto di \(minima sequenza di passaggi\)  
  
1.  Per ogni documento host, creare un file di supporto che utilizza [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Chiamare [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) sul supporto, fornendo il nome, gli attributi del documento, e così via.  
  
3.  Chiamare [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) con l'helper padre per il documento o ANNULLI se il documento è la radice\) per definire il percorso del documento nella struttura ad albero e per renderlo visibile al debugger.  
  
4.  Chiamare [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) o [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) per definire il testo del documento.  \(Possono essere chiamati più volte se il documento viene scaricato incrementale, come nel caso di un browser\).  
  
5.  Chiamare [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) per definire gli intervalli per ciascun blocco di script e i moduli di gestione di script collegati.  
  
## Implementare IActiveScriptSiteDebug  
 Per implementare [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), ottenere il supporto che corrisponde al sito specificato e quindi ottenere l'offset iniziale del documento per il contesto di origine specificato, come segue:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Successivamente, utilizzare l'helper per creare un contesto del nuovo documento per il carattere specificato sottoposto a offset:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Per implementare [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), chiamare semplicemente `IDebugApplication::GetRootNode` ereditato da [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)\).  
  
 Per implementare [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), restituire semplicemente `IDebugApplication` inizialmente creato mediante l'amministratore del processo di debug.  
  
## l'interfaccia facoltativa di IDebugDocumentHost  
 L'host può fornire un'implementazione [Interfaccia IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) utilizzando [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) per offrire controllo aggiuntivo sul supporto.  Di seguito sono riportate alcune delle operazioni principali l'interfaccia host consente di eseguire:  
  
-   Aggiungere il testo utilizzando [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) in modo che l'host non deve fornire i caratteri contemporaneamente.  Quando i caratteri effettivamente necessari, il supporto chiamerà [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md)host.  
  
-   Eseguire l'override della colorazione della sintassi predefinita fornita dal supporto.  L'helper chiama [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) per determinare la colorazione per un intervallo di caratteri, ritornante la relativa implementazione predefinita se il ritorno `E_NOTIMPL`host.  
  
-   Immettere uno sconosciuto di controllo per i contesti di documento creati dal supporto implementando [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md).  Consente all'host eseguire l'override della funzionalità dell'implementazione di contesto del documento predefinito.  
  
-   Immettere il percorso del file system per il documento.  Un utilizzo di debug di Interfacce questo consentire all'utente di modificare e salvare le modifiche apportate al documento.  [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) viene chiamato per notificare l'host dopo il salvataggio del documento.  
  
## Vedere anche  
 [Panoramica di debug script ActiveX](../winscript/active-script-debugging-overview.md)