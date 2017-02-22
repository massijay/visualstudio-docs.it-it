---
title: "CommentMarkAtProfile | Microsoft Docs"
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
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo `CommentMarkAtProfile` inserisce un valore di timestamp, un indicatore numerico e una stringa di commento nel file vsp.  Il valore di timestamp può essere utilizzato per sincronizzare gli eventi esterni.  Per l'inserimento dell'indicatore e del commento, è necessario che la profilatura per il thread contenente la funzione CommentMarkAtProfile sia impostata su ON.  
  
## Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### Parametri  
 `dnTimestamp`  
  
 Integer a 64 bit che rappresenta un valore di timestamp.  
  
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
 La stato di profilatura per il thread contenente la funzione relativa al contrassegno di profilo deve essere impostato su ON quando vengono inseriti indicatori e commenti con il comando Mark o con le funzioni API \(CommentMarkAtProfile, CommentMarkProfile o MarkProfile\).  Gli indicatori di profilo hanno un ambito globale.  Un indicatore di profilo inserito in un thread può, ad esempio, essere utilizzato per contrassegnare l'inizio o la fine di un segmento di dati in qualsiasi thread del file vsp.  
  
> [!IMPORTANT]
>  I metodi CommentMarkAtProfile vanno utilizzati esclusivamente con la strumentazione.  
  
## Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informazioni sulla funzione  
  
|||  
|-|-|  
|**Intestazione**|Includere VSPerf.h|  
|**Libreria**|Utilizzare VSPerf.lib|  
|**Unicode**|Implementato come CommentMarkAtProfileW \(Unicode\) e CommentMarkAtProfileA \(ANSI\).|  
  
## Esempio  
 Nel codice riportato di seguito è illustrato l'utilizzo della chiamata della funzione generica CommentMarkAtProfile.  Nell'esempio si presuppone l'utilizzo di macro di stringa Win32 e delle impostazioni del compilatore per ANSI per stabilire se il codice chiama la versione ANSI della funzione.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio \(native\)](../profiling/visual-studio-profiler-api-reference-native.md)