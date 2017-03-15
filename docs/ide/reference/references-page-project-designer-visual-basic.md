---
title: "Riferimenti (pagina), Creazione progetti (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesReference"
  - "vb.ProjectPropertiesUnusedReference"
  - "vb.ProjectPropertiesReferencePaths"
helpviewer_keywords: 
  - "Riferimenti (pagina) in Creazione progetti"
  - "Creazione progetti, pagina Riferimenti"
  - "Riferimenti inutilizzati (finestra di dialogo)"
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Riferimenti (pagina), Creazione progetti (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La pagina **Riferimenti** di **Progettazione progetti** consente di gestire riferimenti, riferimenti Web e spazi dei nomi importati del progetto.  I progetti possono contenere riferimenti a componenti COM, servizi Web XML, assembly o librerie di classi .NET Framework oppure altre librerie di classi.  Per ulteriori informazioni sull'utilizzo dei riferimenti, vedere [Gestione dei riferimenti in un progetto](../../ide/managing-references-in-a-project.md).  
  
 Per accedere alla pagina **Riferimenti**, scegliere un nodo di progetto \(non il nodo **Soluzione** \) in **Esplora soluzioni**.  Scegliere **Progetto**, **Proprietà** sulla barra dei menu.  Quando viene visualizzato progettazione progetti, fare clic sulla scheda **Riferimenti**.  
  
## Elenco UIElement  
 Le opzioni riportate di seguito consentono di selezionare o rimuovere riferimenti e spazi dei nomi importati del progetto.  
  
 **Riferimenti inutilizzati**  
 Fare clic su questo pulsante per accedere alla finestra di dialogo **Riferimenti inutilizzati**.  
  
 La finestra di dialogo **Riferimenti inutilizzati** consente di rimuovere i riferimenti inclusi nel progetto ma non utilizzati effettivamente dal codice.  Contiene una griglia in cui sono elencati **Nome riferimento**, **Tracciato**e altre informazioni sui riferimenti allo spazio dei nomi utilizzati nel progetto.  All'interno della griglia, selezionare i riferimenti dello spazio dei nomi che si desidera rimuovere dal progetto, quindi fare clic su **Rimuovi**.  
  
 **Percorsi riferimento**  
 Fare clic su questo pulsante per accedere alla finestra di dialogo **Percorsi riferimento**.  
  
> [!NOTE]
>  Quando il sistema del progetto cerca un riferimento a un assembly, il sistema risolve il riferimento vengono ricercati nelle seguenti posizioni, nell'ordine seguente:  
>   
>  1.  La cartella del progetto.  I file della cartella del progetto vengono visualizzati in **Esplora soluzioni** a **Mostra tutti i file** non è attivo.  
> 2.  Cartelle specificate nella finestra di dialogo **Percorsi riferimento**.  
> 3.  Cartelle visualizzati i file nella finestra di dialogo **Aggiungi riferimento**.  
> 4.  La cartella obj del progetto.  \(Quando si aggiunge un riferimento COM al progetto, uno o più assembly possono essere aggiunto alla cartella obj del progetto\).  
  
 **Riferimenti**  
 In questo elenco sono visualizzati tutti i riferimenti del progetto, utilizzati o inutilizzati.  
  
 **Aggiungi**  
 Scegliere questo pulsante per aggiungere un riferimento o un riferimento Web all'elenco **Riferimenti**.  
  
 Scegliere **Riferimento** per aggiungere un riferimento al progetto tramite la finestra di dialogo Aggiungi riferimento.  
  
 Scegliere **Riferimento Web** per aggiungere un riferimento Web al progetto tramite la finestra di dialogo Aggiungi riferimento Web.  
  
 **Rimuovi**  
 Selezionare uno o più riferimenti nell'elenco **Riferimenti** e scegliere questo pulsante per eliminarli.  
  
 **Aggiorna riferimento Web**  
 Selezionare un riferimento Web nell'elenco **Riferimenti** e scegliere questo pulsante per aggiornarlo.  
  
 **Spazi dei nomi importati**  
 È possibile digitare uno spazio dei nomi personalizzato in questa casella e scegliere **Aggiungi importazione utente** per aggiungerlo all'elenco degli spazi dei nomi.  
  
 È possibile creare alias per gli spazi dei nomi importati dall'utente.  A tal fine, immettere l'alias e lo spazio dei nomi nel formato *alias*\=*spazio dei nomi*.  Questa operazione risulta utile se si utilizzano spazi dei nomi lunghi, come: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  
  
 **Aggiungi importazione utente**  
 Scegliere questo pulsante per aggiungere lo spazio specificato nella casella **Spazi dei nomi importati** all'elenco degli spazi dei nomi importati.  Il pulsante è attivo unicamente se lo spazio dei nomi specificato non è presente nell'elenco.  
  
 **Elenco Spazi dei nomi**  
 In questo elenco sono visualizzati tutti gli spazi dei nomi disponibili.  Le caselle di controllo per gli spazi dei nomi inclusi nel progetto sono selezionate.  
  
 **Aggiorna importazione utente**  
 Selezionare uno spazio dei nomi specificato dall'utente nell'elenco degli spazi dei nomi, digitare il relativo nome sostitutivo nella casella **Spazi dei nomi importati** e scegliere questo pulsante per modificare il nuovo spazio dei nomi.  Il pulsante è attivo unicamente se lo spazio dei nomi selezionato è tra quelli aggiunti all'elenco mediante il pulsante **Aggiungi importazione utente**.  È possibile aggiungere:  
  
-   Classi o spazi dei nomi, ad esempio <xref:System.Math?displayProperty=fullName>.  
  
-   Importazioni con alias, ad esempio `VB=Microsoft.VisualBasic`.  
  
-   Spazi dei nomi XML, ad esempio `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  
  
## Vedere anche  
 [Procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/it-it/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Procedura: aggiungere o rimuovere spazi dei nomi importati \(Visual Basic\)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/it-it/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)