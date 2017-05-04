---
title: "Procedura: contrassegnare i controlli come controlli sicuri | Microsoft Docs"
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
  - "controlli sicuri [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, strumenti di creazione di pacchetti avanzati"
  - "sviluppo per SharePoint in Visual Studio, controlli sicuri"
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: contrassegnare i controlli come controlli sicuri
  Per motivi di sicurezza, in SharePoint viene fatta distinzione tra controlli Web protetti dagli attacchi script injection e controlli Web che non prevedono tale protezione.  Gli utenti non attendibili possono accedere ai controlli protetti o *controlli sicuri*.  È possibile contrassegnare i controlli come sicuri nella proprietà Voci di controllo sicure di un elemento di progetto SharePoint o in **Progettazione pacchetti** quando si aggiunge un assembly al pacchetto.  Per ulteriori informazioni, vedere  
  
 [Modificare le impostazioni del file Web.config](http://go.microsoft.com/fwlink/?LinkId=178965) e [Registrazione di un web part di Assembly come controllo sicuro](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Le procedure riportate di seguito hanno solo uno scopo dimostrativo.  Contrassegnare i controlli come sicuri solo se si è certi che lo siano realmente.  
  
## Contrassegnare i controlli come sicuri nella proprietà Voci di controllo sicure  
  
#### Per contrassegnare i controlli come sicuri o non sicuri nella proprietà Voci di controllo sicure  
  
1.  Creare una soluzione SharePoint con un progetto Web part visiva.  
  
2.  Aggiungere due controlli alla Web part, ovvero una casella di testo e un pulsante.  Non modificarne i nomi predefiniti, TextBox1 e Button1 rispettivamente.  
  
3.  Aggiungere due voci alla proprietà **Voci di controllo sicure** della Web part.  A tale scopo, selezionare il pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.png "Ellisse di ASP.NET Mobile Designer")\) accanto alla proprietà **Voci di controllo sicure** nella finestra **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo **Voci di controllo sicure**.  
  
4.  Nella finestra di dialogo **Voci di controllo sicure**, selezionare due volte il pulsante **Aggiungi** per aggiungere due voci di controllo sicure al riquadro **Membri**: una per il pulsante e una per la casella di testo.  
  
5.  Selezionare la prima voce di controllo e quindi modificare il valore della proprietà **Sicuro** su **False**, la proprietà **Nome tipo** su **Button1** e la proprietà **Sicurezza script** su **False**.  
  
     Durante questo passaggio il controllo pulsante viene identificato come controllo non sicuro.  
  
6.  Selezionare la seconda voce di controllo sicura nell'elenco.  Lasciare il valore della proprietà **Sicuro** impostata su **True** e impostarne la proprietà **Nome tipo** su **TextBox1** e la proprietà **Sicurezza script** su **True**.  
  
     Il controllo casella di testo verrà contrassegnato come controllo protetto dagli attacchi script injection.  
  
7.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
## Contrassegnare i controlli sicuri in Progettazione pacchetti  
  
#### Per contrassegnare i controlli come sicuri o non sicuri in Progettazione pacchetti  
  
1.  Creare una soluzione SharePoint con un progetto Web part visiva.  
  
2.  Aggiungere due controlli alla Web part, ovvero una casella di testo e un pulsante.  Non modificarne i nomi predefiniti, TextBox1 e Button1 rispettivamente.  
  
     Prendere nota dello spazio dei nomi del controllo in quanto verrà utilizzato in un secondo momento.  
  
3.  Nella barra dei menu, selezionare **Compila**, **Compila soluzione** per compilare il progetto.  
  
4.  Creare un'altra soluzione SharePoint.  
  
5.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il file Package.Package e quindi scegliere **Apri** per aprire **Progettazione pacchetti**.  
  
6.  In **Progettazione pacchetti**, selezionare la scheda **Avanzate**.  
  
7.  In **Assembly aggiuntivi** selezionare il bottone **Aggiungi** e quindi selezionare **Aggiungi assembly esistente** dall'elenco.  
  
8.  Nella finestra di dialogo **Aggiungi assembly esistente**, selezionare il pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.png "Ellisse di ASP.NET Mobile Designer")\) accanto a **Percorso origine**.  
  
9. Scegliere l'assembly dalla soluzione SharePoint creato nel passaggio 1 e quindi scegliere il pulsante **Apri**.  
  
10. Per questo esempio, lasciare l'opzione **Destinazione distribuzione** su GlobalAssemblyCache.  
  
     Questo passaggio determina la distribuzione dell'assembly nella Global Assembly Cache di sistema.  Se si desidera distribuire l'assembly nella cartella dell'applicazione Web \(Bin\), selezionare l'opzione corrispondente.  Per ulteriori informazioni, vedere [Distribuzione di web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. Nella casella **Controlli sicuri**, selezionare il pulsante **Fare clic qui per aggiungere un nuovo elemento**.  
  
12. Immettere i valori riportati nella tabella seguente per le proprietà.  
  
    |Nome proprietà|Valore|  
    |--------------------|------------|  
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1.VisualWebPart1**.|  
    |Nome tipo|Button1|  
    |Nome assembly|Nome di assembly sicuro, ad esempio Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c.|  
    |Sicuro|Deselezionare la casella di controllo **Sicuro**.|  
    |Sicurezza script|Lasciare deselezionata la casella di controllo **Sicurezza script**.|  
  
    > [!NOTE]  
    >  Il valore **Nome assembly** degli assembly aggiunti mediante la scheda **Avanzate** di **Progettazione pacchetti** non può essere un token, ma deve essere un assembly con nome sicuro.  Per ulteriori informazioni, vedere [Creazione e utilizzo degli assembly con nome sicuro](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Scegliere il tasto TAB per creare un'altra voce di controllo sicura.  
  
14. Selezionare di nuovo il pulsante **Fare clic qui per aggiungere un nuovo elemento**.  
  
15. Immettere i valori riportati nella tabella seguente per le proprietà.  
  
    |Nome proprietà|Valore|  
    |--------------------|------------|  
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1.VisualWebPart1**.|  
    |Nome tipo|TextBox1|  
    |Nome assembly|Nome di assembly sicuro, ad esempio Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c.|  
    |Sicuro|Selezionare la casella di controllo **Sicuro**.|  
    |Sicurezza script|Selezionare la casella di controllo **Sicurezza script**.|  
  
16. Scegliere il tasto TAB e quindi scegliere il pulsante **OK** per chiudere la finestra di dialogo.  
  
## Vedere anche  
 [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  