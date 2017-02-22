---
title: "DisassemblyData | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisassemblyData"
helpviewer_keywords: 
  - "Struttura DisassemblyData"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritto il un'istruzione disassembly per l'ambiente di sviluppo integrato \(IDE\) \(IDE\) da visualizzare.  
  
## Sintassi  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```c#  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## Membri  
 `dwFields`  
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) La costante che specifica quali campi vengono compilati.  
  
 `bstrAddress`  
 L'indirizzo come offset rispetto a un certo punto iniziale \(in genere l'inizio della funzione associata\).  
  
 `bstrCodeBytes`  
 I byte del codice per questa istruzione.  
  
 `bstrOpcode`  
 il codice operativo per questa istruzione.  
  
 `bstrOperands`  
 gli operandi per questa istruzione.  
  
 `bstrSymbol`  
 Il nome del simbolo, se presente, associato all'indirizzo \(simbolo, etichetta pubblici, e così via\).  
  
 `uCodeLocationId`  
 L'identificatore posizione del codice per questa riga smontata.  Se l'indirizzo del contesto di codice di una linea è superiore dell'oggetto di contesto di codice di un altro, è l'identificatore smontato posizione del codice del primo sarà maggiore dell'identificatore posizione del codice del secondo.  
  
 `posBeg`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Che corrisponde alla posizione in un documento in cui i dati del disassembly iniziano.  
  
 `posEnd`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Che corrisponde alla posizione in un documento in cui i dati del disassembly terminano.  
  
 `bstrDocumentUrl`  
 Per documenti di testo che possono essere rappresentati come nomi file, il campo di `bstrDocumentUrl` viene riempito con un nome file in cui l'origine può essere trovato, utilizzando il formato `nome di file://file`.  
  
 Per documenti di testo che non possono essere rappresentati come nomi file, `bstrDocumentUrl` è un identificatore univoco per il documento e il motore di debug deve implementare [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) il metodo.  
  
 Questo campo può inoltre contenere informazioni aggiuntive sui checksum.  Vedere le note per i dettagli.  
  
 `dwByteOffset`  
 Il numero di byte l'istruzione è dall'inizio della riga di codice.  
  
 `dwFlags`  
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) La costante che specifica i flag sono attivi.  
  
## Note  
 Ogni struttura di `DisassemblyData` viene descritto il un'istruzione disassembly.  Una matrice di queste strutture viene [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) restituito dal metodo.  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) La struttura viene utilizzata per i documenti basati su testo.  L'intervallo di codice sorgente per questa istruzione è specificato solo per la prima istruzione generata da un'istruzione o da una riga, ad esempio, quando `dwByteOffset == 0`.  
  
 Per i documenti non testuali, un contesto del documento può essere ottenuto dal codice e il campo di `bstrDocumentUrl` deve essere un valore null.  Se il campo di `bstrDocumentUrl` corrisponde al campo di `bstrDocumentUrl` nell'elemento di matrice precedente di `DisassemblyData` , quindi impostare `bstrDocumentUrl` a un valore null.  
  
 Se il campo di `dwFlags` include il flag di `DF_DOCUMENT_CHECKSUM` impostato su, le informazioni aggiuntive di checksum seguono la stringa indicata dal campo di `bstrDocumentUrl` .  In particolare, dopo il carattere di terminazione di stringa null, è riportato un GUID che identifica l'algoritmo di checksum che a sua volta è seguito da un valore a 4 byte che indica il numero di byte nel checksum e che a sua volta è seguito dai byte di checksum.  Vedere l'esempio riportato in questo argomento sulla codifica e decodifica questo campo in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
## Esempio  
 Il campo di `bstrDocumentUrl` può contenere le informazioni aggiuntive diverso da una stringa se il flag di `DF_DOCUMENT_CHECKSUM` è impostato.  Il processo di creazione e di lettura di questa stringa codificata è chiaro in [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)].  Tuttavia, in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], è un'altra questione.  Per coloro che è curioso, nell'esempio seguente viene illustrato un modo per creare la stringa codificata da [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] e una modalità decodificare la stringa codificata in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
```c#  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)