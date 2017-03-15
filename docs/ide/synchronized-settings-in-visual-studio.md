---
title: Sincronizzare le impostazioni in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: 4166ed8bfa0234e1cc453bd045974b412f87ae42
ms.openlocfilehash: a1a310aa6bf0e3d0042f35f5c49612f33b89fb61
ms.lasthandoff: 02/22/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>Sincronizzare le impostazioni in Visual Studio
Quando si usa lo stesso account di personalizzazione per accedere a Visual Studio Online da più computer, per impostazione predefinita le impostazioni vengono sincronizzate in tutti i computer.

## <a name="synchronized-settings"></a>Impostazioni sincronizzate  
 Per impostazione predefinita, vengono sincronizzate le impostazioni seguenti.  

-   Impostazioni di sviluppo. È necessario selezionare un set di impostazioni la prima volta che si esegue Visual Studio, ma è possibile modificare la selezione in qualsiasi momento. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  

-   Le opzioni seguenti nelle pagine **Strumenti &#124; Opzioni**:  

    -   Impostazioni del **tema** e di maiuscole e minuscole nella barra dei menu nella pagina delle opzioni **Ambiente**, **Generale**  

    -   Tutte le impostazioni nella pagina delle opzioni **Ambiente**, **Tipi di carattere e colori**  

    -   Tutti i tasti di scelta rapida nella pagina delle opzioni **Ambiente**, **Tastiera**  

    -   Tutte le impostazioni nella pagina delle opzioni **Ambiente, Schede e Finestre**  

    -   Tutte le impostazioni nella pagina delle opzioni **Ambiente**, **Avvio**  

    -   Tutte le impostazioni nelle pagine delle opzioni **Editor di testo**  

-   Tutte le impostazioni nelle pagine delle opzioni di XAML Designer  

-   Alias di comandi definiti dall'utente. Per altre informazioni su come definire gli alias di comandi, vedere [Alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).  

-   I layout delle finestre definite dall'utente nella pagina **Finestra &#124; Gestisci layout finestra**  

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Disattivare le impostazioni sincronizzate per un computer specifico  
 Le impostazioni sincronizzate per Visual Studio sono attivate per impostazione predefinita. È possibile disattivare le impostazioni sincronizzate in un computer visitando la pagina **Strumenti &#124; Opzioni &#124; Ambiente&#124; Impostazioni sincronizzate** e deselezionando la casella di controllo.  Se, ad esempio, si decide di non sincronizzare le impostazioni di Visual Studio nel computer A, nessuna delle modifiche alle impostazioni del computer A verrà visualizzata nel computer B o nel computer C. I computer B e C continueranno a sincronizzarsi tra di loro, ma non si sincronizzeranno con il computer A.  

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizzare le impostazioni tra prodotti e edizioni della famiglia Visual Studio  
 Le impostazioni possono essere sincronizzate tra tutte le edizioni di Visual Studio, compresa l'edizione Community. Le impostazioni vengono sincronizzate anche tra prodotti della famiglia Visual Studio. Tuttavia, ogni prodotto di questa famiglia potrebbe disporre di impostazioni personalizzate che non vengono condivise con Visual Studio. Ad esempio, impostazioni specifiche di un prodotto nel computer A verranno condivise con un altro prodotto nel computer B, ma non con Visual Studio nel computer A o B.  

## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dell'IDE](../ide/personalizing-the-visual-studio-ide.md)

