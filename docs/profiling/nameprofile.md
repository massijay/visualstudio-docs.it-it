---
title: "NameProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzione `NameProfile` assegna una stringa al processo o al thread specificato.  
  
 L'API NameProfile è disponibile solo per la profilatura tramite strumentazione.  L'API NameProfile non è supportata per la profilatura tramite campionamento.  
  
## Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### Parametri  
 `pszName`  
  
 Nome dell'elemento di profilo.  Un nome non è valido \(NameProfileA restituisce NAME\_ERROR\_INVALID\_NAME\) quando:  
  
-   Il puntatore passato a NameProfileA è un valore NULL  
  
-   I dati stringa di pszName iniziano con un numero  
  
-   I dati stringa di pszName contengono uno spazio  
  
-   La stringa dati di pszName contiene uno dei seguenti caratteri: ,;.\`~\!@\#$%^&\*\(\)\=\[\]{}&#124;\\?\/\<\>  
  
 `Level`  
  
 Indica il livello di analisi al quale può essere applicata la raccolta dei dati sulle prestazioni.  I valori **PROFILE\_CONTROL\_LEVEL** seguenti possono essere utilizzati per indicare uno dei tre livelli a cui può essere applicata la raccolta dei dati sulle prestazioni:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|PROFILE\_GLOBALLEVEL|L'impostazione del livello globale influisce su tutti i processi e i thread della sessione durante l'esecuzione del profilo.|  
|PROFILE\_PROCESSLEVEL|L'impostazione del livello di processo influisce su tutti i thread appartenenti al processo specificato.|  
|PROFILE\_THREADLEVEL|L'impostazione del livello di profilo dei thread influisce sul thread specificato.|  
  
 `dwId`  
  
 Identificatore del livello di profilo.  Utilizzare l'identificatore del processo o del thread generato dal sistema.  
  
## Valore proprietà\/Valore restituito  
 La funzione indica esito positivo o negativo utilizzando l'enumerazione **PROFILE\_COMMAND\_STATUS**.  Il valore restituito può essere uno dei seguenti:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|NAME\_ERROR\_ID\_NOEXIST|L'elemento di profilo specificato non esiste.|  
|NAME\_ERROR\_INVALID\_NAME|Nome non valido.|  
|NAME\_ERROR\_LEVEL\_NOEXIST|Il livello di profilo specificato non esiste.|  
|NAME\_ERROR\_NO\_SUPPORT|L'operazione specificata non è supportata.|  
|NAME\_ERROR\_OUTOFMEMORY|Memoria non disponibile per registrare l'evento.|  
|NAME\_ERROR\_REDEFINITION|All'elemento di profilo è stato già assegnato un nome.  Il nome presente in questa funzione verrà ignorato.|  
|NAME\_ERROR\_TEXTTRUNCATED|Il testo del nome è stato troncato perché ha superato 32 caratteri, incluso il carattere null.|  
|NAME\_OK|Il nome è stato registrato correttamente.|  
  
## Note  
 A ogni processo o thread è possibile assegnare un solo nome.  Dopo aver assegnato un nome a un elemento di profilo, le chiamate successive alla funzione NameProfile relative all'elemento in questione verranno ignorate.  
  
 Se viene assegnato lo stesso nome a thread o processi diversi, nel report saranno inclusi i dati di tutti gli elementi con quel nome presenti nel livello specifico.  
  
 Se si specifica un processo o un thread diverso da quello attuale, è necessario verificare che sia stato inizializzato e avviato prima dell'assegnazione del nome.  In caso contrario, l'esecuzione del metodo NameProfile avrà esito negativo.  
  
> [!IMPORTANT]
>  Le funzioni API CreateProcess\(\) e CreateThread\(\) possono essere restituite prima dell'inizializzazione del thread o del processo.  
  
## Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informazioni sulla funzione  
  
|||  
|-|-|  
|**Intestazione**|Includere VSPerf.h|  
|**Libreria**|Utilizzare VSPerf.lib|  
|**Unicode**|Implementato come `NameProfileW` \(Unicode\) e `NameProfileA` \(ANSI\).|  
  
## Esempio  
 Nel codice riportato di seguito è illustrata la chiamata della funzione NameProfile.  Nell'esempio si presuppone l'utilizzo di macro di stringa Win32 e delle impostazioni del compilatore per ANSI per stabilire se il codice chiama la versione ANSI della funzione.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio \(native\)](../profiling/visual-studio-profiler-api-reference-native.md)