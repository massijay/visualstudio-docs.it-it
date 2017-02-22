---
title: "Procedura: eliminare le notifiche di modifica File | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - esclusione di notifica di modifica file"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: eliminare le notifiche di modifica File
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando il file fisico che rappresenta il buffer di testo è stato modificato, viene visualizzata una finestra di dialogo con il messaggio **Si desidera salvare le modifiche apportate ai seguenti elementi?** Questo processo è noto come notifica delle modifiche ai file.  Se molte modifiche utilizzeranno essere al file, tuttavia, questa finestra di dialogo che vengono visualizzate in modo continuo può diventare rapidamente seccante.  
  
 A livello di codice è possibile eliminare questa finestra di dialogo utilizzando la procedura riportata di seguito.  In questo modo, è possibile ricaricare un file immediatamente senza dover richiedere all'utente di salvare ogni volta che viene modificato.  
  
### Per eliminare notifica delle modifiche ai file  
  
1.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> per determinare quale oggetto del buffer di testo è associato al file aperto.  
  
2.  Impostare l'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> presente in memoria per ignorare le modifiche apportate a un file di monitoraggio ottenere l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> dall'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(dati di documento\) e quindi implementare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> con il parametro di `fIgnore` impostato su `true`.  
  
3.  Chiamare metodi di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per aggiornare l'oggetto in memoria di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> con le modifiche apportate a un file \(ad esempio quando un campo viene aggiunto al componente\).  
  
4.  Aggiornare il file su disco con le modifiche senza considerare le modifiche in sospeso l'utente potrebbe essere in corso.  
  
     In questo modo, quando si indica all'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> al monitoraggio di l per le notifiche delle modifiche ai file, il buffer di testo in memoria riflette le modifiche che è stato generato e tutte le altre modifiche in sospeso.  Il file su disco riflette l'ultimo codice generato da a e da qualsiasi modifica precedentemente salvato dall'utente nel codice utente\-modificato.  
  
5.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> per passare l'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> al monitoraggio di l per le notifiche delle modifiche ai file impostando il parametro di `fIgnore` a `false`.  
  
6.  Se si intende apportare alcune modifiche al file, come nel caso di controllo del codice \(SCC\) sorgente, quindi di è necessario che il servizio per le modifiche ai file globale di sospendere temporaneamente le notifiche delle modifiche ai file.  
  
     Ad esempio, se riscrivete il file e quindi si modifica il timestamp, è necessario sospendere le notifiche delle modifiche ai file, come le operazioni di timestample e di riscrivere ogni numero come evento per le modifiche ai file separato.  Per abilitare la notifica delle modifiche ai file globale è necessario chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> .  
  
## Esempio  
 L'esempio seguente viene illustrato come eliminare la notifica delle modifiche ai file.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## Programmazione efficiente  
 Se il caso include le modifiche più al file, come nel caso di SCC, quindi di è importante riattivare le notifiche delle modifiche ai file globali prima dell'avviso i dati del monitoraggio di l per il file viene modificato.