---
title: Glossario di plug-in controllo dell&quot;origine | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 251e104336d19e9f88926e5ca75a85330039fbe8
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-plug-in-glossary"></a>Glossario di plug-in del controllo di origine
I seguenti termini utili e le definizioni sono relativi alla documentazione SDK di plug-in controllo di origine.  
  
## <a name="definitions"></a>Definizioni  
 Archiviazione  
 Quando un utente apporta modifiche a una copia di lavoro, un utente deve inviare le modifiche dalla copia di lavoro nel repository di controllo origine dati centrale. Verrà creata una nuova revisione del file che è disponibile ad altri utenti. Questo processo è denominato un'archiviazione.  
  
 Estrai  
 Azione di richiesta di una copia di lavoro dal repository, che informa che il repository dell'intenzione di modificarlo. Una copia di lavoro riflette lo stato del progetto al momento che è estratto.  
  
 Client  
 Un programma che utilizza il sistema di controllo del codice sorgente. Ai fini di questa documentazione è IDE di Visual Studio.  
  
 Commento  
 Un messaggio che descrive le modifiche che è possibile collegare a una revisione quando viene eseguita un'operazione di controllo di origine.  
  
 Conflitto  
 Una situazione in cui due utenti tentano di archiviare le modifiche alla stessa area dello stesso file. In genere, è necessario eseguire un'operazione di unione.  
  
 Directory  
 Una cartella locale sul lato client viene considerata come una directory. Questa è la copia in cui viene effettivamente modificato. Possono esserci più copie di lavoro di un determinato progetto. in genere, ogni sviluppatore ha la propria copia.  
  
 Leggi  
 Un'operazione get porta copia lavoro dell'utente aggiornata con la copia di archivio. A differenza di estrazione, viene eseguito un'operazione get quando l'utente richiede la copia più recente semplicemente ma intende non apportare alcuna modifica.  
  
 Cronologia  
 Generalmente si tratta di un riepilogo di tutte le estrazioni, archiviazioni, gli aggiornamenti, tag e versioni eseguite nel repository del controllo del codice sorgente.  
  
 IDE  
 In genere fa riferimento per l'ambiente di sviluppo integrato di Visual Studio. Tuttavia, potrebbe inoltre fare riferimento ad altri ambienti di client che riconoscono l'API plug-in controllo di origine.  
  
 Merge  
 Il processo durante l'origine di due o più file di codice vengono combinati per formare un nuovo file che include tutte le funzionalità del file precedente. Questo concetto è fondamentale nel controllo della versione in cui due o più sviluppatori lavorano file contemporaneamente.  
  
 Progetto  
 Una cartella del codice sorgente è spesso definita come un progetto. Ciò non ha alcuna relazione con i progetti o soluzioni in Visual Studio.  
  
 Plug-in  
 Una DLL che fornisce controllo del codice sorgente implementando l'API plug-in controllo di origine.  
  
 Repository  
 La copia master in cui un controllo origine sistema archivia la cronologia delle revisioni completo del progetto. Ogni progetto include esattamente un repository.  
  
 Revision  
 Una modifica commit nella cronologia di un file o set di file. Una revisione è uno snapshot in un progetto in continua evoluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)
