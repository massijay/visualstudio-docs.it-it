---
title: "Procedura dettagliata: Utilizzo di un tasto di scelta rapida con un&#39;estensione di Editor | Microsoft Docs"
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
  - "editor [Visual Studio SDK], collegamento new - sequenze di tasti ai comandi"
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura dettagliata: Utilizzo di un tasto di scelta rapida con un&#39;estensione di Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile rispondere a tasti di scelta rapida nell'estensione di editor. La procedura riportata di seguito viene illustrato come aggiungere un'area di controllo di visualizzazione per una visualizzazione di testo utilizzando un tasto di scelta rapida. Questa procedura dettagliata è basata sul modello di riquadro di visualizzazione dell'area di controllo editor e consente di aggiungere l'area di controllo utilizzando il carattere \+.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un progetto Managed Extensibility Framework \(MEF\)  
  
1.  Creare un progetto VSIX in c\#. \(Nel **Nuovo progetto** finestra di dialogo, selezionare **Visual c\# \/ Extensibility**, quindi **progetto VSIX**.\) Denominare la soluzione `KeyBindingTest`.  
  
2.  Aggiungere un modello di elemento dell'area di controllo di Editor testo al progetto e denominarlo `KeyBindingTest`. Per altre informazioni, vedere [Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Aggiungere i riferimenti seguenti e impostare **CopyLocal** a `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 Nel file di classe KeyBindingTest, modificare il nome della classe per PurpleCornerBox. Utilizzare la lampadina visualizzata sul margine sinistro per apportare le opportune modifiche. All'interno del costruttore, modificare il nome del livello di area di controllo da **KeyBindingTest** a **PurpleCornerBox**:  
  
```c#  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## Definizione del filtro di comando  
 Il filtro dei comandi è un'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, che gestisce il comando creando un'area di controllo.  
  
1.  Aggiungere un file di classe e denominarla `KeyBindingCommandFilter`.  
  
2.  Aggiungere le istruzioni using seguenti.  
  
    ```c#  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  La classe denominata KeyBindingCommandFilter deve ereditare da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```c#  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Aggiungere campi privati per la visualizzazione di testo, il comando successivo nella catena di comando e un flag per rappresentare se è già stato aggiunto il filtro dei comandi.  
  
    ```c#  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Aggiungere un costruttore che imposta la visualizzazione di testo.  
  
    ```c#  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementare il `QueryStatus()` metodo come indicato di seguito.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementare il `Exec()` metodo in modo che venga aggiunta una casella viola alla visualizzazione, se un \+ carattere viene digitato.  
  
    ```c#  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## Aggiunta del filtro di comando  
 Il provider dell'area di controllo è necessario aggiungere un filtro per la visualizzazione di testo. In questo esempio, il provider implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> in ascolto di eventi di creazione di visualizzazione di testo. Questo provider dell'area di controllo Esporta anche il livello di area di controllo, che definisce l'ordine Z dell'area di controllo.  
  
1.  Nel file KeyBindingTestTextViewCreationListener, aggiungere le seguenti istruzioni using:  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  Nella definizione del livello dell'area di controllo, modificare il nome di AdornmentLayer da **KeyBindingTest** a **PurpleCornerBox**.  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Per ottenere l'adattatore di visualizzazione di testo, è necessario importare il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```c#  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Modifica di <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che si aggiunge il `KeyBindingCommandFilter`.  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  Il `AddCommandFilter` gestore ottiene l'adattatore di visualizzazione di testo e aggiunge il filtro dei comandi.  
  
    ```c#  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## Effettua l'area di controllo vengono visualizzati su ogni riga  
 L'area di controllo originale era presente in tutti i caratteri 'a' in un file di testo. Ora che abbiamo modificato il codice per aggiungere l'area di controllo in risposta al carattere "\+", viene aggiunto all'area di controllo solo per la riga in cui il "\+" è tipizzata. È possibile modificare il codice dell'area di controllo in modo che l'area di controllo ancora una volta visualizzato su ogni 'a'.  
  
 Nel file KeyBindingTest.cs, modificare il metodo CreateVisuals\(\) per scorrere tutte le righe nella vista per decorare il carattere 'a'.  
  
```c#  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Compilazione e testing del codice  
  
1.  Compilare la soluzione KeyBindingTest ed eseguirlo nell'istanza sperimentale.  
  
2.  Creare o aprire un file di testo. Digitare alcune parole contenenti il carattere 'a', quindi digitare \+ in un punto qualsiasi nella visualizzazione del testo.  
  
     Dovrebbe essere visualizzato un quadrato viola per ogni carattere 'a' nel file.