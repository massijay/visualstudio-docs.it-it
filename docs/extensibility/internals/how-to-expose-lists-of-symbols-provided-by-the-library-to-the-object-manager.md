---
title: Esporre gli elenchi di simboli forniti a Object Manager | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsSimpleLibrary2 interface, lists of symbols
- IVsLibrary2 interface, lists of symbols
- symbols, call browser
- lists, symbols for the object manager
- symbols, exposing lists to the object manager
ms.assetid: 19757068-bdaa-4e7e-85d6-f8ce5026a859
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15248c2ed4ebca289421576bc6d59776cb0d6298
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager"></a>Procedura: esporre elenchi dei simboli forniti dalla libreria per la gestione di oggetti
Gli strumenti di esplorazione simbolo **Visualizzazione classi**, **Visualizzatore oggetti**, **Visualizzatore chiamate** e **risultati ricerca simbolo**, il passaggio delle richieste per i nuovi dati il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di gestione degli oggetti. Gestione degli oggetti consente di trovare le librerie appropriate e richiede nuovi elenchi dei simboli. Le librerie di rispondono fornendo i dati richiesti per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestione degli oggetti tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di gestione degli oggetti chiama i metodi in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> l'interfaccia per ottenere i dati e viene utilizzato per compilare o aggiornare le visualizzazioni degli strumenti di esplorazione del simbolo.  
  
 Una libreria è possibile ricevere le richieste di dati quando viene richiamato lo strumento, viene espanso il nodo o all'aggiornamento della vista. Quando uno strumento di esplorazione simbolo viene richiamato per la prima volta, il gestore di oggetti richiede la libreria per fornire l'elenco di primo livello. Quando si espande un nodo di elenco, la libreria fornisce un elenco di elementi figlio di tale nodo. Ogni richiesta di gestione di oggetto contiene un indice dell'elemento di interesse. Per visualizzare un elenco di nuovo, il gestore di oggetti deve determinare il numero di elementi presenti nell'elenco, il tipo di elementi, i relativi nomi, accessibilità e altre proprietà.  
  
> [!NOTE]
>  Gli esempi di codice gestito seguenti illustrano come fornire gli elenchi di simboli tramite l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia. Object manager chiama i metodi in questa interfaccia e utilizza i dati ottenuti per inserire o aggiornare gli strumenti di esplorazione del simbolo.  
>   
>  Per l'implementazione di provider di codice nativo simbolo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfaccia.  
  
## <a name="providing-lists-of-symbols-to-the-object-manager"></a>Fornire gli elenchi di simboli per il gestore di oggetti  
  
#### <a name="to-provide-lists-of-symbols-to-the-object-manager"></a>Per fornire elenchi di simboli per la gestione degli oggetti  
  
