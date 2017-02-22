---
title: "Procedura: registrare una libreria con il gestore oggetti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "librerie, la registrazione con gestione degli oggetti"
  - "Interfaccia IVsLibrary2, la registrazione della libreria con gestione degli oggetti"
  - "Interfaccia IVsSimpleLibrary2, la registrazione della libreria con gestione degli oggetti"
  - "Interfaccia IVsObjectManager2, la registrazione della libreria con gestione degli oggetti"
  - "librerie, strumenti di esplorazione di simbolo"
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: registrare una libreria con il gestore oggetti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

gli strumenti di Simbolo\-esplorazione, come **Visualizzazione classi**, **Visualizzatore oggetti**, **Visualizzatore chiamate** e **Risultati del simbolo di ricerca**, consentono di visualizzare i simboli nel progetto o in componenti esterni.  I simboli inclusi gli spazi dei nomi, classi, interfacce, i metodi e gli altri elementi del linguaggio.  Le librerie gestione di tali simboli e li espongono gestione dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che popola gli strumenti con i dati.  
  
 L'amministratore dell'oggetto tiene traccia di tutte le librerie disponibili.  Ogni raccolta necessario registrare con l'amministratore dell'oggetto prima di fornire i simboli degli strumenti di simbolo\-esplorazione.  
  
 In genere, si registra una raccolta quando un package VS viene caricato.  Tuttavia, possono essere effettuate in un altro momento in base alle necessità.  Annullare la registrazione della raccolta quando il package VS è stata chiusa.  
  
 per registrare una raccolta, utilizzare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> .  Nel caso di codice gestito, utilizzare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  
  
 Per annullare la registrazione di una raccolta, utilizzare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .  
  
 Per ottenere un riferimento all'amministratore dell'oggetto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passa il servizio ID di <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> al metodo di `GetService` .  
  
## Registrando e annullamento della registrazione di una raccolta con l'amministratore dell'oggetto  
  
#### Per registrare una libreria con l'amministratore dell'oggetto  
  
1.  creare una raccolta.  
  
    ```vb#  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```c#  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Ottenere un riferimento a un oggetto del tipo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> e chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  
  
    ```vb#  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```c#  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### Per annullare la registrazione di una raccolta con l'amministratore dell'oggetto  
  
1.  Ottenere un riferimento a un oggetto del tipo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> e chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .  
  
    ```vb#  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```c#  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## Vedere anche  
 [Estensibilità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Procedura: esporre elenchi dei simboli forniti dalla libreria di gestione degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)