---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzione `CommentMarkProfile` inserisce un marcatore numerico e una stringa di testo nel file vsp.  Per l'inserimento dell'indicatore e del commento, è necessario che la profilatura per il thread contenente la funzione `CommentMarkProfile` sia impostata su ON.  
  
## Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### Parametri  
 `lMarker`  
  
 Marcatore numerico da inserire  che deve essere maggiore o uguale a 0 \(zero\).  
  
 `szComment`  
  
 Puntatore alla stringa di testo da inserire.  La stringa deve contenere meno di 256 caratteri, incluso il carattere di terminazione NULL.  
  
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
 La stato di profilatura per il thread contenente la funzione relativa al contrassegno del profilo deve essere impostato su ON quando vengono inseriti indicatori e commenti con il comando Mark di VSInstr o con le funzioni \(CommentMarkAtProfile, CommentMarkProfile o MarkProfile\).  
  
 Gli indicatori di profilo hanno un ambito globale.  Un indicatore di profilo inserito in un thread può, ad esempio, essere utilizzato per contrassegnare l'inizio o la fine di un segmento di dati in qualsiasi thread del file vsp.  
  
> [!IMPORTANT]
>  Il metodo CommentMarkProfile può essere utilizzato solo con la strumentazione.  
  
## Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informazioni sulla funzione  
  
|||  
|-|-|  
|**Intestazione**|Includere VSPerf.h|  
|**Libreria**|Utilizzare VSPerf.lib|  
|**Unicode**|Implementato come `CommentMarkProfileW` \(Unicode\) e `CommentMarkProfileA` \(ANSI\).|  
  
## Esempio  
 Nel codice riportato di seguito è illustrata la chiamata della funzione CommentMarkProfile.  Nell'esempio si presuppone l'utilizzo di macro di stringa Win32 e delle impostazioni del compilatore Unicode per stabilire se il codice chiama la funzione [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)].  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio \(native\)](../profiling/visual-studio-profiler-api-reference-native.md)