---
title: "Procedura dettagliata: Collegamento di un tipo di contenuto a un&#39;estensione nome File | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], collegamento new - tipo di contenuto per estensione di file"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura dettagliata: Collegamento di un tipo di contenuto a un&#39;estensione nome File
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile definire il tipo di contenuto e collegare un'estensione nome file con estensioni dell'editor Managed Extensibility Framework \(MEF\). In alcuni casi, l'estensione del nome file è già stato definito da un servizio di linguaggio. Tuttavia, per utilizzarlo con MEF è comunque necessario collegarlo a un tipo di contenuto.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un progetto MEF  
  
1.  Creare un progetto VSIX in c\#. \(Nel **Nuovo progetto** finestra di dialogo, selezionare **Visual c\# \/ Extensibility**, quindi **progetto VSIX**.\) Denominare la soluzione `ContentTypeTest`.  
  
2.  Nel **source.extension.vsixmanifest** file, andare alla **asset** scheda e impostare il **tipo** campo **Microsoft.VisualStudio.MefComponent**, il **origine** campo **un progetto nella soluzione corrente**, e **progetto** campo il nome del progetto.  
  
## Definizione del tipo di contenuto  
  
1.  Aggiungere un file di classe e denominarla `FileAndContentTypes`.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Aggiungere il codice seguente `using` direttive.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Dichiarare una classe statica che contiene le definizioni.  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Questa classe, esportare un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominato "nascoste" e dichiarare la definizione di base di "text".  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## Collegamento di un'estensione a un tipo di contenuto  
  
-   Per eseguire il mapping di questo tipo di contenuto per un'estensione nome file, esportare un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> che ha l'estensione "HID" e il tipo di contenuto "nascoste".  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## Aggiungere il tipo di contenuto per un'esportazione di Editor  
  
1.  Creare un'estensione di editor. Ad esempio, è possibile utilizzare l'estensione del glifo margine descritto in [Procedura dettagliata: Creazione di un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Aggiungere la classe che è definita in questa procedura.  
  
3.  Quando si esporta la classe di estensione, aggiungere un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di tipo "nascosta" a esso.  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## Vedere anche  
 [Servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)