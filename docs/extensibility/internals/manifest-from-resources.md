---
title: "Manifesto delle risorse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Manifesto delle risorse
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il manifesto dallo strumento di risorse è un'applicazione console che accetta un elenco di risorse immagine \(file con estensione PNG o con estensione XAML\) e genera un file .imagemanifest che consente le immagini da utilizzare con il servizio di immagini di Visual Studio. Inoltre, questo strumento consente di aggiungere immagini a un .imagemanifest esistente. Questo strumento è utile per aggiungere il supporto ad alta risoluzione e i temi per le immagini a un'estensione di Visual Studio. Il file .imagemanifest generato deve essere incluso in e distribuito come parte di un'estensione di Visual Studio \(VSIX\).  
  
## Procedura: utilizzare lo strumento  
 **Sintassi**  
  
 ManifestFromResources \/risorse: \< Dir1 \>; \< Img1 \> \/assembly: \< AssemblyName \>\< Args facoltativo \>  
  
 **Argomenti**  
  
||||  
|-|-|-|  
|**Nome del commutatore**|**Note**|**Obbligatorio o facoltativo**|  
|\/risorse|Un elenco delimitato da punto e virgola di immagini o directory. Questo elenco deve contenere sempre l'elenco completo delle immagini che si trova il manifesto. Se viene fornito un elenco parziale, solo le voci non incluse andranno perse.<br /><br /> Se un file di risorse specificato è un elenco immagini, lo strumento verrà dividerla in immagini distinte prima di aggiungere ogni immagine secondaria per il manifesto.<br /><br /> Se l'immagine è un file con estensione png, è consigliabile formattare il nome simile al seguente in modo che lo strumento può inserire i giusti attributi per l'immagine: \< nome \>. \< larghezza \>. \< altezza \> PNG.|Obbligatorio|  
|\/assembly|Il nome dell'assembly gestiti \(senza includere l'estensione\) o il percorso di runtime dell'assembly nativo che ospita le risorse \(relativo alla posizione di runtime del manifesto\).|Obbligatorio|  
|\/manifest|Nome da assegnare al file .imagemanifest generato. Può inoltre includere un percorso assoluto o relativo per creare il file in una posizione diversa. Il nome predefinito corrisponde al nome di assembly.<br /><br /> Valore predefinito: \< Directory corrente \> \\ .imagemanifest \< Assembly \>|Facoltativo|  
|\/guidName|Il nome da assegnare al simbolo GUID per tutte le immagini nel manifesto generato.<br /><br /> Predefinito: AssetsGuid|Facoltativo|  
|\/rootPath|Il percorso radice che devono essere rimossi prima di creare gli URI di risorsa gestita. \(Questo flag è di risolvere i casi in cui lo strumento Ottiene il percorso URI relativo errato, causando risorse caricamento\).<br /><br /> Valore predefinito: \< Directory corrente \>|Facoltativo|  
|\/Recursive|L'impostazione di questo flag indica che lo strumento in modo ricorsivo tutte le directory di ricerca nell'argomento \/Resources.. L'omissione di questo flag comporterà una ricerca top\-livello solo delle directory.|Facoltativo|  
|\/isNative|Impostare questo flag quando l'argomento di assembly è un percorso per un assembly nativo. Omettere questo flag quando l'argomento di assembly è il nome di un assembly gestito. \(Vedere la sezione Note per ulteriori informazioni su questo flag\).|Facoltativo|  
|\/newGuids|L'impostazione di questo flag indica che lo strumento per creare un nuovo valore per il simbolo GUID le immagini anziché nel manifesto esistente con quello di unione.|Facoltativo|  
|\/newIds|L'impostazione di questo flag indica che lo strumento per creare nuovi valori di simbolo ID per ogni immagine invece di unione di valori dal manifesto esistente.|Facoltativo|  
|\/noLogo|L'impostazione di questo flag interrompe prodotto e informazioni sul copyright di stampare le informazioni.|Facoltativo|  
|\/?|Stampare le informazioni della Guida.|Facoltativo|  
|\/help|Stampare le informazioni della Guida.|Facoltativo|  
  
 **Esempi**  
  
-   ManifestFromResources \/resources:D:\\Images \/assembly:My.Assembly.Name \/isNative  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/guidName:MyImages \/newGuids \/newIds  
  
## Note  
  
-   Lo strumento supporta solo file con estensione XAML e PNG. Qualsiasi altro tipo di immagine o file verrà ignorato. Viene generato un avviso per tutti i tipi non supportati durante l'analisi delle risorse. Se non supportata immagini disponibili al termine dello strumento di analisi delle risorse, verrà generato un errore  
  
-   Seguendo il formato consigliato per le immagini PNG, lo strumento imposterà il valore di dimensione\/per il PNG per le dimensioni di formato specificato, anche se differisce dalla dimensione effettiva dell'immagine.  
  
-   Il formato larghezza\/altezza può essere omesso per le immagini PNG, ma lo strumento leggerà larghezza\/altezza effettive dell'immagine e usarle per valore o dimensione dell'immagine.  
  
-   Eseguire questo strumento nella stessa sequenza più volte per la stessa .imagemanifest comporterà voci duplicate del manifesto, poiché lo strumento tenta di suddividere l'elenco di immagini in immagini autonomo e aggiungerlo al manifesto esistente.  
  
-   Unione \(omettendo \/newGuids o \/newIds\) deve essere effettuata solo per i manifesti generati dallo strumento. Manifesti che sono stati personalizzati o generati tramite altri mezzi potrebbero non essere uniti correttamente.  
  
-   Manifesti generati per assembly nativo debba essere modificato manualmente dopo la generazione di uniformare i simboli di ID della risorsa ID file RC dell'assembly nativo.  
  
## Esempio di output  
 **Manifesto immagine semplice**  
  
 Un manifesto dell'immagine sarà simile a questo file XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImage" Value="0" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage)"> <Source Uri="$(Resources)/Xaml/MyImage.xaml" /> <Source Uri="$(Resources)/Png/MyImage.16.16.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```  
  
 **Manifesto immagine per un elenco di immagini**  
  
 Manifesto per un'immagine per un elenco immagini sarà simile a questo file XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImageStrip_0" Value="1" /> <ID Name="MyImageStrip_1" Value="2" /> <ID Name="MyImageStrip" Value="3" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)"> <Source Uri="$(Resources)/MyImageStrip_0.png"> <Size Value="16" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)"> <Source Uri="$(Resources)/MyImageStrip_1.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists> <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)"> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" /> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" /> </ImageList> </ImageLists> </ImageManifest>  
```  
  
 **Manifesto di immagini per le risorse immagine nativa**  
  
 Un manifesto dell'immagine per le immagini native sarà simile a questo file XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15198 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" /> <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" /> <ID Name="MyImage1" Value="0" /> <ID Name="MyImage2" Value="1" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage1)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage1)" Type="PNG" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImage2)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage2)" Type="PNG" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```