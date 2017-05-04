---
title: "Interfaccia IDebugDocumentProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentProvider"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugDocumentProvider
Fornisce i mezzi per creare un'istanza di un documento su richiesta.  
  
## Note  
 Ciò significa indiretti per creare un'istanza di un documento:  
  
-   Consente di caricare il documento quando necessario.  
  
-   Consente l'oggetto documento da includere nell'IDE del debugger.  
  
-   Consente diversi modi per accedere allo stesso oggetto del documento.  
  
 Questa condizione separa il documento mediante il provider e consente al provider conterrà il runtime aggiuntive, informazioni sul contesto.  
  
 Oltre ai metodi ereditati da `IDebugDocumentInfo`, l'interfaccia `IDebugDocumentProvider` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Nel documento per poter creare un'istanza se non esiste già.|