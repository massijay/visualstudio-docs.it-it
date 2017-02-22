---
title: "ResumeProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ResumeProfile"
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ResumeProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo `ResumeProfile` decrementa il contatore Suspend\/Resume per il livello di analisi specificato.  
  
## Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### Parametri  
 `Level`  
  
 Indica il livello di analisi al quale può essere applicata la raccolta dei dati sulle prestazioni.  Gli enumeratori **PROFILE\_CONTROL\_LEVEL** seguenti possono essere utilizzati per indicare uno dei tre livelli a cui può essere applicata la raccolta dei dati sulle prestazioni:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|PROFILE\_GLOBALLEVEL|L'impostazione del livello globale influisce su tutti i processi e i thread della sessione durante l'esecuzione del profilo.|  
|PROFILE\_PROCESSLEVEL|L'impostazione del livello di processo influisce su tutti i thread appartenenti al processo specificato.|  
|PROFILE\_THREADLEVEL|L'impostazione del livello di profilo dei thread influisce sul thread specificato.|  
  
 `dwId`  
  
 Identificatore del processo o del thread generato dal sistema.  
  
## Valore proprietà\/Valore restituito  
 La funzione indica esito positivo o negativo utilizzando l'enumerazione **PROFILE\_COMMAND\_STATUS**.  Il valore restituito può essere uno dei seguenti:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|PROFILE\_ERROR\_ID\_NOEXIST|L'ID elemento di profilo non esiste.|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|Il livello di profilo specificato non esiste.|  
|PROFILE\_ERROR\_MODE\_NEVER|La modalità di profilo è stata impostata su NEVER quando è stata chiamata la funzione.|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|Non è ancora stata eseguita l'implementazione della chiamata alla funzione di profilo, del livello di profilo o della combinazione di entrambi.|  
|PROFILE\_OK|La chiamata è stata eseguita correttamente.|  
  
## Note  
 Il valore iniziale del contatore Suspend\/Resume è 0.  Ogni chiamata a SuspendProfile e a ResumeProfile rispettivamente aggiunge e sottrae 1 al conteggio Suspend\/Resume.  
  
 Quando il conteggio Suspend\/Resume è maggiore di 0, lo stato Suspend\/Resume del livello è OFF.  Quando il conteggio è minore o uguale a 0, lo stato Suspend\/Resume è ON.  
  
 Quando gli stati Start\/Stop e Suspend\/Resume sono entrambi impostati su ON, lo stato di profilo del livello è ON.  Per il profilo di un thread è necessario che gli stati a livello globale, di processo e di thread siano tutti impostati su ON.  
  
## Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informazioni sulla funzione  
 Intestazione: dichiarata in VSPerf.h  
  
 Libreria di importazione: VSPerf.lib  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrata la funzione ResumeProfile.  L'esempio presuppone che sia stata effettuata una chiamata al metodo SuspendProfile per lo stesso thread o processo identificato da [PROFILE\_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio \(native\)](../profiling/visual-studio-profiler-api-reference-native.md)