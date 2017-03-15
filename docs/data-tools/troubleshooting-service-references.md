---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
In questo argomento vengono elencati i problemi comuni che possono verificarsi durante l'utilizzo di riferimenti a [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] o [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Restituzione di errore nei dati da un servizio  
 Quando si restituisce un oggetto `DataSet` o `DataTable` da un servizio, è possibile che venga generata un'eccezione che indica il superamento della quota massima delle dimensioni dei messaggi in arrivo.  Per impostazione predefinita, la proprietà `MaxReceivedMessageSize` di alcune associazioni è impostata su un valore relativamente basso per limitare l'esposizione ad attacchi Denial of service.  È possibile aumentare questo valore per evitare che l'eccezione venga generata.  Per ulteriori informazioni, vedere <xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>.  
  
 Per correggere l'errore, eseguire le seguenti operazioni:  
  
1.  In **Esplora soluzioni** fare doppio clic sul file app.config per aprirlo.  
  
2.  Individuare la proprietà `MaxReceivedMessageSize` e impostarla su un valore più alto.  
  
## Impossibile trovare un servizio in Soluzione personale  
 Facendo clic sul pulsante **Individua** nella finestra di dialogo **Aggiungi riferimenti al servizio**, uno o più progetti della libreria di servizi WCF della soluzione non vengono visualizzati nell'elenco dei servizi.  Questo problema può verificarsi quando alla soluzione è stata aggiunta una libreria di servizi non compilata.  
  
 Per correggere l'errore, eseguire le seguenti operazioni:  
  
-   In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto della libreria di servizi WCF e selezionare **Compila**.  
  
## Errore durante l'accesso a un servizio su un desktop remoto  
 Quando un utente accede a un servizio WCF ospitato dal Web mediante una connessione desktop remoto senza disporre delle autorizzazioni amministrative, viene utilizzata l'autenticazione NTLM.  Se l'utente non dispone delle autorizzazioni amministrative, può venire visualizzato il seguente messaggio di errore: "La richiesta HTTP è non autorizzata con lo schema di autenticazione client 'Anonimo.'  Intestazione di autenticazione ricevuta dal server: 'NTLM'."  
  
 Per correggere l'errore, eseguire le seguenti operazioni:  
  
1.  Nel progetto del sito Web aprire le pagine **Proprietà**.  
  
2.  Deselezionare la casella di controllo **Autenticazione NTLM** nella scheda **Opzioni di avvio**  
  
    > [!NOTE]
    >  È necessario disattivare l'autenticazione NTLM solo per siti Web che contengono esclusivamente servizi WCF,  la cui sicurezza viene gestita tramite la configurazione nel file web.config.  In questo modo non è necessario effettuare l’autenticazione NTLM.  
  
 Per ulteriori informazioni, vedere [Risoluzione dei problemi relativi alle eccezioni: System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md).  
  
## Impostazione del livello di accesso per le classi generate senza alcun effetto  
 A volte l'impostazione dell'opzione **Livello di accesso per le classi generate** nella finestra di dialogo **Configura riferimenti al servizio** su **Internal** o **Friend** potrebbe non funzionare.  Anche se l'opzione risulta impostata nella finestra di dialogo, le relative classi di supporto vengono generate con un livello di accesso `Public`.  
  
 Si tratta di una limitazione nota di determinati tipi, ad esempio quelli serializzati utilizzando <xref:System.Xml.Serialization.XmlSerializer>.  
  
## Errore durante il debug del codice del servizio  
 Quando si esegue il codice per un servizio WCF dal codice client, è possibile ricevere un messaggio di errore correlato ai simboli mancanti.  Questa situazione può verificarsi quando un servizio, che faceva parte della soluzione, è stato spostato o rimosso dalla soluzione.  
  
 Quando si aggiunge per la prima volta un riferimento a un servizio WCF che fa parte della soluzione corrente, viene aggiunta una dipendenza di compilazione esplicita tra il progetto di servizio e il progetto client di servizio.  Questa operazione garantisce che il client acceda sempre ai file binari del servizio aggiornati, circostanza importante soprattutto per scenari di debug quali l'esecuzione del codice del servizio dal codice client.  
  
 Se il progetto di servizio viene rimosso dalla soluzione, questa dipendenza di compilazione esplicita viene invalidata.  Visual Studio non può più garantire la ricompilazione del progetto di servizio, se necessario.  
  
 Per correggere l'errore, è necessario ricompilare manualmente il progetto di servizio:  
  
1.  Dal menu **Strumenti**, scegliere **Opzioni**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi selezionare **Generale**.  
  
3.  Assicurarsi che la casella di controllo **Mostra configurazioni della build avanzate** sia selezionata, quindi scegliere **OK**.  
  
4.  Caricare il progetto di servizio WCF.  Per ulteriori informazioni, vedere [Procedura: creare soluzioni basate su più progetti](http://msdn.microsoft.com/it-it/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).  
  
5.  Nella finestra di dialogo **Gestione configurazione** impostare **Configurazione soluzione attiva** su **Debug**.  Per ulteriori informazioni, vedere [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).  
  
6.  In **Esplora soluzioni** selezionare il progetto di servizio WCF.  
  
7.  Scegliere **Ricompila** dal menu **Compila** per ricompilare il progetto di servizio WCF.  
  
## I servizi dati WCF non vengono visualizzati nel browser  
 Quando si tenta di visualizzare una rappresentazione XML dei dati in un servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer potrebbe interpretare erroneamente i dati come feed RSS.  È necessario assicurarsi che l'opzione per visualizzare feed RSS sia disabilitata.  
  
 Per correggere l'errore, disabilitare i feed RSS:  
  
1.  In Internet Explorer, scegliere **Opzioni Internet** dal menu **Strumenti**.  
  
2.  Nella sezione **Feed** della scheda **Contenuto** fare clic su **Impostazioni**.  
  
3.  Nella finestra di dialogo **Impostazioni feed**, deselezionare la casella di controllo **Attiva visualizzazione di lettura feed** e quindi fare clic su **OK**.  
  
4.  Scegliere **OK** per chiudere la finestra di dialogo **Opzioni Internet**.  
  
## Vedere anche  
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Consuming ASMX and WCF Services Sample](http://msdn.microsoft.com/it-it/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)