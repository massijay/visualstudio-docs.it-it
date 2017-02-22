---
title: "Progettazione del manifesto VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Sdk.VsixManifestEditor"
helpviewer_keywords: 
  - "vsixmanifest"
  - "manifesto VSIX"
  - "progettazione manifesto"
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Progettazione del manifesto VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Modifica un file manifesto di pacchetto VSIX, che imposta il comportamento di installazione per un'estensione di Visual Studio.  
  
 Il **Progettazione del manifesto VSIX** esegue il mapping allo schema VSIX sottostante. Ogni elemento dello schema può essere impostato utilizzando un controllo corrispondente nella finestra di progettazione. Per ulteriori informazioni sullo schema, vedere [Riferimento dello Schema 2.0 estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Per aprire la **Progettazione del manifesto VSIX**, individuare un file source.extension.vsixmanifest nel **Esplora**, aprire il file. Se il file non contiene codice XML valido, non verrà aperto Progettazione manifesto.  
  
> [!NOTE]
>  Viene restituito come output Extension. vsixmanifest Source.Extension.vsixmanifest quando il pacchetto viene compilato.  
  
## Elenco UIElement  
 Il **Progettazione del manifesto VSIX** contiene quattro sezioni che corrispondono a questi elementi di primo livello dello schema:  
  
-   Metadati  
  
-   Installare le destinazioni  
  
-   Asset  
  
-   Dipendenze  
  
 L'area di intestazione contiene i seguenti controlli.  
  
 **Nome prodotto**  
 Descrive il nome di estensione.  
  
 **ID prodotto**  
 Specifica le informazioni di identificazione univoco per il pacchetto.  
  
 **Autore**  
 Specifica il nome dell'autore dell'estensione.  
  
 **Versione**  
 Specifica il numero di versione dell'estensione.  
  
 Il **metadati** scheda contiene i seguenti controlli.  
  
 **Descrizione**  
 Fornisce una descrizione dell'estensione, deve essere visualizzato **Gestione estensioni**.  
  
 **Linguaggio**  
 Specifica la lingua predefinita per il pacchetto, che corrisponde ai dati testuali nel manifesto. Il `Language` attributo segue la convenzione di codice delle impostazioni locali di common language runtime \(CLR\) per gli assembly di risorse, ad esempio, en\-us, en, fr\-fr. Per impostazione predefinita, il valore è neutro; Ciò significa che il pacchetto verrà eseguito in qualsiasi versione localizzata di Visual Studio.  
  
 **Licenza**  
 Specifica il file di testo che contiene la licenza utente, se presente.  
  
 **Icona**  
 Specifica il file di grafica \(con estensione png, bmp, JPEG,. ico\) che contiene l'icona da visualizzare in **Gestione estensioni**, se è presente un'icona. L'immagine dell'icona deve essere 32 x 32 pixel o viene ridimesionata alle quote. Se non viene specificata alcuna icona, **Gestione estensioni** utilizza un'icona predefinita.  
  
 **Immagine di anteprima**  
 Specifica il file di grafica \(con estensione png, bmp, JPEG,. ico\) che contiene l'immagine di anteprima da visualizzare in **Gestione estensioni**, se è presenta un'immagine di anteprima. L'immagine di anteprima deve essere di 200 x 200 pixel. Se viene specificata alcuna immagine di anteprima, **Gestione estensioni** utilizza un'immagine predefinita.  
  
 **Tag**  
 Aggiunge il tag di testo da utilizzare per i suggerimenti per la ricerca.  
  
 **Note sulla versione**  
 Specifica un file \(con estensione txt,. RTF\) che contiene le note sulla versione. Richiede inoltre l'URL di un sito Web che consente di visualizzare le note sulla versione.  
  
 **Guida introduttiva**  
 Specifica un file \(con estensione txt,. RTF\) che contiene informazioni su come utilizzare l'estensione o il contenuto nel pacchetto VSIX. In questa guida viene visualizzato una volta completata l'installazione dell'estensione. Richiede inoltre l'URL di un sito Web che consente di visualizzare la Guida.  
  
 **Ulteriori informazioni sull'URL**  
 Specifica l'URL di un sito Web che contiene informazioni aggiuntive sul prodotto.  
  
 Il **destinazioni di installazione** scheda contiene i seguenti controlli.  
  
 **Tipo di installazione**  
 Elenca **estensione di Visual Studio** e **SDK di estensione** come tipi di installazione di destinazione. Le opzioni variano a seconda del tipo scelto.  
  
 **Estensione di Visual Studio**  
 Elenca il **InstallationTarget** elementi che descrivono come il pacchetto può essere installato e in quali prodotti Visual Studio questa estensione può essere installata. Ogni prodotto viene identificato separatamente dal nome e una versione o intervallo.  Prodotti possono essere aggiunto all'elenco, modificare ed eliminati. Il nome e la versione di un prodotto corrispondono al **Id** e **versione** gli attributi dell'oggetto associato **InstallationTarget** elemento.  
  
 **Intervallo versione** è \[12.0, 14,0\] e viene utilizzata la notazione seguente:  
  
-   \[\-versione minima inclusiva  
  
-   \], versione massima inclusivo  
  
-   \(\-versione minima esclusiva  
  
-   \), versione massima esclusivo  
  
-   Versione unica \# \- solo la versione specificata  
  
 **SDK di estensione**  
 Specifica un'installazione globale che non hanno come ambita per un prodotto specifico e una versione.**Identificatore di piattaforma di destinazione** è la piattaforma, ad esempio "Windows", di destinazione.**Versione piattaforma di destinazione** è la versione, ad esempio 8.0, la piattaforma di destinazione.**Nome SDK** e **versione SDK** sono rispettivamente il nome e il numero di versione di SDK.  
  
 **VSIX questo viene installato per tutti gli utenti \(richiede l'elevazione dei privilegi durante l'installazione\)** casella di controllo  
 Se questa casella di controllo è selezionata, questa estensione è installata per tutti gli utenti. in caso contrario, installarlo solo per l'utente corrente.  
  
 **VSIX questo è installato Windows Installer** casella di controllo  
 Se questa casella di controllo è selezionata, questa estensione viene installata da Windows Installer \(file con estensione msi\). in caso contrario, viene installato come un pacchetto VSIX tipico \(file con estensione VSIX\).  
  
 Il **asset** scheda contiene i seguenti controlli.  
  
 **Elenco degli asset**  
 Elenca gli elementi di Asset che descrivono gli elementi di estensione o il contenuto da questo pacchetto superfici. Ogni estensione o un elemento di contenuto è elencato separatamente dall'origine, tipo e percorso. Elementi estensioni e il contenuto possono essere aggiunto all'elenco, modificare ed eliminati. Il tipo e il percorso di un elemento di estensione o il contenuto corrispondente per il `Type` e `Path` gli attributi dell'oggetto associato `Asset` elemento. I tipi seguenti sono noti:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Per aggiungere o modificare una risorsa, è necessario specificare il tipo di risorsa, se la risorsa è un progetto nella soluzione corrente o un file nel file system e il nome del progetto. È inoltre possibile specificare il nome della cartella in cui deve essere incorporato.  
  
 È anche possibile creare i propri tipi e assegnare loro nomi univoci.  
  
 Il **dipendenze** scheda contiene i seguenti controlli.  
  
 **Nome di origine e intervallo di versioni**  
 Elenca gli elementi di dipendenza di questo pacchetto, che sono altri pacchetti che dipende da questo pacchetto. Se viene specificato un pacchetto di dipendenze, deve essere installato prima di questo pacchetto viene installato; in caso contrario, questo pacchetto è necessario installarlo.  
  
 I pacchetti di dipendenza vengono specificati dall'identificatore, nome, versione intervallo, origine e come la dipendenza viene risolto. Ogni pacchetto di dipendenze è elencato separatamente dal nome, versione e origine. I pacchetti di dipendenza possono essere aggiunto all'elenco, modificare ed eliminati.  
  
 L'identificatore deve corrispondere il `ID` attributo dei metadati del pacchetto di dipendenza. L'origine può essere un progetto nella soluzione corrente, un'estensione attualmente installata o un file. Il **è la dipendenza viene risolta** impostazione può essere il percorso relativo di un pacchetto nidificato o l'URL del percorso di download per la dipendenza. L'ID, la versione e la risoluzione del pacchetto della dipendenza corrispondono al `Id`, `Version`, e `Location` gli attributi dell'oggetto associato `Dependency` elemento.  
  
## Vedere anche  
 [Riferimento dello Schema 2.0 estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)