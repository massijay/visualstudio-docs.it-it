---
title: Creazione di modelli di elemento e progetto personalizzato | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 10
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: be53e0aa5179a38f9c2079513661607b45767a11
ms.lasthandoff: 02/22/2017

---
# <a name="creating-custom-project-and-item-templates"></a>Creazione di progetto personalizzati e modelli di elemento
Visual Studio SDK include modelli di progetto che creano un modello di progetto personalizzati e un modello di elemento personalizzato. Questi modelli includono alcuni le sostituzioni dei parametri comuni e compilare come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. È necessario copiare il file zip file per il percorso  
  
 I modelli di creazione del modello consentono di includere modelli nelle estensioni di dimensioni maggiori. Ciò consente di implementare il controllo della versione nei file di origine e creare un gruppo di progetti di modello in un pacchetto VSIX.  
  
 Per gli scenari di creazione di modelli di base, è necessario utilizzare il **Esporta modello** procedura guidata, l'output in un file compresso. Per ulteriori informazioni sulla creazione di modelli di base, vedere [la creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md).  
  
 A partire da Visual Studio 2017, la ricerca di progetto personalizzati e modelli di elemento sarà non verrà eseguita. Al contrario, l'estensione deve fornire i file di manifesto modello che descrivono il percorso di installazione di questi modelli. È possibile utilizzare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per ulteriori informazioni, vedere [aggiornamento progetto personalizzato e i modelli di Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Lo schema del manifesto del modello è documentato in [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="creating-a-project-template"></a>Creazione di un modello di progetto  
  
1.  Creare un progetto di modello di progetto. È possibile trovare il modello di progetto nel **nuovo progetto** finestra di dialogo, in Visual Basic o Visual c# **estendibilità** cartella.  
  
     Il modello genera un file di classe, un'icona, un file. vstemplate, un file di progetto modificabile denominato ProjectTemplate o csproj e alcuni file che in genere vengono generati da altri tipi di progetto, tale file resx, un file AssemblyInfo e un file Settings. Ogni file di codice contiene le sostituzioni dei parametri comuni dove appropriato.  
  
2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto. Non rimuovere il file di progetto modificabile, il file AssemblyInfo o il file. vstemplate.  
  
3.  Aggiornare il file. vstemplate per riflettere le aggiunte ed eliminazioni. Il [progetto](../extensibility/project-element-visual-studio-templates.md) elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altro contenuto esposti all'utente e aggiungere le sostituzioni dei parametri appropriati.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea un file con estensione zip che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="creating-an-item-template"></a>Creazione di un modello di elemento  
  
1.  Creare un progetto di modello di elemento.  
  
     Il modello genera un file di classe, un'icona, un file. vstemplate e un file AssemblyInfo. Il file di classe contiene alcuni le sostituzioni dei parametri comuni.  
  
2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto.  
  
3.  Aggiornare il file. vstemplate per riflettere le aggiunte ed eliminazioni. Il [progetto](../extensibility/project-element-visual-studio-templates.md) elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altro contenuto esposti all'utente e aggiungere le sostituzioni dei parametri appropriati.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea un file compresso che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="deployment"></a>Distribuzione  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Per distribuire il modello di progetto o un elemento  
  
1.  Creare un progetto VSIX. Per ulteriori informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
2.  Impostare il progetto VSIX come progetto di avvio. Nel **Esplora**, selezionare il nodo del progetto VSIX, pulsante destro del mouse e selezionare **imposta come progetto di avvio**.  
  
3.  Impostare il progetto di modello di progetto come asset del progetto VSIX. Aprire il file vsixmanifest. Andare alla **asset** scheda e fare clic su **nuovo**.  
  
    1.  Impostare il **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Per origine, selezionare il **un progetto nella soluzione corrente** opzione e quindi selezionare il progetto che contiene il modello.  
  
4.  Compilare la soluzione, quindi premere F5. Verrà visualizzata l'istanza sperimentale.  
  
5.  Un progetto di modello di progetto, dovrebbe essere visualizzato il modello di progetto elencato nel **nuovo progetto** finestra di dialogo (**File / nuovo / progetto**), nel nodo Visual Basic o Visual c#. Per un progetto di modello di elemento, si dovrebbe essere elencato nella finestra di dialogo Aggiungi nuovo elemento del modello di elemento (nel **Esplora**, selezionare il nodo del progetto e fare clic su **Aggiungi / nuovo elemento**).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti ai modelli di Visual Studio](../ide/visual-studio-template-reference.md)
