---
title: "Funzione SccAddFromScc | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFromScc"
helpviewer_keywords: 
  - "Funzione SccAddFromScc"
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccAddFromScc
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di individuare i file già presenti nel sistema di controllo di origine e successivamente rendere tali file del progetto corrente. Ad esempio, questa funzione può ottenere un file di intestazione comune nel progetto corrente senza copiare il file. La matrice restituita di file, `lplpFileNames`, contiene l'elenco dei file che si desidera aggiungere al progetto IDE.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpnFiles  
 \[in, out\] Un buffer per il numero di file che vengono aggiunti in. \(Si tratta di `NULL` Se la memoria a cui puntava `lplpFileNames` deve essere rilasciato. Vedere la sezione Osservazioni per informazioni dettagliate\).  
  
 lplpFileNames  
 \[in, out\] Matrice di puntatori a tutti i nomi di file senza i percorsi di directory. Questa matrice viene allocata e liberata mediante il plug\-in del controllo del codice sorgente. Se `lpnFiles` \= 1 e `lplpFileNames` non `NULL`, il nome della matrice a cui puntava `lplpFileNames` contiene la cartella di destinazione.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|I file sono stati correttamente Trova e aggiunto al progetto.|  
|SCC\_I\_OPERATIONCANCELED|Operazione annullata senza alcun effetto.|  
|SCC\_I\_RELOADFILE|Un progetto o il file deve essere ricaricata.|  
  
## Note  
 Questa funzione viene chiamata l'IDE. Se il controllo del codice sorgente del plug\-in supporta la specifica di una cartella di destinazione locale, l'IDE passa `lpnFiles` \= 1 e passa il nome della cartella locale in `lplpFileNames`.  
  
 Quando la chiamata al `SccAddFromScc` funzione viene restituito, il plug\-in è assegnato valori a `lpnFiles` e `lplpFileNames`, allocare la memoria per la matrice di nome file in base alle esigenze \(si noti che questa allocazione sostituisce il puntatore in `lplpFileNames`\). Il plug\-in del controllo del codice sorgente è responsabile dell'immissione di tutti i file nella directory dell'utente o nella cartella designazione specificato. L'IDE aggiunge quindi i file per il progetto dell'IDE.  
  
 Infine, l'IDE chiama questa funzione una seconda volta, passando `NULL` per `lpnFiles`. Ciò viene interpretato come un segnale speciale per il plug\-in per rilasciare la memoria allocata per la matrice di nomi di file nel controllo del codice sorgente `lplpFileNames``.`  
  
 `lplpFileNames` è un `char ***` puntatore. Il plug\-in del controllo del codice sorgente posiziona un puntatore a una matrice di puntatori ai nomi di file, quindi passare l'elenco nella modalità standard per questa API.  
  
> [!NOTE]
>  Versioni iniziali dell'API VSSCI non ha fornito un modo per indicare il progetto di destinazione per i file aggiunti. Di conseguenza, la semantica di `lplpFIleNames` parametro sono state migliorate per renderlo un parametro in\/out piuttosto che un parametro di output. Se solo un singolo file viene specificato, ovvero il valore a cui puntava `lpnFiles` \= 1, quindi il primo elemento del `lplpFileNames` contiene la cartella di destinazione. Utilizzare questa nuova semantica, le chiamate IDE il `SccSetOption` è utilizzabile con il `nOption`parametro impostato su `SCC_OPT_SHARESUBPROJ`. Se un plug\-in del controllo del codice sorgente non supporta la semantica, restituisce `SCC_E_OPTNOTSUPPORTED`. Eseguire quindi disabilita l'utilizzo del **Aggiungi dal controllo del codice sorgente** funzionalità. Se un plug\-in supporta il **Aggiungi dal controllo del codice sorgente** funzionalità \(`SCC_CAP_ADDFROMSCC`\), quindi deve supportare la semantica di nuovo e restituire `SCC_I_SHARESUBPROJOK`.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)