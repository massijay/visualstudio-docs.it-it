---
title: "IDebugProgramNode2::GetHostName | Microsoft Docs"
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
  - "IDebugProgramNode2::GetHostName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetHostName"
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::GetHostName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il nome dell'hosting del programma.  
  
## Sintassi  
  
```cpp#  
HRESULT GetHostName (   
   GETHOSTNAME_TYPE dwHostNameType,  
   BSTR*            pbstrHostName  
);  
```  
  
```c#  
int GetHostName (   
   enum_GETHOSTNAME_TYPE dwHostNameType,  
   out string            pbstrHostName  
);  
```  
  
#### Parametri  
 `dwHostNameType`  
 \[in\]  Un valore [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) dell'enumerazione che specifica il tipo di nome per restituire.  
  
 `pbstrHostName`  
 \[out\]  Restituisce il nome del processo di hosting.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CProgram` che espone [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) l'interfaccia.  In questo esempio viene ignorato il parametro di `dwHostNameType` e restituisce solo il nome del programma come richiesto dal nome di base del percorso del file di modulo.  
  
```cpp#  
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {    
   // Check for valid argument.    
   if (pbstrHostName)    
   {    
      char szModule[_MAX_PATH];    
  
      // Attempt to assign to szModule the path for the file used  
      // to create the calling process.    
      if (GetModuleFileName(NULL, szModule, sizeof (szModule)))    
      {    
         // If successful then declare several char arrays    
         char  szDrive[_MAX_DRIVE];    
         char  szDir[_MAX_DIR];    
         char  szName[_MAX_FNAME];    
         char  szExt[_MAX_EXT];    
         char  szFilename[_MAX_FNAME + _MAX_EXT];    
         WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];    
  
         // Break the szModule path name into components.    
         _splitpath(szModule, szDrive, szDir, szName, szExt);    
  
         // Copy the base file name szName into szFilename.    
         lstrcpy(szFilename, szName);    
         // Append the field extension szExt into szFilename.    
         lstrcat(szFilename, szExt);    
  
         // Convert the szFilename sequence of multibyte characters    
         // to the wszFilename sequence of wide characters.    
         mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);    
  
         // Assign the wszFilename to the value at *pbstrHostName.    
         *pbstrHostName = SysAllocString(wszFilename);    
  
          return S_OK;    
      }    
   }    
  
    return E_INVALIDARG;    
}    
```  
  
## Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)