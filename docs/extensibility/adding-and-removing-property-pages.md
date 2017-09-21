---
title: "加入和移除屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性頁中加入"
  - "屬性頁中的專案子類型"
  - "屬性頁中移除"
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 加入和移除屬性頁
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

專案設計工具提供集中的位置，來管理專案屬性、 設定和資源在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  它會以單一視窗中出現[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合開發環境 \(IDE\)，並包含在右邊窗格，可以透過左邊的索引標籤存取的數字。  \(時常被稱為屬性頁\)\] 在專案設計工具窗格會因專案類型和語言而定。  專案設計工具可以使用存取**屬性** 命令 **專案**功能表。  
  
 專案子類型 」 常需要在專案設計工具中顯示額外的屬性頁。  同樣地，某些專案子類型可能需要移除內建屬性頁。  如果要執行兩項作業，您的專案子類型必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面，並覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>方法。  藉由覆寫這個方法，並使用`propId`參數包含的值的其中一個<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>列舉型別，您可以篩選、 新增或移除專案屬性。  例如，您可能需要組態相關屬性頁中加入頁面。  若要這樣做，您要篩選組態相關屬性頁，然後將新頁面新增至現有的清單。  
  
## 加入和移除專案設計工具中的 \[屬性頁  
  
#### 若要移除 \[專案設計工具中的 \[屬性頁  
  
1.  覆寫`GetProperty(uint itemId, int propId, out object property)`方法，以篩選屬性頁，並取得`clsids`清單。  
  
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
  
2.  移除**建置事件**從網頁取得`clsids`清單。  
  
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
  
#### 若要在專案設計工具中加入一個屬性頁  
  
1.  建立您想要新增的屬性頁。  
  
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
  
2.  註冊新的屬性頁。  
  
    ```vb#  
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>  
    ```  
  
    ```c#  
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]  
    ```  
  
3.  覆寫`GetProperty(uint itemId, int propId, out object property)`方法，以篩選屬性頁、 取得`clsids`清單，並加入新的屬性頁。  
  
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
>  本主題提供的所有程式碼範例是 「 組件的較大的範例中， [VSSDK 範例](../misc/vssdk-samples.md)。  
  
## 請參閱  
 [專案子類型](../extensibility/internals/project-subtypes.md)