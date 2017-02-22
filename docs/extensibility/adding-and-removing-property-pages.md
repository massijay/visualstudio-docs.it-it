---
title: "Aggiunta e rimozione di pagine delle propriet&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pagine delle proprietà, aggiunta"
  - "pagine delle proprietà, sottotipi di progetto"
  - "pagine delle proprietà, rimozione"
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Aggiunta e rimozione di pagine delle propriet&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Progettazione progetti fornisce una posizione centralizzata per la gestione delle proprietà, le impostazioni e le risorse in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Viene visualizzata come una sola finestra nell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e contiene una serie di riquadri a destra a cui si accede mediante le schede a sinistra.  I riquadri \(a cui spesso come pagine delle proprietà\) in progettazione progetti variano in base al tipo di progetto e al linguaggio.  Progettazione progetti è possibile accedere al comando di **Proprietà** scegliere dal menu di **Progetto** .  
  
 Un sottotipo di progetto necessita spesso visualizza le pagine delle proprietà aggiuntive in progettazione progetti.  Inoltre, i sottotipi di progetto potrebbero richiedere che le pagine delle proprietà incorporate sono state rimosse.  Per eseguire uno, il sottotipo di progetto deve implementare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ed eseguire l'override del metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> .  Eseguendo l'override di questo metodo e utilizzando il parametro di `propId` contenente uno dei valori di enumerazione di <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> , è possibile filtrare, aggiungere o rimuovere le proprietà del progetto.  Ad esempio, potrebbe essere necessario aggiungere una pagina alle pagine delle proprietà dipendenti dalla configurazione.  A tale scopo, è necessario filtrare le pagine delle proprietà di distribuzione e quindi aggiungere una nuova pagina all'elenco esistente.  
  
## Aggiunta e rimozione delle pagine delle proprietà in progettazione progetti  
  
#### Per rimuovere una pagina delle proprietà in progettazione progetti  
  
1.  Eseguire l'override del metodo di `GetProperty(uint itemId, int propId, out object property)` alle pagine delle proprietà filter e ottenere un elenco di `clsids` .  
  
    ```vb#  
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-independent property pages.  
        Select Case propId  
            ....   
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))  
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)  
                'Remove the property page here  
                   ....  
            ....  
        End Select  
            ....   
        Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
  
    ```  
  
    ```c#  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-independent property pages.  
        switch (propId)  
        {  
            . . . .  
  
            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);  
                    //Remove the property page here  
                    . . . .  
                }  
             . . . .  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
2.  Rimuovere la pagina di **eventi di compilazione** ottenuto dall'elenco di `clsids` .  
  
    ```vb#  
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"  
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)  
    If index <> -1 Then  
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1  
        If index2 >= propertyPagesList.Length Then  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)  
        Else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)  
        End If  
    End If  
    'New property value  
    property = propertyPagesList  
    ```  
  
    ```c#  
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";  
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);  
    if (index != -1)  
    {  
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        int index2 = index + buildEventsPageGuid.Length + 1;  
        if (index2 >= propertyPagesList.Length)  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');  
        else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);  
    }  
    //New property value  
    property = propertyPagesList;  
    ```  
  
#### Per aggiungere una pagina delle proprietà in progettazione progetti  
  
1.  Creare una pagina delle proprietà che si desidera aggiungere.  
  
    ```vb#  
    Class DeployPropertyPage  
            Inherits Form  
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
        'Summary: Return a stucture describing your property page.  
        ....   
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())  
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()  
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))  
            info.dwHelpContext = 0  
            info.pszDocString = Nothing  
            info.pszHelpFile = Nothing  
            info.pszTitle = "Deployment" 'Assign tab name  
            info.SIZE.cx = Me.Size.Width  
            info.SIZE.cy = Me.Size.Height  
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then  
                pPageInfo(0) = info  
            End If  
        End Sub  
    End Class  
    ```  
  
    ```c#  
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
    {  
        . . . .   
        //Summary: Return a stucture describing your property page.  
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)  
        {  
            PROPPAGEINFO info = new PROPPAGEINFO();  
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));  
            info.dwHelpContext = 0;  
            info.pszDocString = null;  
            info.pszHelpFile = null;  
            info.pszTitle = "Deployment";  //Assign tab name  
            info.SIZE.cx = this.Size.Width;  
            info.SIZE.cy = this.Size.Height;  
            if (pPageInfo != null && pPageInfo.Length > 0)  
                pPageInfo[0] = info;  
        }  
    }  
    ```  
  
2.  Registrare la nuova pagina delle proprietà.  
  
    ```vb#  
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>  
    ```  
  
    ```c#  
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]  
    ```  
  
3.  Eseguire l'override del metodo di `GetProperty(uint itemId, int propId, out object property)` alle pagine delle proprietà filter, ottenere un elenco di `clsids` e aggiungere una nuova pagina delle proprietà.  
  
    ```vb#  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-dependent property pages.  
        Select Case propId  
            ....   
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):  
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                'Add the Deployment property page.  
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")  
        End Select  
            ....   
            Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
    ```  
  
    ```c#  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-dependent property pages.  
        switch (propId)  
        {  
            . . . .  
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    //Add the Deployment property page.  
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");  
                }  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
> [!NOTE]
>  Tutti gli esempi di codice forniti in questo argomento fanno parte di un esempio più esaustivo [Esempi di VSSDK](../misc/vssdk-samples.md).  
  
## Vedere anche  
 [Progetto \(sottotipi\)](../extensibility/internals/project-subtypes.md)