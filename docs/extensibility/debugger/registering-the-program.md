---
title: "Il programma di registrazione | Microsoft Docs"
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
  - "programmi, la registrazione"
  - "debug [Debugging SDK], programma di registrazione"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Il programma di registrazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dopo che il motore di debug ha acquisito una porta, rappresentata [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) da un'interfaccia, il passaggio successivo dell'abilitazione del programma da sottoporre a debug è necessario registrarlo con la porta.  Dopo aver registrato, il programma è disponibile per il debug da uno dei seguenti modi:  
  
-   Il processo di associazione, che consente al debugger del controllo completo di debug di miglioramento di un'applicazione in esecuzione.  
  
-   Debug \(JIT\) JIT, che consente il debug di una volta \-\- fatto di un programma che viene eseguito indipendentemente dal debugger.  Quando l'architettura di runtime rileva un errore, il debugger riceve una notifica prima del sistema operativo o dell'ambiente di runtime elimina la memoria e le risorse del programma di errore.  
  
## registrare routine  
  
#### Per registrare il programma  
  
1.  Chiamare [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) il metodo implementato dalla porta.  
  
     `IDebugPortNotify2::AddProgramNode` richiede un puntatore [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) a un'interfaccia.  
  
     In genere, quando il sistema operativo o dell'ambiente di runtime carica un programma, crea il nodo del programma.  Se il motore di \(DE\) debug viene richiesto per il caricamento del programma quindi il DE viene creato e registrato il nodo del programma.  
  
     Nell'esempio seguente viene illustrato il motore di debug che avvia il programma e averlo registrata con una porta.  
  
    > [!NOTE]
    >  Ciò non rappresentano l'unico modo per avviare e riattivare un processo; ciò è principalmente un esempio di registrazione di un programma con una porta.  
  
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
 [Recupero di una porta](../../extensibility/debugger/getting-a-port.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)