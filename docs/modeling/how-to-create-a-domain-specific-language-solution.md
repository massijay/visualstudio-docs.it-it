---
title: 'Procedura: creare una soluzione di linguaggio specifico di dominio | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Procedura: creare una soluzione per un linguaggio specifico di dominio
Un linguaggio specifico di dominio (DSL) creato utilizzando un specializzato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Prima di iniziare questa procedura, è innanzitutto necessario installare questi componenti:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|SDK di visualizzazione e modellazione di Visual Studio||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione di linguaggio specifico di dominio  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Per creare una soluzione di linguaggio specifico di dominio  
  
1.  Avviare la procedura guidata DSL.  
  
    1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
    2.  Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
    3.  In **i tipi di progetto**, espandere il **altri tipi di progetto** nodo e scegliere **estendibilità**.  
  
    4.  Fare clic su **progettazione di linguaggio specifico di dominio**.  
  
    5.  Nel **nome** , digitare un nome per la soluzione. Fare clic su **OK**.  
  
         Il **Domain-Specific Language progettazione guidata** viene visualizzata.  
  
        > [!NOTE]
        >  Preferibilmente, il nome digitato deve essere un Visual identificatore c# valido, poiché può essere utilizzato per generare il codice.  
  
     ![Finestra di dialogo DSL crea](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  Scegliere un modello DSL.  
  
     Nel **selezionare le opzioni di linguaggio specifico di dominio** selezionare uno dei modelli di soluzione, ad esempio **linguaggio minimo**. Scegliere un modello che è simile al linguaggio specifico di dominio che si desidera creare.  
  
     Per ulteriori informazioni sui modelli di soluzioni, vedere [scelta di un modello di soluzione di linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3.  Immettere un'estensione di **estensione** pagina. Deve essere univoco nel computer e in qualsiasi computer in cui si desidera installare il linguaggio DSL. Verrà visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio utilizzano questa estensione**.  
  
    -   Se è stata utilizzata l'estensione di file in DSL sperimentale precedente che non è stato completamente installato, è possibile cancellarli out utilizzando il **Reimposta l'istanza sperimentale** strumento, che può trovarsi nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menu SDK.  
  
    -   Se un altro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione che utilizza questa estensione di file è stato completamente installato nel computer in uso, è consigliabile disinstallarlo. Nel **strumenti** menu, fare clic su **Gestione estensioni**.  
  
4.  Esaminare e modificare se necessario, i campi nelle pagine rimanenti della procedura guidata. Quando si è soddisfatti con le impostazioni, fare clic su **fine**. Per ulteriori informazioni sulle impostazioni, vedere [pagine della procedura guidata Progettazione DSL](#settings).  
  
     La procedura guidata crea una soluzione che include due progetti, denominati **Dsl** e **DslPackage**.  
  
    > [!NOTE]
    >  Se viene visualizzato un messaggio che avvisa l'utente non eseguono modelli di testo da origini non attendibili, fare clic su **OK**. È possibile impostare questo messaggio non venga nuovamente visualizzato.  
  
##  <a name="a-namesettingsa-the-dsl-designer-wizard-pages"></a><a name="settings"></a>Le pagine della finestra di progettazione DSL  
 È possibile lasciare molti dei campi invariati i valori predefiniti. Assicurarsi, tuttavia, impostare il campo dell'estensione di File.  
  
### <a name="solution-settings-page"></a>Pagina Impostazioni di soluzione  
 **Il modello si desidera basare il linguaggio specifico di dominio?**  
 Scegliere un modello che è simile al linguaggio specifico di dominio che si desidera creare. I diversi modelli forniscono punti di partenza utili. Quando si seleziona un modello di soluzione, la procedura guidata consente di visualizzare una descrizione. Per ulteriori informazioni sui modelli di soluzioni, vedere [scelta di un modello di soluzione di linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **Ciò che si desidera assegnare un nome di linguaggio specifico di dominio?**  
 Il valore predefinito è il nome della soluzione. Codice viene generato da questo valore. Deve essere valido come nome di classe c#.  
  
### <a name="file-extension-page"></a>Pagina di estensione di file  
 **Deve stabilire quale estensione di file?**  
 Digitare una nuova estensione di file.  
  
 Verificare che questa estensione di file non già registrata per l'utilizzo in questo computer, come indicato di seguito:  
  
 Cercare in **altri strumenti e applicazioni registrato per gestire questa estensione**. Se viene visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio utilizzano questa estensione**, è possibile utilizzare questa estensione di file.  
  
 Se è visualizzato un elenco di strumenti o pacchetti, è necessario eseguire una delle operazioni seguenti:  
  
-   Digitare un'estensione di file diverso.  
  
     \- oppure -  
  
-   Reimpostare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] istanza sperimentale. Questo verrà annullata la registrazione di tutti i linguaggi specifici di dominio che sono creati in precedenza. Nel **avviare** menu, fare clic su **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare l'istanza di Microsoft Visual Studio 2010 sperimentale**. È possibile ricompilare qualsiasi altri linguaggi specifici di dominio che si desidera utilizzare di nuovo.  
  
     \- oppure -  
  
-   Se un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione che utilizza questa estensione di file è stato completamente installato nel computer in uso, disinstallarla. Nel **strumenti** menu, fare clic su **Gestione estensioni**.  
  
### <a name="product-settings-page"></a>Pagina Impostazioni di prodotto  
 **Che cos'è il nome del prodotto a cui appartiene il nuovo linguaggio specifico di dominio?**  
 Il valore predefinito è il nome del linguaggio DSL.  
  
 Questo valore viene utilizzato in Windows Explorer (o Esplora File) per descrivere i file con estensione di file.  
  
 **Che cos'è il nome della società a cui appartiene il prodotto?**  
 Il nome della società.  
  
 Questo valore viene incorporato nelle proprietà del pacchetto DSL AssemblyInfo.  
  
 **Che cos'è lo spazio dei nomi radice per i progetti in questa soluzione?**  
 Il valore predefinito è un nome composto dall'azienda e i nomi di prodotto.  
  
### <a name="signing-page"></a>Pagina firma  
 **Creare un file chiave con nome sicuro**  
 L'opzione predefinita consiste nel creare una nuova chiave per firmare l'assembly DSL.  
  
 **Utilizzare una chiave esistente con nome sicuro**  
 Utilizzare questa opzione se si desidera integrare il linguaggio DSL con un altro assembly.  
  
 Per ulteriori informazioni sulla denominazione sicuro, vedere [creazione e uso degli assembly](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Glossario sugli strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

