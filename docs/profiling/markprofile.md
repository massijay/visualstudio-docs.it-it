---
title: "MarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MarkProfile"
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# MarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo `MarkProfile` inserisce un indicatore del profilo nel file vsp.  Per l'inserimento dell'indicatore, è necessario che la profilatura del thread contenente la funzione `MarkProfile` sia impostata su ON.  
  
## Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### Parametri  
 `lMarker`  
  
 Marcatore da inserire  che deve essere maggiore o uguale a 0 \(zero\).  
  
## Valore proprietà\/Valore restituito  
 La funzione indica esito positivo o negativo utilizzando l'enumerazione **PROFILE\_COMMAND\_STATUS**.  Il valore restituito può essere uno dei seguenti:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|MARK\_ERROR\_MARKER\_RESERVED|Il parametro è minore di o uguale a 0.  I valori sono riservati.  L'indicatore e il commento non vengono registrati.|  
|MARK\_ERROR\_MODE\_NEVER|La modalità di profilo è stata impostata su NEVER quando è stata chiamata la funzione.  L'indicatore e il commento non vengono registrati.|  
|MARK\_ERROR\_MODE\_OFF|La modalità di profilatura era impostata su OFF quando è stata chiamata la funzione.  L'indicatore e il commento non vengono registrati.|  
|MARK\_ERROR\_NO\_SUPPORT|In questo contesto non sono supportati indicatori.  L'indicatore e il commento non vengono registrati.|  
|MARK\_ERROR\_OUTOFMEMORY|Memoria non disponibile per registrare l'evento.  L'indicatore e il commento non vengono registrati.|  
|MARK\_TEXTTOOLONG|La stringa supera il limite massimo di 256 caratteri.  La stringa di commento viene troncata e l'indicatore e il commento vengono registrati.|  
|MARK\_OK|MARK\_OK viene restituito per indicare esito positivo.|  
  
## Note  
 Il valore dell'indicatore viene inserito nel file vsp a ogni esecuzione del codice se è in corso il profilo del thread che contiene la funzione MarkProfile.  Tale funzione può essere chiamata più volte.  
  
 Gli indicatori di profilo hanno un ambito globale.  Un indicatore di profilo inserito in un thread può, ad esempio, essere utilizzato per contrassegnare l'inizio o la fine di un segmento di dati in qualsiasi thread del file vsp.  
  
 La stato di profilatura per il thread contenente la funzione relativa al contrassegno di profilo deve essere impostato su ON quando vengono inseriti indicatori e commenti con il comando Mark o con le funzioni API \(CommentMarkAtProfile, CommentMarkProfile o MarkProfile\).  
  
> [!IMPORTANT]
>  I metodi MarkProfile vanno utilizzati esclusivamente con la profilatura mediante strumentazione.  
  
## Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informazioni sulla funzione  
 Intestazione: dichiarata in VSPerf.h  
  
 Libreria di importazione: VSPerf.lib  
  
## Esempio  
 Nel codice seguente è illustrata la funzione MarkProfile.  
  
```  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio \(native\)](../profiling/visual-studio-profiler-api-reference-native.md)