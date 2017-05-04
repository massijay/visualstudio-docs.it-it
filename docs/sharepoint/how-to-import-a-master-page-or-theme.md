---
title: "Procedura: importare una pagina master o un tema | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "importazione di elementi [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, importazione di elementi"
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: importare una pagina master o un tema
  È possibile fornire un aspetto coerente alle pagine del sito SharePoint creando e utilizzando pagine master e temi.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non fornisce modelli per questi elementi, ma è possibile crearli in SharePoint Designer e importali successivamente in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per ulteriori informazioni, vedere [Blocco predefinito: Pagine e interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095) nel sito Web Microsoft.  
  
### Per importare una pagina master o un tema  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare o aprire un progetto SharePoint.  
  
     Per ulteriori informazioni su come creare un progetto SharePoint, vedere [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Sulla barra dei menu scegliere **Progetto**,  **Aggiungi nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
4.  Nell'elenco di modelli SharePoint, scegliere il modello **Modulo** e quindi specificare un nome per il modulo.  
  
     Un modulo contiene i file \(ad esempio, file della pagina master o del tema\) per la distribuzione in un percorso specifico in SharePoint.  
  
5.  Nel modulo, eliminare il file predefinito, denominato Esempi.txt.  
  
6.  Scegliere il nodo del modulo.  
  
7.  Sulla barra dei menu, scegliere **Progetto**, **Aggiungi elemento esistente** quindi scegliere i file della pagine master o del tema.  
  
     I file della pagina master hanno estensione .master e il file del tema hanno estensione .thmx.  
  
8.  Se è stata aggiunta una pagina master, modificare l'impostazione **Risoluzione conflitti di distribuzione** a **Automatico** nelle proprietà del modulo.  
  
    > [!NOTE]  
    >  Gli errori possono verificarsi se il nome della pagina master corrisponde al nome di una pagina master esistente contrassegnata come Pagina master predefinita o Pagina master personalizzata.  Per informazioni su come risolvere questo problema, vedere [Procedura dettagliata: importazione di una pagina master personalizzata e di una pagina del sito con un'immagine](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Nel modulo, aprire il file Elements.xml.  
  
     È necessario aggiornare il file Elements.xml per fare riferimento alla pagina master o al tema aggiunto.  
  
10. Per una pagina master, sostituire il markup del modulo esistente con quello riportato di seguito.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Per un tema, sostituire il markup del modulo esistente con quello riportato di seguito.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Assicurarsi di sostituire i valori segnaposto con i nomi effettivi del modulo e della pagina master o del tema.  
  
     L'attributo `Type="GhostableInLibrary"` indica che l'elemento viene aggiunto al database del contenuto mentre l'attributo `Url` del modulo consente di specificare dove archiviare il file nel database del contenuto SharePoint.  
  
11. Per modificare l'ambito di distribuzione per una pagina master, in **Esplora soluzioni**, aprire il file di funzionalità in progettazione funzionalità e quindi scegliere un nuovo ambito di distribuzione dall'elenco **Ambito**.  
  
     Il valore **Web** indica che la pagina master si applica solamente al sito Web attualmente specificato nel progetto.  Il valore **Sito** indica che la pagina master si applica alla raccolta siti corrente, che comprende tutti i siti secondari e il sito web principale.  Gli altri valori non sono validi.  
  
    > [!NOTE]  
    >  Poiché i temi si applicano solo a livello di raccolta siti, si consiglia di non impostare l'ambito di un tema ad un valore diverso da **Sito**.  Se un tema viene utilizzato in un sito secondario, si possono verificare errori.  
  
12. Sulla barra dei menu scegliere **Compilazione**, **Distribuisci soluzione**.  
  
13. Per verificare se i file sono stati distribuiti correttamente, aprire il sito di SharePoint, selezionare il menu **Azioni sito**, selezionare il comando **Impostazioni sito** quindi scegliere il collegamento **Pagine master** o il collegamento **Temi**.  
  
     Viene visualizzato l'elenco delle pagine master o dei temi e contiene sia le pagine master o i temi che sono stati importati.  
  
## Vedere anche  
 [Pagine master](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Creazione di pagine per SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Utilizzo di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  