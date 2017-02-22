---
title: "Recupero di una porta | Microsoft Docs"
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
  - "porte, recupero"
  - "debug [Debugging SDK], porte"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Recupero di una porta
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una porta rappresenta una connessione a un computer in cui i processi in esecuzione.  Il computer può essere il computer locale o un computer remoto \(in grado di eseguire anche in un sistema operativo basa non Finestra; vedere [Porte](../../extensibility/debugger/ports.md) per ulteriori informazioni.  
  
 Una porta è rappresentata [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) dall'interfaccia.  Viene utilizzata per ottenere informazioni sui processi in esecuzione sul computer che la porta è connessa a.  
  
 Un motore di debug è necessario accedere a una porta per registrare i nodi di programma con la porta e soddisfare le richieste di informazioni del processo.  Ad esempio, se il motore di debug implementa [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) l'interfaccia, l'implementazione del [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metodo potrebbe chiedere alla porta le informazioni del processo necessari di essere restituito.  
  
 Visual Studio fornisce la porta necessaria al motore di debug e ottiene questa porta da un fornitore di porte.  Se un programma è associato \(dal debugger o a causa di un'eccezione è stato generato, che genera la finestra di dialogo JIT \(just\-in\-time\) \[\]\), l'utente viene fornito la scelta di trasporto \(un altro nome per un fornitore di porte\) da utilizzare.  In caso contrario, se l'utente vara il programma nel debugger, il sistema del progetto specifica il fornitore di porte da utilizzare.  In qualsiasi evento, Visual Studio crea un'istanza del fornitore di porte, rappresentato [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) da un'interfaccia e richiede una nuova porta chiamando [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) un'interfaccia.  Questa porta viene quindi passata al motore di debug in un form o in.  
  
## Esempio  
 In questo frammento di codice seguente viene illustrato come utilizzare la porta forniti [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per registrare un nodo di programma in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md).  I parametri non direttamente correlati a questo concetto sono stati omessi per maggiore chiarezza.  
  
> [!NOTE]
>  In questo esempio viene utilizzata la porta per avviare e riprendere il processo e presuppone che [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) l'interfaccia viene implementata la porta.  Si tratta in nessun caso l'unica modalità per eseguire queste attività ed è possibile che la porta può non essere implicitamente da disporre del [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) programma di fornita da.  
  
```cpp#  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## Vedere anche  
 [Il programma di registrazione](../../extensibility/debugger/registering-the-program.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)   
 [Porte](../../extensibility/debugger/ports.md)