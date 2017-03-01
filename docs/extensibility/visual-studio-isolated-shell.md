---
title: Visual Studio isolato Shell | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 35
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: d6925bbb3fa432c098f62d223b1c1a7478ecca23
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-isolated-shell"></a>Visual Studio isolato Shell
La shell di Visual Studio isolato consente di creare applicazioni autonome che è possono eseguire side-by-side con altre versioni di Visual Studio. È utilizzato principalmente per ospitare strumenti specializzati che è possono utilizzare i servizi di Visual Studio, ma anche avere un aspetto personalizzato e personalizzazione. Funzionalità di Visual Studio e gruppi di comandi di menu possono facilmente essere attivati e disattivata. Applicazione titoli, le icone delle applicazioni e le schermate sono completamente personalizzabili. Per un elenco delle funzionalità personalizzabili, vedere [personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md).  
  
 Per utilizzare un progetto di shell isolata, è necessario installare Visual Studio SDK. A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Per creare un'applicazione shell isolata, iniziare con un progetto di Visual Studio Shell isolata. Questo progetto contiene tutte le operazioni necessarie per sviluppare e testare un'applicazione shell isolata. Quando si è pronti a scrivere il programma di installazione che consente di distribuire l'applicazione, è necessario ottenere il pacchetto ridistribuibile di shell isolata da [Microsoft Visual Studio Shell (Isolated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Prima di poter accedere il pacchetto ridistribuibile di shell isolata, verrà richiesto di compilare un questionario sui clienti breve.  Dopo aver compilato il sondaggio, si verrà indirizzati a una pagina con i collegamenti ai download del pacchetto ridistribuibile Visual Studio connettersi.  È possibile trovare i collegamenti ai download durante le successive visite al sito di Visual Studio Connect sotto il **programmi | VISUAL STUDIO 2015 e isolato SHELL integrata** scheda.  
  
> [!NOTE]
>  Per ulteriori informazioni su come distribuire un'applicazione basata su shell isolata, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Con la shell isolata  
 Un'applicazione di shell di Visual Studio isolato dispone dell'accesso completo ai servizi di Visual Studio e supporta la personalizzazione speciale e la personalizzazione. Esistono diversi modi per personalizzare un'applicazione shell isolata:  
  
-   È possibile utilizzare componenti VSPackage e Managed Extensibility Framework (MEF) per estendere un'applicazione shell isolata esattamente come si farebbe in un'altra estensione di Visual Studio. Per ulteriori informazioni, vedere [estensione Shell isolata](../extensibility/extending-the-isolated-shell.md).  
  
-   Per rendere le funzionalità di Visual Studio e gruppi di comandi di menu disponibili o non è disponibile, aggiornare il file vsct nel progetto dell'interfaccia utente dell'applicazione.  
  
-   Per rimuovere **opzioni** pagine o altri componenti di Visual Studio shell dell'applicazione, aggiornare il file .pkgundef dell'applicazione.  
  
-   Per modificare il comportamento della shell o altri aspetti dell'aspetto, aggiornare il file. pkgdef dell'applicazione.  
  
-   Alcuni aspetti della shell possono essere specificati anche quando l'applicazione viene avviata. A tale scopo, aggiornare i parametri nella chiamata al punto di ingresso iniziale del appenvstub.dll.  
  
 Per ulteriori informazioni sui diversi elementi che è possibile personalizzare, vedere [gli elementi della Shell isolata](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Funzionalità standard della Shell isolata  
 Le funzionalità seguenti sono standard per tutte le edizioni di Visual Studio.  
  
|Categoria funzionalità|Funzionalità|  
|----------------------|-------------|  
|Funzionalità dell'IDE|Importazione/esportazione impostazioni<br /><br /> Programma di installazione del controllo della casella degli strumenti<br /><br /> Elenco attività / elenco errori<br /><br /> Finestra di output<br /><br /> Pagina iniziale<br /><br /> Finestra Proprietà<br /><br /> Casella degli strumenti<br /><br /> Esplora soluzioni<br /><br /> Finestra Segnalibri<br /><br /> Visualizzazione classi<br /><br /> Visualizzatore oggetti<br /><br /> Finestra di comando<br /><br /> Struttura documento<br /><br /> Visualizzazione risorse<br /><br /> Strumento esterno<br /><br /> Windows Communication Foundation (WCF) Aggiungi riferimento al servizio<br /><br /> Language Integrated Query (LINQ) supporto|  
|Editor di progettazione|Esplorazione degli strumenti (ricerca unificata, definizione dell'origine, ereditarietà) del codice<br /><br /> IntelliSense<br /><br /> Smart tag<br /><br /> Gestione frammenti di codice<br /><br /> Frammenti di codice<br /><br /> Refactoring<br /><br /> Elenco<br /><br /> Filtro IntelliSense<br /><br /> Finestra Definizione codice<br /><br /> Progettazione applicazioni<br /><br /> Progettazione Windows Form<br /><br /> Progettazione di Windows Presentation Foundation (WPF)|  
|Debug|Analizzatore di espressioni c#<br /><br /> Il debug locale<br /><br /> Debug gestito<br /><br /> Modifica e continuazione<br /><br /> Debug di cross-thread<br /><br /> Visualizzazioni<br /><br /> DataTips<br /><br /> Debug nativo<br /><br /> Debug di script<br /><br /> Debug di interoperabilità<br /><br /> Il debug Just-in-time (JIT)<br /><br /> Debug multiprocesso<br /><br /> Debug di XSLT<br /><br /> Connetti a processo locale<br /><br /> Punti di traccia<br /><br /> Vincoli di punto di interruzione|  
|Dati|Esplora server (semplificato - solo dati)<br /><br /> Eseguire l'associazione dati ai dati locali (. MDF o. MDB)<br /><br /> Associare dati all'oggetto<br /><br /> Associazione dei dati al servizio Web<br /><br /> Set completo di controlli dati<br /><br /> Editor XML<br /><br /> Associazione dei dati al server di database locale<br /><br /> Finestra Origini dati|  
|Web|Editor HTML<br /><br /> Web browser<br /><br /> Progettazione Web Form<br /><br /> Progetto di sito Web<br /><br /> Progetto Applicazione Web|  
|Estendibilità|Utilizza i componenti MEF e package VS|  
  
## <a name="see-also"></a>Vedere anche  
 [Shell (Isolated o integrato)](../extensibility/shell-isolated-or-integrated.md)
