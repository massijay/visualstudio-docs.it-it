---
title: "Interfacce del Provider di simboli | Microsoft Docs"
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
  - "interfacce, gestore dei simboli"
  - "gestore dei simboli, le interfacce"
  - "gestore dei simboli, la valutazione di variabili"
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfacce del Provider di simboli
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Di seguito sono elencate le interfacce di gestione dei simboli per [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Descrizione  
 Queste interfacce vengono utilizzate per valutare le variabili in uno stack di chiamate in modalità di interruzione.  Vengono distribuiti solo per i provider del simbolo di Common Language \(SP\) Runtime.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|rappresenta l'indirizzo di un elemento.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Rappresenta l'indirizzo di un elemento, fornendo l'accesso a all'identificazione processo|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Rappresenta un simbolo o un tipo di matrice di matrici.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Rappresenta il simbolo della classe o il tipo della classe.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Rappresenta un provider del simbolo COM\+ con i metodi specifici del codice gestito.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Rappresenta un provider del simbolo COM\+ con i metodi specifici del codice gestito ed estende **il IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Rappresenta un simbolo o un tipo con un contenitore di altri simboli o tipi.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Rappresenta un attributo personalizzato che può essere collegato a un simbolo.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Rappresenta una query per gli attributi personalizzati in un metodo o un tipo.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Fornisce accesso agli attributi personalizzati in un simbolo.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|L'interfaccia di base per qualsiasi tipo che può essere determinato in fase di esecuzione.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|rappresenta un campo dinamico per [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) un oggetto.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|rappresenta un tipo di enumerazione.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Estende i tipi di campi disponibili finché i generics di codice gestito di supporto.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|La classe base per tutti i campi; rappresenta una descrizione di un simbolo o di un tipo.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|rappresenta la definizione di un campo per un tipo generico di codice gestito.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|rappresenta un'istanza di un campo per un tipo generico di codice gestito.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|rappresenta un parametro per un tipo generico di codice gestito.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|rappresenta un metodo.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|rappresenta un modificatore facoltativo di debug.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|rappresenta un puntatore.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Rappresenta un valore di enumerazione di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) tipo primitivo da un'interfaccia.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Rappresenta una proprietà di una classe di codice gestito che può essere ottiene o imposta.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Rappresenta un provider di simboli che fornisce i simboli e i tipi.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Rappresenta un provider del simbolo con accesso diretto ai metadati e supportano le interfacce del simbolo.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Rappresenta la possibilità di creare un campo che rappresenta un tipo.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Estende **il IDebugTypeFieldBuilder** per poter creare tipi di matrice.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Rappresenta una raccolta di oggetti [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md).|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Rappresenta una raccolta di oggetti [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md).|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Rappresenta una raccolta di oggetti [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).|  
  
## Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)