1.  Ottenere il numero di elementi nell'elenco dei simboli implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metodo. Nell'esempio seguente viene illustrato il modo in cui il gestore oggetti Ottiene le informazioni sul numero di elementi nell'elenco.  
  
    ```vb  
    Protected m_Methods As System.Collections.Generic.SortedList(Of String, Method) = New System.Collections.Generic.SortedList(Of String, Method)()  
  
    Public Function GetItemCount(ByRef pCount As UInteger) As Integer  
        pCount = CUInt(m_Methods.Count)  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    protected System.Collections.Generic.SortedList<string, Method> m_Methods = new System.Collections.Generic.SortedList<string, Method>();  
  
    public int GetItemCount(out uint pCount)  
    {  
        pCount = (uint)m_Methods.Count;  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
2.  Ottenere informazioni sulle categorie di e gli attributi di un elemento di elenco specificato mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metodo. Le categorie di elementi vengono specificate nel <xref:Microsoft.VisualStudio.Shell.Interop.LIB_CATEGORY> enumerazione. Nell'esempio seguente viene illustrato il modo in cui il gestore oggetti Ottiene gli attributi degli elementi per una determinata categoria.  
  
    ```vb  
    Public Function GetCategoryField2(ByVal index As UInteger, ByVal Category As Integer, ByRef pfCatField As UInteger) As Integer  
        pfCatField = 0  
  
        Select Case CType(Category, LIB_CATEGORY)  
            Case LIB_CATEGORY.LC_MEMBERTYPE  
                pfCatField = CUInt(_LIBCAT_MEMBERTYPE.LCMT_METHOD)  
  
            Case LIB_CATEGORY.LC_MEMBERACCESS  
                Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
  
                If method.IsPublic Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PUBLIC)  
                ElseIf method.IsPrivate Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PRIVATE)  
                ElseIf method.IsFamily Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED)  
                ElseIf method.IsFamilyOrAssembly Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED) Or CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)  
                Else  
                    ' Show everything else as internal.  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)  
                End If  
  
            Case LIB_CATEGORY.LC_VISIBILITY  
                pfCatField = CUInt(_LIBCAT_VISIBILITY.LCV_VISIBLE)  
  
            Case LIB_CATEGORY.LC_LISTTYPE  
                pfCatField = CUInt(_LIB_LISTTYPE.LLT_MEMBERS)  
  
            Case Else  
                Return Microsoft.VisualStudio.VSConstants.S_FALSE  
        End Select  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int GetCategoryField2(uint index, int Category, out uint pfCatField)  
    {  
        pfCatField = 0;  
  
        switch ((LIB_CATEGORY)Category)  
        {  
            case LIB_CATEGORY.LC_MEMBERTYPE:  
                pfCatField = (uint)_LIBCAT_MEMBERTYPE.LCMT_METHOD;  
                break;  
  
            case LIB_CATEGORY.LC_MEMBERACCESS:  
                {  
                    Method method = m_Methods.Values[(int)index];  
  
                    if (method.IsPublic)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PUBLIC;  
                    }  
                    else if (method.IsPrivate)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PRIVATE;  
                    }  
                    else if (method.IsFamily)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED;  
                    }  
                    else if (method.IsFamilyOrAssembly)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED |  
                                     (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;  
                    }  
                    else  
                    {  
                        // Show everything else as internal.  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;  
                    }  
                }  
                break;  
  
            case LIB_CATEGORY.LC_VISIBILITY:  
                pfCatField = (uint)_LIBCAT_VISIBILITY.LCV_VISIBLE;  
                break;  
  
            case LIB_CATEGORY.LC_LISTTYPE:  
                pfCatField = (uint)_LIB_LISTTYPE.LLT_MEMBERS;  
                break;  
  
            default:  
                return Microsoft.VisualStudio.VSConstants.S_FALSE;  
        }  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
