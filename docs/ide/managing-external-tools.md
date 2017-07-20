---
title: Gestire strumenti esterni | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 1d273749cc41eb975dc9f93329edf9a57aaae09a
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---
# Gestire strumenti esterni
<a id="manage-external-tools" class="xliff"></a>
È possibile chiamare strumenti esterni direttamente in Visual Studio usando il menu **Strumenti**. Alcuni strumenti predefiniti sono disponibili nel menu **Strumenti**, ma è possibile aggiungere altri file eseguibili personalizzati.  

## Strumenti disponibili nel menu Strumenti di Visual Studio
<a id="tools-available-on-the-visual-studio-tools-menu" class="xliff"></a>
 Il menu **Strumenti** include alcuni strumenti predefiniti, ad esempio:

*  **Estensioni e aggiornamenti** per la [gestione delle estensioni di Visual Studio](finding-and-using-visual-studio-extensions.md)
*  **Gestione frammenti di codice** per l'[organizzazione dei frammenti di codice](code-snippets.md#code-snippet-manager)
*  **PreEmptive Protection - Dotfuscator** per l'avvio di [Dotfuscator Community Edition (CE)](dotfuscator/index.md) se [installato](dotfuscator/install.md)
*  **Personalizza** per la [personalizzazione di menu e barre degli strumenti](how-to-customize-menus-and-toolbars-in-visual-studio.md)
*  **Opzioni** per l'[impostazione di un'ampia gamma di opzioni per l'IDE di Visual Studio e altri strumenti](reference/options-dialog-box-visual-studio.md)

## Aggiungere nuovi strumenti al menu Strumenti
<a id="add-new-tools-to-the-tools-menu" class="xliff"></a> 
 È possibile aggiungere uno strumento esterno al menu **Strumenti**. Aprire la finestra di dialogo **Strumenti esterni**, fare clic su **Aggiungi** e quindi specificare le informazioni. L'immissione seguente consente ad esempio di aprire la cartella dove si trova il file attualmente aperto in Visual Studio:  
  
1.  Titolo: *Apri percorso file*
  
2.  Comando: `explorer.exe`  
  
3.  Argomenti: `/root, "$(ItemDir)"`  
  
 Di seguito è riportato un elenco completo di argomenti che può essere usato quando si definisce uno strumento esterno.
  
> [!NOTE]
>  La barra di stato dell'IDE visualizza le variabili di Riga corrente e Colonna corrente per indicare dove si trova il punto di inserimento nell'Editor codice attivo. La variabile di Testo corrente restituisce il testo o codice selezionato in quella posizione.  
  
|Nome|Argomento|Descrizione|  
|----------|--------------|-----------------|  
|Percorso elemento|$(ItemPath)|Nome file completo del file corrente (unità + percorso + nome file).|  
|Directory elemento|$(ItemDir)|Directory del file corrente (unità + percorso).|  
|Nome file elemento|$(ItemFilename)|Nome del file corrente (nome file).|  
|Estensione di elemento|$(ItemExt)|Estensione del nome del file corrente.|  
|Riga corrente|$(CurLine)|Posizione della riga corrente del cursore nella finestra del codice.|  
|Colonna corrente|$(CurCol)|Posizione della colonna corrente del cursore nella finestra del codice.|  
|Testo corrente|$(CurText)|Testo selezionato.|  
|Percorso di destinazione|$(TargetPath)|Nome file completo dell'elemento da compilare (unità + percorso + nome file).|  
|Target Directory|$(TargetDir)|Directory dell'elemento da compilare.|  
|Target Name|$(TargetName)|Nome file dell'elemento da compilare.|  
|Estensione di destinazione|$(TargetExt)|Estensione di file dell'elemento da compilare.|  
|Directory binaria|$(BinDir)|Posizione finale del file binario in fase di compilazione (definita come unità + percorso). Ad esempio: **\\...\Documenti\Visual Studio \<Versione>\\<NomeProgetto\>\bin\debug**|  
|Directory del progetto|$(ProjDir)|Directory del progetto corrente (unità + percorso).|  
|Nome del file di progetto|$(ProjFileName)|Nome file del progetto corrente (unità + percorso + nome file).|  
|Directory soluzione|$(SolutionDir)|Directory della soluzione corrente (unità + percorso).|  
|Nome file della soluzione|$(SolutionFileName)|Nome file della soluzione corrente (unità + percorso + nome file).|  

## Vedere anche
<a id="see-also" class="xliff"></a>  
 [Strumenti per la compilazione in C/C++](/cpp/build/reference/c-cpp-build-tools)

