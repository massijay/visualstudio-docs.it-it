---
title: Creare soluzioni e progetti | Microsoft Docs
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 9a4b04dc59c409a5c68ad1fb376abb33b3859ff6
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---

# Creare soluzioni e progetti
<a id="create-solutions-and-projects" class="xliff"></a>

I progetti sono i contenitori logici di tutti gli elementi necessari per compilare l'applicazione. Quando si crea un progetto scegliendo **File**, **Nuovo**, **Progetto** nel menu principale, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea una soluzione per contenerlo. È quindi possibile aggiungere altri progetti nuovi o esistenti alla soluzione, se necessario. È possibile creare progetti dai file di codice esistenti ed è possibile creare progetti temporanei (solo .NET) che verranno eliminati al termine del loro uso.

> [!NOTE]
>  Le descrizioni in questo argomento sono basate sull'edizione Visual Studio Community. Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti in questa sezione, in quanto dipendono dalle impostazioni o dall'edizione di Visual Studio. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## Creare un progetto da un modello di progetto installato
<a id="create-a-project-from-an-installed-project-template" class="xliff"></a>  
 Scegliere **File**, **Nuovo**, **Progetto** nel menu principale per visualizzare la finestra di dialogo Nuovo progetto. Nel riquadro sinistro sotto **Installati**, **Modelli** selezionare il linguaggio la piattaforma o la tecnologia di programmazione e quindi scegliere un modello tra quelli disponibili nel riquadro centrale.  

 Nella finestra di dialogo **Nuovo progetto** l'elenco a discesa **Soluzione** offre l'opzione per creare il nuovo progetto in una soluzione nuova o esistente o in una nuova istanza di Visual Studio.  

## Creare un progetto da file di codice esistenti
<a id="create-a-project-from-existing-code-files" class="xliff"></a>  
 Se si ha una raccolta di file di origine separati, è possibile creare facilmente un progetto che li contenga. Scegliere **File**, **Nuovo**, **Progetto da codice esistente** per avviare la **Creazione guidata nuovo progetto da file di codice esistenti** e quindi seguire le istruzioni.  

> [!TIP]
>  Questa opzione risulta più adatta per raccolte di file relativamente semplici.  

## Creare un progetto temporaneo (C# e Visual Basic)
<a id="create-a-temporary-project-c-and-visual-basic" class="xliff"></a>
 Quando si lavora con i progetti temporanei, è possibile creare ed effettuare prove con un progetto .NET senza specificare un percorso sul disco. Quando si crea un progetto, è sufficiente selezionare un tipo di progetto e un modello e specificare un nome nella finestra di dialogo **Nuovo progetto**. In qualsiasi momento mentre si lavora con il progetto temporaneo è possibile salvarlo o rimuoverlo.  

## Creare un progetto .NET che usa una specifica versione di .NET Framework
<a id="create-a-net-project-that-targets-a-specific-version-of-the-net-framework" class="xliff"></a>  
 È possibile creare un progetto destinato a versioni precedenti di .NET Framework mediante il menu a discesa della versione prescelta di **.NET Framework** nella parte superiore della finestra di dialogo **Nuovo progetto**. Impostare questo valore prima di selezionare un modello di progetto, poiché nell'elenco verranno visualizzati solo i modelli compatibili con tale versione di .NET Framework.  

 È necessario disporre di .NET Framework 3.5 installato nel sistema peri accedere alle versioni di framework precedenti alla 4.0.  

## Scaricare soluzioni di esempio
<a id="download-sample-solutions" class="xliff"></a>  
 È possibile usare Visual Studio per scaricare e installare esempi di soluzioni dalla [raccolta di codici MSDN](http://go.microsoft.com/fwlink/?LinkId=254185), nonché da altre origini, ad esempio i repository GIT.

 È possibile scaricare esempi individualmente oppure scaricare un Pacchetto di esempi contenente gli esempi correlati che condividono una tecnologia o un argomento. Si riceverà una notifica al momento della pubblicazione delle modifiche apportate al codice sorgente per ogni esempio scaricato.  

 Per altre informazioni vedere [Visual Studio Samples](../ide/visual-studio-samples.md) (Esempi di Visual Studio).  

## Aggiungere singoli file a livello di soluzione
<a id="add-single-files-at-the-solution-level" class="xliff"></a>  
 In alcuni casi più progetti possono fare riferimento a un solo file oppure un file potrebbe contenere testo o dati vari che appartengono logicamente al livello della soluzione anziché a un progetto specifico.  Per aggiungere un elemento singolo a una soluzione:  

- Fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi**, **Nuovo elemento** o **Aggiungi**, **Elemento esistente**.  

## Creare soluzioni vuote
<a id="create-empty-solutions" class="xliff"></a>  
 Anche se un progetto può risiedere in una soluzione, è possibile creare soluzioni che non contengono progetti. È anche possibile aprire progetti di codice senza usare una soluzione.

#### Per creare una soluzione vuota
<a id="to-create-an-empty-solution" class="xliff"></a>  

1.  Nel menu **File** scegliere **Nuovo**, **Nuovo progetto**.  

2.  Nel riquadro sinistro scegliere **Installato**, **Altri tipi di progetto**, **Soluzioni di Visual Studio** nell'elenco espanso.  

3.  Nel riquadro centrale scegliere **Soluzione vuota**.  

4.  Impostare i valori **Nome** e **Percorso** per la soluzione e quindi fare clic su **OK**.  

Dopo aver creato una soluzione vuota, è possibile aggiungervi progetti o elementi nuovi o esistenti scegliendo **Aggiungi nuovo elemento** o **Aggiungi elemento esistente** nel menu **Progetto**.

### Eliminare soluzioni
<a id="delete-solutions" class="xliff"></a>  
 È possibile eliminare definitivamente una soluzione, ma non usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Prima di eliminare una soluzione, spostare eventuali progetti da riutilizzare in un'altra soluzione. Usare quindi Esplora file per eliminare la directory contenente i due file di soluzione con estensione sln e suo.  

> [!NOTE]
>  Il file con estensione suo è un file nascosto che non viene visualizzato nelle impostazioni predefinite di Esplora file.  

##### Per eliminare una soluzione
<a id="to-delete-a-solution" class="xliff"></a>  

1.  In **Esplora soluzioni** scegliere **Apri cartella in Esplora file** nel menu di scelta rapida della soluzione da eliminare.

2.  In Esplora file spostarsi in alto di un livello.

3.  Selezionare la directory contenente la soluzione e premere CANC.

## Vedere anche
<a id="see-also" class="xliff"></a>  
 [Solutions and Projects](../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)   

