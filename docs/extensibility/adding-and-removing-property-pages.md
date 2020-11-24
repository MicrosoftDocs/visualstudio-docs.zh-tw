---
title: 新增和移除屬性頁 |Microsoft Docs
description: 瞭解如何在 [專案設計工具] 中加入和移除屬性頁，以提供在 Visual Studio 中管理專案屬性的集中位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- property pages, adding
- property pages, project subtypes
- property pages, removing
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 5bcd97b39d623a74eeebc26ae9e3c479530a1345
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597778"
---
# <a name="add-and-remove-property-pages"></a>新增和移除屬性頁

專案設計工具提供集中的位置，以管理中的專案屬性、設定和資源 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 它會顯示為整合式開發環境中的單一視窗 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (IDE) ，並且在右邊的索引標籤上包含一些可存取的窗格。 在 [專案設計工具] 中， (通常稱為屬性頁) 的窗格會因專案類型和語言而異。 您可以使用 [**專案**] 功能表上的 [**屬性**] 命令來存取專案設計工具。

專案子類型通常需要在 [專案設計工具] 中顯示其他屬性頁。 同樣地，某些專案子類型可能需要移除內建屬性頁。 若要執行這其中一項，您的專案子類型必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面並覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 方法。 藉由覆寫這個方法，並使用 `propId` 包含其中一個列舉值的參數 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ，您就可以篩選、加入或移除專案屬性。 例如，您可能需要將頁面新增至設定相依的屬性頁。 若要這樣做，您需要篩選與設定相依的屬性頁面，然後將新頁面新增至現有的清單。

## <a name="add-and-remove-property-pages-in-project-designer"></a>在專案設計工具中加入和移除屬性頁

### <a name="remove-a-property-page"></a>移除屬性頁

1. 覆寫 `GetProperty(uint itemId, int propId, out object property)` 方法以篩選屬性頁並取得 `clsids` 清單。

    ```vb
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

    ```csharp
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

2. 從取得的清單中移除 [ **建立事件** ] 頁面 `clsids` 。

    ```vb
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

    ```csharp
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

### <a name="add-a-property-page"></a>加入屬性頁

1. 建立您想要加入的屬性頁。

    ```vb
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

    ```csharp
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

2. 註冊您的新屬性頁面。

    ```vb
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>
    ```

    ```csharp
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]
    ```

3. 覆寫 `GetProperty(uint itemId, int propId, out object property)` 方法以篩選屬性頁，取得 `clsids` 清單並加入新的屬性頁。

    ```vb
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

    ```csharp
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

## <a name="see-also"></a>另請參閱

- [專案子類型](../extensibility/internals/project-subtypes.md)
