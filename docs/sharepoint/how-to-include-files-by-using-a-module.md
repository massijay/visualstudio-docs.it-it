---
title: "Procedura: includere file mediante un modulo | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "moduli [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, moduli"
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Procedura: includere file mediante un modulo
  I *moduli*, da non confondere con i moduli di [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], sono contenitori che consentono di distribuire file quali pagine master ASPX, file di testo o immagini in SharePoint.  
  
 È possibile scegliere di distribuire un file in una raccolta documenti o come un file normale, ad esempio default.aspx, all'esterno di una raccolta documenti.  Per aggiungere un file a una raccolta documenti, specificare `Type="GhostableInLibrary"` come attributo nell'elemento **File**.  Questa impostazione indica a SharePoint di creare un elemento elenco da associare al file quando viene aggiunto alla libreria.  Per distribuire un file all'esterno di una raccolta documenti, specificare `Type="Ghostable"` oppure omettere semplicemente l'attributo **Type**.  
  
## Aggiunta di un modulo a una soluzione SharePoint  
  
#### Per aggiungere un modulo  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare o aprire un progetto SharePoint.  
  
     Per ulteriori informazioni, vedere [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  In **Esplora soluzioni** scegliere il nodo del progetto, quindi, nella barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Nell'elenco dei modelli SharePoint, scegliere il modello **Modulo** e quindi fare click sul pulsante **OK**.  
  
     Questo passaggio crea un nodo nel progetto denominato Module1.  
  
4.  In Module1, eliminare il file Sample.txt.  
  
     Il file Sample.txt è incluso in tutti i nuovi moduli a scopo di esempio e non è necessario. Osservare che l'eliminazione del file comporta anche la rimozione della relativa voce dal file Elements.xml del modulo.  
  
5.  Se si desidera che i file vengano distribuiti in una determinata struttura di cartelle in SharePoint, creare tali cartelle in Module1 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scegliendo il nodo Module1, quindi sulla barra dei menu, scegliendo **Progetto**, **Nuova cartella**.  
  
6.  Scegliere la cartella in cui si desidera aggiungere il file e scegliere, nella barra dei menu, **Progetto**, **Aggiungi elemento esistente**.  
  
7.  Selezionare uno o più file da distribuire in SharePoint, quindi fare clic su **Aggiungi**.  
  
     Quando si aggiunge un file al progetto, viene automaticamente aggiunta una voce correlata al file Elements.xml del modulo.  Quando viene distribuito il progetto, i file vengono copiati nel server SharePoint, in corrispondenza della directory radice del progetto, specificata dall'attributo **Url** dell'elemento **File**, ad esempio `Url="Module1/New Folder/SomeFile.doc`.  Se si desidera modificare il percorso di distribuzione di un file, spostarlo in un'altra cartella in **Esplora soluzioni** o modificare l'impostazione del relativo attributo **Url**.  
  
8.  Per qualsiasi file da visualizzare in una raccolta documenti, aggiungere l'attributo `Type="GhostableInLibrary"` alla rispettiva voce in Elements.xml.  Di seguito è riportato un esempio:  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Distribuire il progetto.  
  
     I file vengono copiati nei percorsi specificati in SharePoint.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  