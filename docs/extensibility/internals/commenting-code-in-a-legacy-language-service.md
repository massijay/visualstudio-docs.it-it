---
title: "Commenti di codice in un servizio di linguaggio Legacy | Microsoft Docs"
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
  - "commenti, supporto in servizi di linguaggio [framework pacchetto gestito]"
  - "servizi di linguaggio [framework gestito pacchetto], commenti nel codice"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Commenti di codice in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

I linguaggi di programmazione in genere forniscono un mezzo per annotare o impostarlo come commento il codice.  Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice ma verrà ignorato durante la compilazione o l'interpretazione.  
  
 Le classi gestite del framework \(MPF\) del pacchetto forniscono supporto per il commento e rimuovere il commento dal testo selezionato.  
  
## stili di commento  
 Esistono due stili generali del commento:  
  
1.  Allineare i commenti, dove il commento viene su una sola riga.  
  
2.  Bloccare i commenti, dove il commento può comprendere più righe.  
  
 I commenti della riga in genere un carattere iniziale \(o caratteri, mentre le osservazioni di blocco sono entrambi i caratteri iniziale e finale.  In c, ad esempio, un commento la riga inizia con \/\/e l'avvio di un commento di blocco con\/\* e termina con \*\/.  
  
 Quando l'utente seleziona il comando **selezione di commento** da **Modifica** \- il menu di \> **Avanzate** , il comando viene indirizzato al metodo di <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> sulla classe di <xref:Microsoft.VisualStudio.Package.Source> .  Quando l'utente seleziona il comando **Rimuovere il commento dalla selezione**, il comando viene indirizzato al metodo di <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> .  
  
## Commenti del codice di supporto  
 È possibile disporre i commenti del codice di supporto del servizio di linguaggio per utilizzare il parametro denominato di `EnableCommenting` di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .  Questo imposta la proprietà di <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> della classe di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  Per ulteriori informazioni sulle funzionalità di servicce di linguaggio impostazione, vedere [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
 È inoltre necessario eseguire l'override del metodo di <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> per restituire una struttura di <xref:Microsoft.VisualStudio.Package.CommentInfo> con i caratteri di commento per il linguaggio.  i caratteri stile c\# di commento la riga è l'impostazione predefinita.  
  
### Esempio  
 Di seguito è un'implementazione di esempio del metodo di <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> .  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)