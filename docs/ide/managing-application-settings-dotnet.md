---
title: Gestione delle impostazioni di un'applicazione (.NET)| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msvse_settingsdesigner.err.nameblank
helpviewer_keywords: application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 924d62f31ae073f3b832507182aa511abc484011
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-settings-net"></a>Gestione delle impostazioni di un'applicazione (.NET)
Le impostazioni dell'applicazione consentono di archiviare le informazioni sull'applicazione in modo dinamico. Le impostazioni consentono di archiviare nel computer client le informazioni che non devono essere incluse nel codice dell'applicazione (ad esempio una stringa di connessione), le preferenze dell'utente e altre informazioni necessarie in fase di esecuzione.  
  
 Le impostazioni dell'applicazione sostituiscono le proprietà dinamiche usate nelle versioni precedenti di Visual Studio.  
  
 Ogni impostazione dell'applicazione deve avere un nome univoco. Tale nome può essere formato da una combinazione di lettere, numeri o un carattere di sottolineatura, non può iniziare con un numero e non può contenere spazi. Il nome può essere modificato tramite la proprietà `Name` .  
  
 Le impostazioni dell'applicazione possono essere archiviate come qualsiasi tipo di dati che può essere serializzato come XML che abbia un oggetto `TypeConverter` che implementa `ToString`/`FromString`. I tipi più comuni sono `String`, `Integer`e `Boolean`, ma è anche possibile archiviare i valori come <xref:System.Drawing.Color>, <xref:System.Object>o come una stringa di connessione.  
  
 Anche le impostazioni dell'applicazione contengono un valore. Il valore viene impostato con la proprietà **Valore** e deve corrispondere al tipo di dati dell'impostazione.  
  
 Inoltre, in fase di progettazione, è possibile associare le impostazioni dell'applicazione alla proprietà di un form o di un controllo.  
  
 Sono disponibili due tipi di impostazioni dell'applicazione, in base all'ambito:  
  
-   Le impostazioni con ambito di applicazione possono essere usate per informazioni quali un URL per un servizio Web o una stringa di connessione del database. Questi valori sono associati all'applicazione. Di conseguenza, gli utenti non possono modificarli in fase di esecuzione.  
  
-   Le impostazioni con ambito di utente possono essere usate per informazioni quali la memorizzazione dell'ultima posizione di un form oppure una preferenza su un tipo di carattere. Gli utenti possono modificare questi valori in fase di esecuzione.  
  
 È possibile modificare il tipo di un'impostazione usando la proprietà **Ambito** .  
  
 Nel sistema del progetto le impostazioni dell'applicazione vengono archiviate in due file XML: un file app.config, creato in fase di progettazione al momento della creazione della prima impostazione dell'applicazione, e un file user.config, creato in fase di esecuzione quando l'utente che esegue l'applicazione modifica il valore di una qualsiasi impostazione utente. Le modifiche apportate alle impostazioni utente non vengono scritte su disco a meno che nell'applicazione non venga specificamente chiamato un metodo che esegua questa operazione.  
  
## <a name="creating-application-settings-at-design-time"></a>Creazione di impostazioni dell'applicazione in fase di progettazione  
 In fase di progettazione, le impostazioni dell'applicazione possono essere create in due modi, mediante la pagina **Impostazioni** di **Creazione progetti**oppure mediante la finestra **Proprietà** per un form o un controllo, che consente di associare un'impostazione direttamente a una proprietà.  
  
 Quando si crea un'impostazione con ambito di applicazione, ad esempio una stringa di connessione del database oppure un riferimento a risorse del server, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tale impostazione viene salvata nel file app.config con il tag `<applicationSettings>` . (Le stringhe di connessione vengono salvate nel tag `<connectionStrings>` .)  
  
 Quando si crea un'impostazione con ambito di utente, ad esempio il tipo di carattere predefinito, la pagina iniziale o le dimensioni delle finestre, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tale impostazione viene salvata nel file app.config con il tag `<userSettings>` .  
  
> [!IMPORTANT]
>  Quando si archiviano stringhe di connessione in app.config, è opportuno adottare delle precauzioni per evitare di rivelare informazioni riservate, quali password o percorsi del server, nella stringa di connessione.  
>   
>  Se si ricevono informazioni della stringa di connessione da un'origine esterna, quale un utente che immette un ID utente e una password, accertarsi che tra i valori usati per costruire la stringa di connessione non siano presenti parametri aggiuntivi in grado di modificare il comportamento della connessione.  
>   
>  Valutare l'uso della funzionalità di configurazione protetta per crittografare le informazioni riservate nel file di configurazione. Per altre informazioni, vedere [Protezione delle informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).  
  
