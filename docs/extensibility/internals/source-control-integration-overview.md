---
title: Panoramica dell&quot;integrazione di controllo di origine | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 16
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
ms.openlocfilehash: d3facc06885ef927448eb506ff2f4aa5c04ce85f
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-integration-overview"></a>Panoramica sull'integrazione di controllo di origine
In questa sezione Confronta i due modi per integrare nel controllo del codice sorgente Visual Studio; un controllo del codice sorgente del plug-in e un package VS che offre una soluzione di controllo di origine e vengono evidenziate le nuove funzionalità di controllo di origine. Visual Studio consente il passaggio manuale tra controllo del codice sorgente di VSPackage e plug-in del controllo codice sorgente, nonché commutazione automatica basata sulla soluzione.  
  
## <a name="source-control-integration"></a>Integrazione del controllo codice sorgente  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta due tipi di opzioni integrazione del controllo codice sorgente. Tutte le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è comunque possibile integrare un plug-in basato sull'origine controllo plug-in di API (in precedenza definita anche come API MSSCCI), che fornisce la funzionalità di controllo di base origine mentre si utilizza l'interfaccia utente di controllo dall'origine di Visual Studio (UI). Un controllo del codice sorgente VSPackage, d'altra parte, offre una nuova, integrazione profonda [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] percorso adatto per l'integrazione del controllo codice sorgente che richiede un elevato livello di complessità e l'autonomia del modello di controllo di origine.  
  
 ![Cenni preliminari sul controllo di origine](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente  
 Tutte le versioni di Visual Studio supportano l'API di plug-in controllo di origine specifica versione 1.2 come un percorso di integrazione. Un responsabile di plug-in del controllo origine scrive una DLL che implementa le funzioni API plug-in controllo di origine per l'integrazione del controllo codice sorgente e la registrazione, come descritto in [la creazione di un plug-in controllo origine](../../extensibility/internals/creating-a-source-control-plug-in.md). In questo approccio, si utilizza l'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per le finestre di dialogo, ad esempio archiviazione, estrazione, pagine delle proprietà Strumenti/opzioni, barre degli strumenti e icone di controllo di origine. Una stretta osservanza all'API di plug-in controllo di origine garantisce un facile integrazione in Visual Studio e un'esperienza senza problemi per l'utente. Ciò significa che il plug-in del controllo del codice sorgente deve implementare la maggior parte delle funzioni e i callback dettagliati nell'API.  
  
 Per implementare un controllo del codice sorgente del plug-in tramite l'API plug-in controllo di origine, seguire questi passaggi:  
  
1.  Creare una DLL che implementa le funzioni specificate nel [Plug-in controllo del codice sorgente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrare la DLL, creando le voci del Registro di sistema (descritto in [procedura: installare un plug-in controllo origine](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Creare un supporto di interfaccia utente e la visualizzazione quando viene richiesto il pacchetto di scheda di controllo di origine (il componente di Visual Studio che gestisce la funzionalità di controllo sorgente tramite plug-in del controllo codice sorgente)  
  
 In risposta a un comando di controllo di origine, l'IDE di Visual Studio presenta un'interfaccia utente standard per le operazioni di base e quindi passa le informazioni per il controllo del codice sorgente del plug-in tramite le funzioni definite nell'API di plug-in controllo di origine. Per le opzioni avanzate, il plug-in del controllo del codice sorgente può essere chiamato su per presentare la propria interfaccia utente, ad esempio, la ricerca di un progetto di controllo del codice sorgente. Ciò significa che potrebbe essere visualizzato quando l'utente con due probabilmente diversi stili dell'interfaccia utente di Gestione controllo del codice sorgente: l'interfaccia utente che visualizza di Visual Studio e l'interfaccia utente che visualizza il plug-in del controllo del codice sorgente. Questo è particolarmente evidente con operazioni di controllo avanzate.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Svantaggi di implementazione di un plug-in del controllo del codice sorgente  
  
-   Per le funzionalità avanzate, l'utente può visualizzare due diversi tipi di interfacce, causando possibili confusioni.  
  
-   Il plug-in del controllo del codice sorgente è limitato al modello di controllo di origine in cui è inclusa l'API plug-in controllo di origine.  
  
-   L'API plug-in controllo di origine potrebbero essere troppo restrittiva per alcuni scenari di controllo di origine.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantaggi dell'implementazione di un plug-in del controllo del codice sorgente  
  
-   Visual Studio fornisce l'interfaccia utente per tutte le operazioni di controllo di base in modo che il plug-in del controllo del codice sorgente non è necessario implementare potenzialmente complesso dell'interfaccia utente.  
  
-   A causa dell'API strict, il plug-in del controllo del codice sorgente può interagire facilmente con i programmi di controllo di origine esterna per fornire funzionalità più ampia. Visual Studio non è rilevante troppo molto come il controllo del codice sorgente viene eseguita, solo che questa operazione viene eseguita in base alle API di plug-in controllo di origine.  
  
-   È più semplice implementare un controllo del codice sorgente del plug-in di un controllo del codice sorgente VSPackage.  
  
## <a name="source-control-vspackage"></a>Origine controllo VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Consente l'integrazione completa in Visual Studio con controllo completo del controllo del codice sorgente e la sostituzione completa dell'interfaccia utente del controllo di origine fornito da Visual Studio. Un controllo del codice sorgente VSPackage è registrato con Visual Studio e fornisce funzionalità di controllo di origine. Sebbene controllo del codice sorgente diversi package VS può essere registrato con Visual Studio, solo uno di essi può essere attivo in qualsiasi momento. Un controllo del codice sorgente VSPackage abbia il pieno controllo sul controllo del codice sorgente e l'aspetto in Visual Studio mentre è attiva. Tutti gli altri controllo del codice sorgente package VS che possono essere registrati nel sistema sono inattivo e non sarà visualizzato qualsiasi interfaccia utente affatto.  
  
 Implementazione di un controllo del codice sorgente VSPackage richiede una strategia di "tutto o niente". Il creatore di un controllo del codice sorgente VSPackage necessario investire una quantità significativa di lavoro richiesto nell'implementazione di un numero di interfacce di controllo di origine e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intero di controllo del codice sorgente. Vedere [la creazione di un pacchetto di controllo di origine](../../extensibility/internals/creating-a-source-control-vspackage.md) per ulteriori dettagli.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Svantaggi di implementazione di un pacchetto di controllo di origine  
  
-   VSPackage deve implementare un numero di interfacce complesse per integrare correttamente con Visual Studio.  
  
-   VSPackage deve fornire l'interfaccia utente necessaria per controllo del codice sorgente; Visual Studio non verrà fornita alcuna assistenza in questa area.  
  
-   Un controllo del codice sorgente VSPackage è strettamente correlato a Visual Studio e non può funzionare con programmi autonomi, in modo da funzionalità non può essere facilmente condivisa con una versione del programma di controllo di origine esterna.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantaggi dell'implementazione di un pacchetto di controllo di origine  
  
-   Poiché il VSPackage dispone di funzionalità e il controllo completo tramite il controllo del codice sorgente dell'interfaccia utente, viene visualizzata con un'interfaccia intuitiva per controllo del codice sorgente.  
  
-   Il pacchetto Visual Studio non è confinato a un modello di controllo di origine specifico.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)   
 [Creazione di plug-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creazione di un pacchetto di controllo di origine](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Novità di controllo del codice sorgente](../../extensibility/internals/what-s-new-in-source-control.md)
