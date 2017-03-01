---
title: Procedure guidate | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 13
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: af0466ea3c11b75090e45cb9b408ed0723cd8a6f
ms.lasthandoff: 02/22/2017

---
# <a name="wizards"></a>Creazioni guidate
Dopo aver creato una procedura guidata, in genere da aggiungere per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo (IDE) integrato in modo che altri utenti possono utilizzarlo. L'aggiunta guidata viene quindi visualizzata nel **Aggiungi nuovo progetto** o **Aggiungi nuovo elemento** finestre di dialogo. Per visualizzare il **Aggiungi nuovo progetto** o **Aggiungi nuovo elemento** finestra di dialogo finestre, fare doppio clic su una soluzione aperta in **Esplora soluzioni**, scegliere **Aggiungi**, quindi fare clic su **nuovo progetto** o **nuovo elemento**.  
  
 Procedure guidate possono essere implementate in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per consentire agli utenti selezionare da una visualizzazione struttura ad albero di valori disponibili all'apertura di **Aggiungi nuovo progetto** la finestra di dialogo o **Aggiungi nuovo elemento** nella finestra di dialogo oppure quando sono su un elemento **Esplora soluzioni**.  
  
 Nella procedura guidata, è possibile fornire la possibilità di localizzare il nome di un progetto nuovo o ites ed è possibile determinare l'icona che verrà visualizzato quando si seleziona la procedura guidata. È inoltre possibile controllare l'ordine in cui i nuovi elementi visualizzati in relazione agli altri elementi disponibili; gli elementi non dovranno essere organizzati in ordine alfabetico.  
  
 È inoltre possibile fornire una procedura guidata che viene avviato in modo diverso, in base ai parametri personalizzati che vengono passati alla procedura guidata quando viene aperto.  
  
 Negli argomenti in questa sezione viene illustrato i file che implementano per fare in modo di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** finestre di dialogo per visualizzare l'elenco della procedura guidata tra modelli e procedure guidate disponibili e i requisiti che deve essere soddisfatti per funzionare nell'IDE di una procedura guidata.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Descrizione del modello Directory (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Viene fornita una panoramica il modello di file di descrizione delle directory e funzionamento nell'IDE per visualizzare le cartelle, file VSZ della procedura guidata e file di modello che sono associati a un progetto nelle finestre di dialogo.  
  
 [Procedura guidata (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Viene illustrato l'IDE di avvio di procedure guidate e sono elencate le tre parti del file con estensione vsz.  
  
 [Interfaccia della procedura guidata (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Viene descritto il `IDTWizard` interfaccia che devono implementare le procedure guidate per funzionare nell'IDE.  
  
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)  
 Viene illustrato come vengono implementate le procedure guidate e che cosa accade quando l'IDE passa i parametri di contesto per l'implementazione.  
  
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)  
 Viene illustrato come utilizzare i parametri personalizzati per controllare il funzionamento della procedura guidata dopo aver avviata la procedura guidata.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.  
  
 [Procedura dettagliata: Creazione di una procedura guidata](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Viene illustrato come creare una procedura guidata.  
  
 [Estensione di progetti](../../extensibility/extending-projects.md)  
 Viene descritto come utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti e soluzioni per organizzare i file di codice e i file di risorse e come implementare il codice sorgente.