> [!NOTE]
>  Poiché non è presente alcun modello di file di configurazione per le librerie di classi, le impostazioni dell'applicazione non si applicano ai progetti Libreria di classi, ad eccezione dei progetti DLL di Visual Studio Tools per Office che possono avere un file di configurazione.  
  
## <a name="using-customized-settings-files"></a>Uso di file di impostazioni personalizzati  
 È possibile aggiungere file di impostazioni personalizzati al progetto per agevolare la gestione dei gruppi di impostazioni. Le impostazioni contenute in un unico file vengono caricate e salvate come unità. Di conseguenza, l'archiviazione delle impostazioni in file diversi per i gruppi di utilizzo frequente e di utilizzo non frequente può determinare un risparmio di tempo nel caricamento e nel salvataggio delle impostazioni.  
  
 Ad esempio, è possibile aggiungere un file quale SpecialSettings.settings al progetto. Mentre la classe `SpecialSettings` non è esposta nello spazio dei nomi `My` , **Visualizza codice** può leggere il file di impostazioni personalizzate contenente `Partial Class SpecialSettings`.  
  
 Progettazione impostazioni cerca innanzi tutto il file Settings.settings creato dal sistema del progetto, ovvero il file predefinito visualizzato nella scheda **Impostazioni** di Creazione progetti. Settings.settings è situato nella cartella Progetti per i progetti [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e nella cartella Proprietà per i progetti [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] . Successivamente, Creazione progetti cerca gli altri file di impostazioni nella cartella radice del progetto. Pertanto, è necessario inserirvi il file di impostazioni personalizzato. Se si aggiunge un file .settings in un altro punto del progetto, questo non verrà trovato da Creazione progetti.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Accesso o modifica delle impostazioni dell'applicazione in fase di esecuzione in Visual Basic  
 Nei progetti [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] è possibile accedere alle impostazioni dell'applicazione in fase di esecuzione usando l'oggetto `My.Settings` . Nella pagina **Impostazioni** scegliere il pulsante **Visualizza codice** per visualizzare il file Settings.vb. Nel file Settings.vb viene definita la classe `Settings` che consente di gestire i seguenti eventi nella classe delle impostazioni: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>e <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. La classe `Settings` nel file Settings.vb è una classe parziale in cui viene visualizzato solo il codice di proprietà dell'utente, non l'intera classe generata. Per altre informazioni sull'accesso alle impostazioni dell'applicazione mediante l'oggetto `My.Settings` , vedere [Accessing Application Settings](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).  
  
 I valori di qualsiasi impostazione con ambito di utente che vengono modificati dall'utente in fase di esecuzione, ad esempio la posizione di un form, vengono archiviati in un file user.config. I valori predefiniti vengono salvati nel file app.config.  
  
 Se si modifica qualsiasi impostazione con ambito di utente in fase di esecuzione, ad esempio durante il test dell'applicazione, e si desidera ripristinare i valori predefiniti per queste impostazioni, scegliere il pulsante **Sincronizza** .  
  
 È consigliabile usare l'oggetto `My.Settings` e il file .settings predefinito per accedere alle impostazioni. Ciò perché è possibile usare Progettazione impostazioni per assegnare proprietà alle impostazioni e le impostazioni utente vengono salvate automaticamente prima della chiusura dell'applicazione. L'applicazione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , comunque, può accedere direttamente alle impostazioni. In quel caso è necessario accedere alla classe `MySettings` e usare un file .settings personalizzato nella radice del progetto. È inoltre necessario salvare le impostazioni utente prima di terminare l'applicazione, come per le applicazioni C#, come illustrato nella sezione seguente.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Accesso o modifica delle impostazioni dell'applicazione in fase di esecuzione in Visual C# #
 In linguaggi diversi da [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], quali [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], è necessario accedere direttamente alla classe `Settings` , come illustrato nell'esempio seguente relativo a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .  
  
```csharp  
Properties.Settings.Default.FirstUserSetting = "abc";  
```  
  
 È inoltre necessario chiamare in modo esplicito il metodo `Save` di questa classe wrapper per rendere persistenti le impostazioni utente. Questa operazione viene generalmente effettuata nel gestore eventi `Closing` del form principale. Nell'esempio seguente relativo a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] viene illustrata una chiamata al metodo `Save` .  
  
```csharp  
Properties.Settings.Default.Save();  
```  
  
 Per informazioni generali sull'accesso alle impostazioni dell'applicazione mediante la classe `Settings` , vedere [Application Settings Overview](/dotnet/framework/winforms/advanced/application-settings-overview). Per impostazioni sullo scorrimento delle impostazioni, vedere questo [post del forum](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso alle impostazioni dell'applicazione](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
