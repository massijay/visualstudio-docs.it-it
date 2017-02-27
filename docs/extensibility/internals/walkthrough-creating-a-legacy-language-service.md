---
title: "Procedura dettagliata: Creazione di un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio [framework gestito pacchetto], creazione"
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura dettagliata: Creazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzo delle classi di linguaggio framework \(MPF\) pacchetto gestito per implementare un servizio di linguaggio in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] è semplice. È necessario un VSPackage per ospitare il servizio di linguaggio, il servizio di linguaggio stesso e un parser per la propria lingua.  
  
## Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## Per il modello di progetto Package Visual Studio  
 Il modello di progetto di Visual Studio pacchetto può trovarsi in tre posizioni di modelli diversi nel **Nuovo progetto** la finestra di dialogo:  
  
1.  Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.  
  
2.  Nella sezione relativa all'estendibilità di C\#. Il linguaggio predefinito del progetto è C\#.  
  
3.  Nella sezione relativa all'estendibilità di altri tipi di progetto. La lingua predefinita del progetto è C\+\+.  
  
### Creare un VSPackage  
  
1.  Creare un nuovo pacchetto con il modello di progetto Package Visual Studio.  
  
     Se si aggiunge un servizio di linguaggio a un pacchetto esistente, ignorare i passaggi seguenti e passare direttamente alla procedura "Creazione di classi di Language Service".  
  
2.  Immettere MyLanguagePackage per il nome del progetto e fare clic su **OK**.  
  
     È possibile utilizzare qualsiasi nome desiderato. Queste procedure descritti in questa sezione presuppongono MyLanguagePackage come nome.  
  
3.  Selezionare [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] come la lingua e l'opzione per generare un nuovo file di chiave. Scegliere **Avanti**.  
  
4.  Immettere le informazioni della società e il pacchetto appropriate. Scegliere **Avanti**.  
  
5.  Selezionare **comando di Menu**. Scegliere **Avanti**.  
  
     Se non si prevede di supportare i frammenti di codice, è possibile semplicemente fare clic su Fine e ignorare il passaggio successivo.  
  
6.  Immettere **Inserisci frammento di codice** come il **nome del comando** e `cmdidInsertSnippet` per il **ID di comando**. Scegliere **Fine**.  
  
     Il **nome comando** e **ID di comando** può essere qualsiasi nome desiderato, questi sono solo esempi.  
  
### Creare la classe di servizio di linguaggio  
  
1.  In **Esplora**, pulsante destro del mouse sul progetto MyLanguagePackage, scegliere **Aggiungi**, **riferimento**, quindi scegliere il **Aggiungi nuovo riferimento** pulsante.  
  
2.  Nel **Aggiungi riferimento** nella finestra di dialogo **Microsoft.VisualStudio.Package.LanguageService** nel **.NET** scheda e fare clic su **OK**.  
  
     Questa operazione deve essere eseguito solo una volta per il progetto del pacchetto di linguaggio.  
  
3.  In **Esplora**, del mouse sul progetto VSPackage e scegliere **Aggiungi**, **classe**.  
  
4.  Assicurarsi che **classe** sia selezionato nell'elenco dei modelli.  
  
5.  Immettere **MyLanguageService.cs** per il nome del file di classe e fare clic su **Aggiungi**.  
  
     È possibile utilizzare qualsiasi nome desiderato. Queste procedure dettagliate di seguito presuppongono `MyLanguageService` come nome.  
  
6.  Aggiungere il codice seguente nel file MyLanguageService.cs `using` istruzioni.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modificare la `MyLanguageService` classe da cui derivare la <xref:Microsoft.VisualStudio.Package.LanguageService> classe:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Posizionare il cursore nel "LanguageService" e il **modificare**, **IntelliSense** dal menu **Implementa classe astratta**. Aggiunge i metodi minimi necessari per implementare una classe di servizio di linguaggio.  
  
9. Implementare i metodi astratti, come descritto in [Implementazione di un servizio di linguaggio](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### Registrare il servizio di linguaggio  
  
1.  Aprire il file MyLanguagePackagePackage.cs e aggiungere il codice seguente `using` istruzioni:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrare la classe di servizio di linguaggio, come descritto in [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md). Ciò include gli attributi ProvideXX e le sezioni "Proffering il servizio del linguaggio". Utilizzare in questo argomento viene utilizzato TestLanguageService MyLanguageService.  
  
### Il Parser e Scanner  
  
1.  Implementare un parser e scanner per la lingua, come descritto nella [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Modalità di implementazione il parser e lo scanner è ed esula dall'ambito di questo argomento.  
  
## Funzionalità del linguaggio  
 Per implementare ogni funzionalità nel servizio di linguaggio, in genere una classe derivata dalla classe servizio di linguaggio MPF appropriata, implementare metodi astratti in base alle necessità e l'override dei metodi appropriati. Le classi creare e\/o derivare da è dipende dalle funzionalità di cui si intende supportare. Queste funzionalità vengono discusse in dettaglio in [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md). La procedura seguente è l'approccio generale per la derivazione di una classe da classi di MPF.  
  
#### Derivazione da una classe MPF  
  
1.  In **Esplora**, del mouse sul progetto VSPackage e scegliere **Aggiungi**, **classe**.  
  
2.  Assicurarsi che **classe** sia selezionato nell'elenco dei modelli.  
  
     Immettere un nome appropriato per il file di classe e fare clic su **Aggiungi**.  
  
3.  Nel nuovo file di classe, aggiungere il codice seguente `using` istruzioni.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modificare la classe da cui derivare la classe MPF desiderata.  
  
5.  Aggiungere un costruttore di classe che richiede almeno gli stessi parametri del costruttore della classe di base e passare i parametri del costruttore al costruttore di classe base.  
  
     Ad esempio, il costruttore per una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Source> classe potrebbe essere simile alla seguente:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Dal **modificare**, **IntelliSense** dal menu **Implementa classe astratta** se la classe di base dispone di metodi astratti che devono essere implementati.  
  
7.  In caso contrario, posizionare il cursore all'interno della classe e immettere il metodo da sottoporre a override.  
  
     Ad esempio, digitare `public override` per visualizzare un elenco di tutti i metodi che può essere sottoposto a override nella classe.  
  
## Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)