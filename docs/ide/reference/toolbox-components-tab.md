---
title: Casella degli strumenti, Scheda Componenti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb474e832f815453fd84ba35bc3680b961e17954
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="toolbox-components-tab"></a>Casella degli strumenti, Scheda Componenti
Consente di visualizzare i componenti che è possibile aggiungere alle finestre di progettazione di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Oltre ai componenti [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] inclusi in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio i componenti <xref:System.Messaging.MessageQueue> e <xref:System.Diagnostics.EventLog>, in questa scheda è possibile aggiungere componenti personalizzati o di terze parti. Per altre informazioni, vedere [Procedura: modificare le schede della Casella degli strumenti](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 Per visualizzare questa scheda, scegliere **Casella degli strumenti** dal menu **Visualizza**. Nella **Casella degli strumenti** selezionare la scheda **Componenti**.  
  
 **BackgroundWorker**  
 Crea un'istanza del componente `System.ComponentModel.BackgroundWorker` che può eseguire un'operazione su un thread separato dedicato.  
  
 **DirectoryEntry**  
 Crea un'istanza del componente <xref:System.DirectoryServices.DirectoryEntry> che incapsula un nodo o un oggetto nella gerarchia di Active Directory e può essere usata per interagire con i provider del servizio Active Directory.  
  
 **DirectorySearcher**  
 Crea un'istanza del componente <xref:System.DirectoryServices.DirectorySearcher> che è possibile usare per eseguire query in Active Directory.  
  
 **ErrorProvider**  
 Crea un'istanza del componente `System.Windows.Forms.ErrorProvider` che indica all'utente finale che a un controllo in un form è associato un errore.  
  
 **EventLog**  
 Crea un'istanza del componente <xref:System.Diagnostics.EventLog> che consente di interagire con i log di sistema e i log eventi personalizzati, ad esempio scrivendo eventi e leggendo dati. Per altre informazioni, vedere [Introduzione al componente EventLog](http://msdn.microsoft.com/en-us/a2ba4f28-4b1a-435e-99ef-51b28e21f805).  
  
 **FileSystemWatcher**  
 Crea un'istanza del componente <xref:System.IO.FileSystemWatcher> che consente di monitorare le modifiche apportate a una directory o a un file a cui si ha accesso. Per altre informazioni, vedere [Procedura: configurare istanze del componente FileSystemWatcher](http://msdn.microsoft.com/en-us/2e628234-4951-4135-8a86-28b924070d50).  
  
 **HelpProvider**  
 Crea un'istanza del componente `System.Windows.Forms.HelpProvider` che offre informazioni della Guida, anche in finestre popup.  
  
 **ImageList**  
 Crea un'istanza del componente `System.Windows.Forms.ImageList` che rende disponibili metodi per la gestione di una raccolta di oggetti `System.Drawing.Image`.  
  
 **MessageQueue**  
 Crea un'istanza del componente <xref:System.Messaging.MessageQueue> che consente di interagire con le code di messaggi, leggendo e scrivendo messaggi nelle code, elaborando transazioni ed eseguendo attività di amministrazione delle code. Per altre informazioni, vedere [Utilizzo dei componenti di messaggistica](http://msdn.microsoft.com/en-us/922dbac7-26f0-4e39-b666-ccfc184793d7).  
  
 **PerformanceCounter**  
 Crea un'istanza del componente <xref:System.Diagnostics.PerformanceCounter> che consente di interagire con i contatori delle prestazioni di Windows, creando nuove categorie e istanze, leggendo valori dai contatori ed eseguendo calcoli sui dati dei contatori stessi. Per altre informazioni, vedere [Monitoraggio dei valori limite delle prestazioni](http://msdn.microsoft.com/en-us/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).  
  
 **Processo**  
 Crea un'istanza del componente <xref:System.Diagnostics.Process> che consente di arrestare e avviare i processi del sistema, nonché di manipolare i dati associati a questi. Per altre informazioni, vedere [Monitoraggio e gestione di processi Windows](http://msdn.microsoft.com/en-us/a86bd4c1-b92c-49a0-8f32-61d67837b45e).  
  
 **SerialPort**  
 Crea un'istanza del componente `System.IO.Ports.SerialPort` che rende disponibili le funzioni di I/O sincrono e basato su eventi, l'accesso agli stati di blocco e interruzione, l'accesso alle proprietà del driver seriale.  
  
 **ServiceController**  
 Crea un'istanza del componente <xref:System.ServiceProcess.ServiceController> che consente di manipolare i servizi esistenti, avviandoli e arrestandoli e inviando loro dei comandi. Per altre informazioni, vedere [Monitoraggio di servizi Windows](http://msdn.microsoft.com/en-us/4542ee3f-e052-4cb9-8726-58e9420de222).  
  
 **Timer**  
 Crea un'istanza del componente <xref:System.Windows.Forms.Timer> che consente di aggiungere funzionalità basate sull'ora alle applicazioni basate su Windows. Per altre informazioni, vedere [Componente Timer](/dotnet/framework/winforms/controls/timer-component-windows-forms).  
  
> [!NOTE]
>  È disponibile anche un componente <xref:System.Timers.Timer> basato su sistema che è possibile aggiungere alla **Casella degli strumenti**. Il componente <xref:System.Timers.Timer> è ottimizzato per le applicazioni server mentre il componente <xref:System.Windows.Forms.Timer> di Windows Forms è più adatto all'uso con Windows Forms.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione con i componenti](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [Procedure dettagliate sulla programmazione dei componenti](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [Casella degli strumenti](../../ide/reference/toolbox.md)   
 [Finestra di dialogo Scegli elementi della Casella degli strumenti (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)