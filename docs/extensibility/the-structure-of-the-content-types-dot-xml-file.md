---
title: La struttura del File XML [Content_types] | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
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
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La struttura del File XML [Content_types]
Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Visual Studio utilizza il file XML [Content_Types] per installare il pacchetto senza installare il file stesso.  
  
> [!NOTE]
>  Sebbene in questo argomento si applica solo a [Content_Types]. XML file che vengono utilizzati nei pacchetti VSIX, il tipo di file [Content_Types]. XML è parte di *Open Packaging Conventions (OPC)* standard. Per ulteriori informazioni, vedere [OPC: un nuovo Standard per la creazione di pacchetti di dati](http://go.microsoft.com/fwlink/?LinkID=148207) sul sito Web MSDN.  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono l'elemento radice e i relativi attributi e gli elementi figlio.  
  
### <a name="root-element"></a>Elemento radice  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Types`|Contiene gli elementi figlio che enumera i tipi di file nel pacchetto VSIX.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Xmlns`|Obbligatorio. Il percorso dello schema utilizzato per il file con estensione XML [Content_Types].|  
  
### <a name="attribute-name-attribute"></a>Attributo {nome} Attributo  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|http://schemas.OpenFormats.org/package/2006/Content-Types|Il percorso dello schema di tipi di contenuto.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Il `Types` elemento può contenere un numero qualsiasi di `Default` elementi.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Default`|Descrive un tipo di contenuto nel pacchetto VSIX. Ogni tipo di file del pacchetto deve disporre del relativo `Default` elemento.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Extension`|L'estensione di un file nel pacchetto VSIX.|  
|`ContentType`|Descrive il tipo di contenuto che è associato con l'estensione del nome file.|  
  
### <a name="attribute-name-attribute"></a>Attributo {nome} Attributo  
 Visual Studio vengono riconosciuti i seguenti `ContentType` i valori per la proprietà associata `Extension` tipi.  
  
|Estensione|ContentType|  
|---------------|-----------------|  
|txt|testo|  
|pkgdef|testo|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o html|text/html|  
|formato RTF|applicazione/rtf|  
|PDF|Application/pdf|  
|GIF|image/gif|  
|jpg o jpeg|immagine/jpg|  
|TIFF|immagine/tiff|  
|vsix|applicazione/zip|  
|ZIP|applicazione/zip|  
|dll|application/octet-stream|  
|tutti gli altri tipi di file|application/octet-stream|  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 Il seguente file XML [Content_Types] viene descritto un pacchetto VSIX tipico.  
  
### <a name="code"></a>Codice  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Riferimento dello Schema 1.0 estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Un nuovo Standard per l'assemblaggio dei dati](http://go.microsoft.com/fwlink/?LinkID=148207)
