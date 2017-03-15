---
title: "Nozioni di base di Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Installer, package VS"
  - "Package VS, nozioni di base di Windows Installer"
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Nozioni di base di Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Windows Installer installa e Disinstalla le applicazioni o software sul computer dell'utente, eseguire queste attività in unità denominate i componenti di Windows Installer \(talvolta chiamati WICs o solo i componenti\). Un GUID identifica ogni WIC, ovvero l'unità base di conteggio dei riferimenti per le impostazioni tramite Windows Installer e installazione.  
  
 Per una documentazione completa di Windows Installer, vedere l'argomento di Platform SDK, [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## Creazione di un VSPackage  
 Windows Installer utilizza i pacchetti di installazione, che contengono informazioni che è necessario Windows Installer per installare, disinstallare o ripristinare un prodotto e per eseguire l'interfaccia utente del programma di installazione \(UI\). Ogni pacchetto di installazione di un file con estensione msi, che contiene un database di installazione, un flusso di informazioni di riepilogo e i flussi di dati per le varie parti dell'installazione. Per utilizzare il programma di installazione, è necessario creare un'installazione. Poiché il programma di installazione consente di organizzare le installazioni sul concetto di componenti e archivia le informazioni sull'installazione in un database relazionale, il processo di creazione di un pacchetto di installazione su vasta scala comporta i passaggi seguenti:  
  
1.  Pianificare l'installazione di authoring per supportare il controllo delle versioni e le strategie side\-by\-side.  
  
2.  Identificare le funzionalità da presentare agli utenti.  
  
3.  Organizzare i package VS e le dipendenze in componenti.  
  
4.  Popolare il database di installazione con le informazioni.  
  
5.  Convalidare il pacchetto di installazione.  
  
 Questa documentazione riguarda principalmente il primo e terzo passaggio del processo. Durante questa procedura organizzare le funzionalità di VSPackage WICs pertanto possibile definire il controllo delle versioni e per le versioni successive di strategia di manutenzione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. I seguenti tre passaggi sono trattati in dettaglio nella documentazione di Windows Installer in Platform SDK.  
  
## Termini chiave  
 Di seguito sono definizioni dei termini chiave relativi alla tecnologia Windows Installer.  
  
 Risorsa  
 File, chiavi del Registro di sistema, collegamenti, o e così via che può essere installato in un computer. Queste risorse sono raggruppate logicamente in componenti di Windows Installer.  
  
 Componente di Windows Installer \(WIC\)  
 L'unità di installazione che rappresenta un raggruppamento logico di risorse correlate, che vengono installati e disinstallati come un'unità di base. Componenti di Windows Installer sono identificati da un ID componente univoco o un GUID. Inoltre, Windows Installer mantiene il riferimento a livello di WIC di conteggio. Per la flessibilità massima controllo delle versioni, includere non più di una risorsa primaria, ad esempio una DLL, in un determinato WIC. Si noti che dopo individuare e popolare un WIC, assegnargli un GUID e distribuirlo, è possibile modificare la composizione. Per ulteriori informazioni, vedere [organizzare le applicazioni in componenti](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Pacchetto \(package Redist\)  
 Un'unità di distribuzione che include un file con estensione msi e i file di origine esterna a cui questo file potrebbe fare riferimento. Un pacchetto contiene tutte le informazioni necessarie per eseguire l'interfaccia utente e per installare o disinstallare l'applicazione Windows Installer.  
  
 file con estensione msi  
 Un file di archiviazione strutturata COM contenente le istruzioni e i dati necessari per installare un'applicazione. Ogni pacchetto contiene almeno un file con estensione msi. Il file con estensione msi contiene il database di programma di installazione, un flusso di informazioni di riepilogo e probabilmente una o più trasformazioni e i file di origine interna. Vengano installati i file possono essere compressi in un file CAB e archiviati in un flusso di file con estensione msi o archiviati, compressi o non compressi, all'esterno del file con estensione msi sul supporto di origine. Per ulteriori informazioni, vedere [estensioni di File di Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## Imposizione di regole di Windows Installer  
 Due set di regole determinano la distribuzione di risorse tramite i componenti del programma di installazione. Un set di regole viene mantenuto dal programma di installazione di Windows, mentre è necessario applicare il secondo set gli autori di installazione.  
  
> [!NOTE]
>  Applicazione delle regole di Windows Installer si verifica solo se si esegue una convalida del file MSI. Tuttavia, vengono avvisati da considerare queste regole come procedure consigliate. Per ulteriori informazioni, vedere [convalida di un Database di installazione](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) e [convalida del pacchetto](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### Regole applicate a livello di programma di installazione  
  
-   Tutti i file in un determinato componente devono essere installati nella stessa directory. Al contrario, i file installati per separare le cartelle devono appartenere per separare i componenti.  
  
-   Può esistere un solo percorso della chiave per ogni componente. Il percorso della chiave è semplicemente una chiave del Registro di sistema o file che rappresenta l'intero componente.  
  
#### Responsabilità del Provider di componenti  
  
-   Le due risorse che potrebbe essere fornito separatamente nelle versioni successive deve essere disponibile in componenti separati. Le risorse devono essere raggruppate in stesso componente solo quando si è certi che queste risorse mai spedirà separatamente. Infatti, è consigliabile che tutte le risorse principali \(ad esempio DLL\) esistono sempre nello WICs separato. Per ulteriori informazioni, vedere [la definizione di componenti](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Nessuna risorsa di versione deve mai fornito con più WIC.  
  
## Vedere anche  
 [Cosa accade se le regole dei componenti vengono interrotte.](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)