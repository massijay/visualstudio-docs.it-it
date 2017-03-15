---
title: "Finestra di dialogo Configura riferimento a servizio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.dlg.ConfigureServiceReference"
helpviewer_keywords: 
  - "Servizi WCF, finestra di dialogo Configura riferimento al servizio"
  - "riferimenti ai servizi [Visual Studio], configurazione comportamento"
  - "Configura riferimento a servizio (finestra di dialogo)"
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Finestra di dialogo Configura riferimento a servizio
La finestra di dialogo **Configura riferimento a servizio** consente di configurare il comportamento dei servizi [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)].  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere Importa\/esporta impostazioni dal menu Strumenti.  Per altre informazioni vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Per accedere alla finestra di dialogo **Configura riferimento a servizio**, fare clic con il pulsante destro del mouse su un riferimento al servizio in **Esplora soluzioni** e scegliere **Configura riferimento a servizio**.  È anche possibile accedere alla finestra di dialogo facendo clic sul pulsante **Avanzate** nella [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
## Elenco attività  
  
-   Per cambiare l'indirizzo al quale è ospitato il servizio WCF, immettere il nuovo indirizzo nel campo **Indirizzo**.  
  
-   Per cambiare il livello di accesso alle classi in un client WCF, selezionare una parola chiave del livello di accesso nell'elenco **Livello di accesso per classi generate**.  
  
-   Per chiamare i metodi di un servizio WCF in modo asincrono, selezionare la casella di controllo **Genera operazioni asincrone**.  
  
-   Per generare i tipi di contratto di messaggio in un client WCF, selezionare la casella di controllo **Genera sempre contratti di messaggio**.  
  
-   Per specificare i tipi di raccolta elenco o dizionario per un client WCF, selezionare i tipi dagli elenchi **Tipo di raccolta** e **Tipo di raccolta dizionario**.  
  
-   Per disabilitare la condivisione dei tipi, deselezionare la casella di controllo **Riutilizza tipi in assembly di riferimento**.  Per abilitare la condivisione di tipi per un sottoinsieme di assembly di riferimento, selezionare la casella di controllo **Riutilizza tipi in assembly di riferimento**, selezionare **Riutilizza tipi negli assembly di riferimento specificati** e selezionare i riferimenti desiderati nell'elenco **Assembly di riferimento**.  
  
## Elenco UIElement  
 **Address**  
 Usato per aggiornare l'indirizzo Web in cui un riferimento al servizio cerca un servizio.  Ad esempio, durante lo sviluppo il servizio potrebbe essere ospitato su un server di sviluppo, quindi spostato a un server di produzione, necessitando un cambio di indirizzo.  
  
> [!NOTE]
>  L'elemento Address non è disponibile quando viene visualizzata la finestra di dialogo **Configura riferimento a servizio** dalla [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
 **Livello di accesso per classi generate**  
 Determina il livello di accesso del codice per le classi del client WCF.  
  
> [!NOTE]
>  Per i progetti di siti Web, questa opzione è impostata sempre su `Public` e non può essere modificata.  Per altre informazioni, vedere [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
 **Genera operazioni asincrone**  
 Determina se i metodi del servizio WCF verranno chiamati in modo sincrono \(impostazione predefinita\) oppure asincrono.  
  
 **Genera operazioni basate su attività**  
 Durante la scrittura di codice asincrono, questa opzione consente di sfruttare la Task Parallel Library \(TPL\) introdotta con .Net 4.  Vedere [Task Parallel Library \(TPL\)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Genera sempre contratti di messaggio**  
 Determina se i tipi di contratto di messaggio verranno generati per un client WCF.  Per altre informazioni sui contratti di messaggio, vedere [Utilizzo dei contratti di messaggio](../Topic/Using%20Message%20Contracts.md).  
  
 **Tipo di raccolta**  
 Specifica il tipo di raccolta elenco per un client WCF.  Il tipo predefinito è <xref:System.Array>.  
  
 **Tipo di raccolta dizionario**  
 Specifica il tipo di raccolta dizionario per un client WCF.  Il tipo predefinito è <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Riutilizza tipi in assembly di riferimento**  
 Determina se un client WCF proverà a riusare i tipi già esistenti negli assembly di riferimento piuttosto di generare nuovi tipi quando un servizio viene aggiunto o aggiornato.  Per impostazione predefinita, questa opzione è selezionata.  
  
 **Riutilizza tipi in tutti gli assembly di riferimento**  
 Quando è selezionata, tutti i tipi nell'elenco **Assembly di riferimento** verranno riutilizzati, se possibile.  Questa opzione è selezionata per impostazione predefinita.  
  
 **Riutilizza tipi negli assembly di riferimento specificati**  
 Quando è selezionata, solo i tipi selezionati nell'elenco **Assembly di riferimento** verranno riutilizzati.  
  
 **Elenco Assembly di riferimento**  
 Contiene un elenco di assembly di riferimento per il progetto o il sito Web.  Quando si seleziona **Riutilizza tipi negli assembly di riferimento specificati**, sarà possibile selezionare o deselezionare i singoli assembly.  
  
 **Aggiungi riferimento Web**  
 Verrà visualizzata [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/it-it/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Usare questa opzione solo per i progetti destinati alla versione 2.0 di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  Il pulsante **Aggiungi riferimento Web** è disponibile solo quando viene visualizzata la finestra di dialogo **Configura riferimento a servizio** dalla [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
## Vedere anche  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)   
 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)   
 [How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)   
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/configure-service-reference-dialog-box.md)   
 [Esempio di utilizzo di servizi ASMX e WCF](http://msdn.microsoft.com/it-it/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)