3.  Ottenere la rappresentazione testuale di un elemento di elenco specificato mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metodo. Nell'esempio seguente viene illustrato come ottenere un nome completo di un elemento specificato.  
  
    ```vb  
    Public Function GetTextWithOwnership(<System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")> ByVal index As UInteger, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")> ByVal tto As Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")> ByRef ppszText As String) As Integer  
        ppszText = m_Methods.Values(CInt(Fix(index))).FullName  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int GetTextWithOwnership([System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")] uint index, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")] Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS tto, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")] out string ppszText)  
    {  
        ppszText = m_Methods.Values[(int)index].FullName;  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
4.  Ottenere le informazioni sull'icona per un elemento di elenco specificato mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metodo. L'icona rappresenta il tipo (classe, metodo e così via) e l'accessibilità (privato, pubblico e così via) di un elemento elenco. Nell'esempio seguente viene illustrato come ottenere le informazioni sull'icona in base agli attributi di un elemento specificato.  
  
    ```vb  
    Public Overridable Function GetDisplayData(ByVal index As UInteger, ByVal pData As Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA()) As Integer  
        If pData Is Nothing Then  
            Return Microsoft.VisualStudio.VSConstants.E_INVALIDARG  
        End If  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
  
        Dim iImage As Integer = 12 * 6 ' See env\inc\OMGlyphs.h.  
  
        Const OM_GLYPH_ACC_PUBLIC As Integer = 0  
        Const OM_GLYPH_ACC_INTERNAL As Integer = 1  
        Const OM_GLYPH_ACC_PROTECTED As Integer = 3  
        Const OM_GLYPH_ACC_PRIVATE As Integer = 4  
  
        If method.IsPublic Then  
            iImage += OM_GLYPH_ACC_PUBLIC  
        ElseIf method.IsPrivate Then  
            iImage += OM_GLYPH_ACC_PRIVATE  
        ElseIf method.IsFamily Then  
            iImage += OM_GLYPH_ACC_PROTECTED  
        ElseIf method.IsFamilyOrAssembly Then  
            iImage += OM_GLYPH_ACC_PROTECTED  
        Else  
            iImage += OM_GLYPH_ACC_INTERNAL  
        End If  
  
        pData(0).Image = CUShort(iImage)  
        pData(0).SelectedImage = CUShort(iImage)  
  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public virtual int GetDisplayData(uint index, Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA[] pData)  
    {  
        if (pData == null)  
        {  
            return Microsoft.VisualStudio.VSConstants.E_INVALIDARG;  
        }  
  
        Method method = m_Methods.Values[(int)index];  
  
        int iImage = 12 * 6;    // See env\inc\OMGlyphs.h.  
  
        const int OM_GLYPH_ACC_PUBLIC = 0;  
        const int OM_GLYPH_ACC_INTERNAL = 1;  
        const int OM_GLYPH_ACC_PROTECTED = 3;  
        const int OM_GLYPH_ACC_PRIVATE = 4;  
  
        if (method.IsPublic)  
        {  
            iImage += OM_GLYPH_ACC_PUBLIC;  
        }  
        else if (method.IsPrivate)  
        {  
            iImage += OM_GLYPH_ACC_PRIVATE;  
        }  
        else if (method.IsFamily)  
        {  
            iImage += OM_GLYPH_ACC_PROTECTED;  
        }  
        else if (method.IsFamilyOrAssembly)  
        {  
            iImage += OM_GLYPH_ACC_PROTECTED;  
        }  
        else  
        {  
            iImage += OM_GLYPH_ACC_INTERNAL;  
        }  
  
        pData[0].Image = (ushort)iImage;  
        pData[0].SelectedImage = (ushort)iImage;  
  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
5.  Ottenere le informazioni sul fatto che un elemento di elenco specificato sia espandibile implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodo. Nell'esempio seguente viene illustrato come ottenere le informazioni su se è possibile espandere un elemento specificato.  
  
    ```vb  
    Public Function GetExpandable(ByVal index As UInteger, ByRef pfExpandable As Integer) As Integer  
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
  
    Public Function GetExpandable3(ByVal index As UInteger, ByVal ListTypeExcluded As UInteger, ByRef pfExpandable As Integer) As Integer  
        Return GetExpandable(index, pfExpandable)  
    End Function  
    ```  
  
    ```csharp  
    public int GetExpandable(uint index, out int pfExpandable)  
    {  
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE;  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    public int GetExpandable3(uint index, uint ListTypeExcluded, out int pfExpandable)  
    {  
        return GetExpandable(index, out pfExpandable);  
    }  
  
    ```  
  
6.  Ottenere un elenco di elementi figlio di simboli di un elemento di elenco specificato mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metodo. Nell'esempio seguente viene illustrato come ottenere un elenco di elementi figlio di simboli di un elemento specificato per **chiamare** o **chiamanti** grafici.  
  
    ```vb  
    ' Call graph list.  
    Public Class CallsList  
        Inherits ResultsList  
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
        Public Sub New(ByVal library As Library)  
            MyBase.New(library)  
        End Sub  
  
        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
            Return MyBase.GetCallsList(index, ppList)  
        End Function  
    End Class  
  
    ' Callers graph list.  
    Public Class CallersList  
        Inherits ResultsList  
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
        Public Sub New(ByVal library As Library)  
            MyBase.New(library)  
        End Sub  
  
        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
            Return MyBase.GetCallersList(index, ppList)  
        End Function  
    End Class  
  
    ' Call graph list.  
    Public Function GetCallsList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
        ppList = Nothing  
        Dim callsList As ResultsList = New CallsList(m_Library)  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
        Dim strMethod As String = method.m_strPrototype  
  
        Dim Calls As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallGraph(method)  
  
        For i As Integer = 0 To Calls.Count - 1  
            Dim caller As Method = Calls(i).m_Target  
            callsList.AddMethod(caller)  
        Next i  
  
        ppList = CType(callsList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
  
    ' Callers graph list.  
    Public Function GetCallersList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
        ppList = Nothing  
        Dim callersList As ResultsList = New CallersList(m_Library)  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
        Dim strMethod As String = method.m_strPrototype  
  
        Dim Callers As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallersGraph(method)  
  
        For i As Integer = 0 To Callers.Count - 1  
            Dim caller As Method = Callers(i).m_Source  
            callersList.AddMethod(caller)  
        Next i  
  
        ppList = CType(callersList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
  
    ' Get a child list of symbols for a given list item.  
    Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
        ppList = Nothing  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
        Dim strMethod As String = method.m_strPrototype  
  
        ' Determine if the list belongs to Call or Callers graphs.  
        If CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM)) > 0 Then  
            ' Build the list for the Call graph.  
            Return MyBase.GetCallsList(index, ppList)  
        ElseIf CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO)) > 0 Then  
            ' Build the list for the Callers graph.  
            Return MyBase.GetCallersList(index, ppList)  
        End If  
  
        Return Microsoft.VisualStudio.VSConstants.E_FAIL  
    End Function  
    ```  
  
    ```csharp  
    // Call graph list.  
    public class CallsList :  
        ResultsList,  
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
    {  
        public CallsList(Library library) :  
            base(library)  
        {  
        }  
  
        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
        {  
            return base.GetCallsList(index, out ppList);  
        }  
    }  
  
    // Callers graph list.  
    public class CallersList :  
        ResultsList,  
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
    {  
        public CallersList(Library library) :  
            base(library)  
        {  
        }  
  
        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
        {  
            return base.GetCallersList(index, out ppList);  
        }  
    }  
  
    // Call graph list.  
    public int GetCallsList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
    {  
        ppList = null;  
        ResultsList callsList = new CallsList(m_Library);  
  
        Method method = m_Methods.Values[(int)index];  
        string strMethod = method.m_strPrototype;  
  
        System.Collections.Generic.List<CallInstance> Calls = m_Library.CallGraph.GetCallGraph(method);  
  
        for (int i = 0; i < Calls.Count; i++)  
        {  
            Method caller = Calls[i].m_Target;  
            callsList.AddMethod(caller);  
        }  
  
        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callsList);  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    // Callers graph list.  
    public int GetCallersList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
    {  
        ppList = null;  
        ResultsList callersList = new CallersList(m_Library);  
  
        Method method = m_Methods.Values[(int)index];  
        string strMethod = method.m_strPrototype;  
  
        System.Collections.Generic.List<CallInstance> Callers = m_Library.CallGraph.GetCallersGraph(method);  
  
        for (int i = 0; i < Callers.Count; i++)  
        {  
            Method caller = Callers[i].m_Source;  
            callersList.AddMethod(caller);  
        }  
  
        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callersList);  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    // Get a child list of symbols for a given list item.  
    public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
    {  
        ppList = null;  
  
        Method method = m_Methods.Values[(int)index];  
        string strMethod = method.m_strPrototype;  
  
        // Determine if the list belongs to Call or Callers graphs.  
        if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM) > 0)  
        {  
            // Build the list for the Call graph.  
            return base.GetCallsList(index, out ppList);  
        }  
        else if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO) > 0)  
        {  
            // Build the list for the Callers graph.  
            return base.GetCallersList(index, out ppList);  
        }  
  
        return Microsoft.VisualStudio.VSConstants.E_FAIL;  
    }  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Procedura: registrare una libreria con il gestore oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)   
 [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)