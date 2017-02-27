---
title: "Aggiunta di icone ai comandi di Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "icone [Visual Studio], aggiunta di barre degli strumenti"
  - "aggiunta di icone ai comandi di barre degli strumenti [Visual Studio]"
  - "comandi [Visual Studio], aggiunta di icone"
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Aggiunta di icone ai comandi di Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I comandi possono essere visualizzati in entrambi i menu e barre degli strumenti. Sulla barra degli strumenti, è comune per un comando da visualizzare solo un'icona \(per risparmiare spazio\) durante il menu visualizzato in genere un comando con un'icona e testo.  
  
 Le icone sono di 16 pixel di larghezza e 16 pixel di altezza e possono essere profondità di colore a 8 bit \(256 colori\) o profondità di colore a 32 bit \(colore true\). le icone di colore a 32 bit vengono preferite. Le icone vengono disposte in genere in una singola riga orizzontale in una singola bitmap, anche se sono consentite più immagini bitmap. Questa bitmap viene dichiarata nel file vsct insieme le singole icone disponibili nella bitmap. Vedere la documentazione per il [Elemento di bitmap](../extensibility/bitmaps-element.md) Per ulteriori dettagli.  
  
## Aggiunta di un'icona a un comando  
 La procedura seguente si presuppone che si dispone di un progetto VSPackage esistente con un comando di menu. Per scoprire come eseguire questa operazione, vedere [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Creare una bitmap con una profondità di colore pari a 32 bit. Un'icona è sempre 16 x 16 questa bitmap deve pertanto essere 16 pixel di altezza e multipli di 16 pixel di larghezza.  
  
     Ogni icona è posizionato sulla bitmap uno accanto a altro in una singola riga. Utilizzare il canale alfa per indicare punti di trasparenza in ciascuna icona.  
  
     Se si utilizza una profondità di colore a 8 bit, utilizzare magenta, `RGB(255,0,255)`, come la trasparenza. Tuttavia, le icone di colore a 32 bit sono preferite.  
  
2.  Copiare il file di icona directory delle risorse nel progetto VSPackage. In Esplora soluzioni, aggiungere l'icona per il progetto. \(Selezione di risorse e menu di scelta rapida scegliere Aggiungi, quindi elemento esistente e selezionare il file di icona.\)  
  
3.  Aprire il file vsct nell'editor.  
  
4.  Aggiungere un `GuidSymbol` elemento con un nome di **testIcon**. Creare un GUID \(**Strumenti \/ creare GUID**, quindi selezionare **il formato del Registro di sistema** e scegliere Copia\) e incollarlo il `value` attributo. Il risultato dovrebbe essere simile al seguente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Aggiungere un `<IDSymbol>` per l'icona. Il `name` attributo è l'ID dell'icona e `value` indica la relativa posizione nell'elenco, se presente. Se è presente solo un'icona, aggiungere 1. Il risultato dovrebbe essere simile al seguente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Creare un `<Bitmap>` nel `<Bitmaps>` sezione del file vsct per rappresentare la bitmap contenente le icone.  
  
    -   Impostare il `guid` al nome del valore il `<GuidSymbol>` elemento è stato creato nel passaggio precedente.  
  
    -   Impostare il `href` valore per il percorso relativo del file bitmap \(in questo caso **risorse \< nome del file icona \>**.  
  
    -   Impostare il `usedList` valore per il IDSymbol creato in precedenza. Questo attributo specifica un elenco delimitato da virgole delle icone da utilizzare in VSPackage. Le icone non inclusi nell'elenco sono esclusi modulo compilazione.  
  
         Il blocco di Bitmap dovrebbe essere simile al seguente:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Esistente `<Button>` elemento, impostare il `Icon` elemento ai valori GUIDSymbol e IDSymbol creato in precedenza. Di seguito è riportato un esempio di un elemento pulsante con i valori:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Verificare l'icona. Compilare il progetto e avviare il debug. Nell'istanza sperimentale, trovare il comando. Dovrebbe venire visualizzata l'icona che è stato aggiunto.  
  
## Vedere anche  
 [Estensione menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Riferimento allo Schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)