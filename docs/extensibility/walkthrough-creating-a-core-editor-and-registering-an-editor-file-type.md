---
title: 建立核心編輯器和註冊編輯器檔案類型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cfad04648f62cbe289c1ce2408973ed3701c4b9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959560"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>逐步解說：建立核心編輯器 」 和 「 登錄編輯程式檔案類型
本逐步解說示範如何建立啟動 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器時的檔案 *.myext*載入檔案的副檔名。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>在 Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 [新增專案]  對話方塊的三個不同位置：  
  
1.  位在 [Visual Basic 擴充性] 下。 專案的預設語言為 Visual Basic。  
  
2.  位在 [C# 擴充性] 下。 專案的預設語言為 C#。  
  
3.  位在 [其他專案類型擴充性] 下。 專案的預設語言為 C++。  
  
### <a name="to-create-the-vspackage"></a>若要建立 VSPackage  
  
- 開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]並建立[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]名為 VSPackage`MyPackage`中所述，[逐步解說：建立功能表命令 VSPackage](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32)。  
  
### <a name="to-add-the-editor-factory"></a>若要加入編輯器 factory  
  
1. 以滑鼠右鍵按一下**MyPackage**專案，指向**新增**，然後按一下**類別**。  
  
2. 在 **加入新項目**對話方塊方塊中，請確定**類別**選取範本時，型別`EditorFactory.cs`為名稱，然後按一下**新增**將類別新增至您的專案。  
  
    *EditorFactory.cs*檔案應該會自動開啟。  
  
3. 從您的程式碼中參考下列組件。  
  
   ```vb  
   Imports System.Runtime.InteropServices  
   Imports Microsoft.VisualStudio  
   Imports Microsoft.VisualStudio.Shell  
   Imports Microsoft.VisualStudio.Shell.Interop  
   Imports Microsoft.VisualStudio.OLE.Interop  
   Imports Microsoft.VisualStudio.TextManager.Interop  
   Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
   ```  
  
   ```csharp  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Shell;  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio.OLE.Interop;  
   using Microsoft.VisualStudio.TextManager.Interop;  
   using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
   ```  
  
4. 新增的 GUID`EditorFactory`類別，新增`Guid`之前的類別宣告的屬性。  
  
    您可以使用來產生新的 GUID *guidgen.exe*程式設計時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示字元，或依序按一下**建立 GUID**上**工具**功能表。 此處所使用的 GUID 是只是範例;請勿使用它在您的專案。  
  
   ```vb  
   <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
   ```  
  
   ```csharp  
   [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
   ```  
  
5. 在類別定義中，加入要包含父封裝和服務提供者的兩個私用變數。  
  
   ```vb  
   Class EditorFactory  
       Private parentPackage As Package  
       Private serviceProvider As IOleServiceProvider  
   ```  
  
   ```csharp  
   class EditorFactory  
   {  
       private Package parentPackage;  
       private IOleServiceProvider serviceProvider;  
   }  
  
   ```  
  
6. 新增公用類別建構函式接受一個參數的型別<xref:Microsoft.VisualStudio.Shell.Package>:  
  
   ```vb  
   Public Sub New(ByVal parentPackage As Package)  
       Me.parentPackage = parentPackage  
   End Sub  
   ```  
  
   ```csharp  
   public EditorFactory(Package parentPackage)  
   {  
       this.parentPackage = parentPackage;  
   }  
   ```  
  
7. 修改`EditorFactory`類別衍生自宣告<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。  
  
   ```vb  
   Class EditorFactory Implements IVsEditorFacto  
   ```  
  
   ```csharp  
   class EditorFactory : IVsEditorFactory  
  
   ```  
  
8. 以滑鼠右鍵按一下<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>，按一下**實作介面**，然後按一下**明確實作介面**。  
  
    這個步驟會加入四個方法必須實作在<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。  
  
9. 以下列程式碼取代 `IVsEditorFactory.Close` 方法的內容。  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. 內容取代`IVsEditorFactory.SetSite`為下列程式碼。  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. 以下列程式碼取代 `IVsEditorFactory.MapLogicalView` 方法的內容。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. 以下列程式碼取代 `IVsEditorFactory.CreateEditorInstance` 方法的內容。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. 編譯專案，並確定沒有任何錯誤。  
  
### <a name="to-register-the-editor-factory"></a>若要註冊編輯器 factory  
  
1. 在**方案總管 中**，按兩下**Resources.resx**檔案，以開啟到字串資料表，在其中的項目**String1 是**選取。  
  
2. 變更的識別項的名稱`IDS_EDITORNAME`和以文字**MyPackage 編輯器。** 這個字串會顯示為您的編輯器的名稱。  
  
3. 開啟**VSPackage.resx**檔案中，加入新字串，將名稱設**101**，並將值設定為`IDS_EDITORNAME`。 此步驟可讓您存取您所建立的字串資源識別碼的套件。  
  
   > [!NOTE]
   >  如果**VSPackage.resx**檔案包含另一個字串`name`屬性設為**101**，取代另一個唯一的數字的值，這裡並在下列步驟。  
  
4. 在 **方案總管**，開啟**MyPackagePackage.cs**檔案。  
  
    這個檔案是主套件檔案。  
  
5. 之前加入下列的使用者屬性`Guid`屬性。  
  
   ```vb  
   <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
   <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
         ".myext", 32, NameResourceID:=101 )> _  
   ```  
  
   ```csharp  
   [ProvideEditorFactory(typeof(EditorFactory), 101)]  
   [ProvideEditorExtension(typeof(EditorFactory),   
         ".myext", 32, NameResourceID = 101)]   
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>屬性產生關聯 *.myext*檔案編輯器 factory 的延伸模組，讓任何一次，在載入延伸模組，會叫用編輯器 factory 的檔案。  
  
6. 加入私用變數，以`MyPackage`類別，建構函式之前，並提供它的類型`EditorFactory`。  
  
   ```vb  
   Private editorFactory As EditorFactory  
   ```  
  
   ```csharp  
   private EditorFactory editorFactory;  
   ```  
  
7. 尋找`Initialize`方法 (您可能必須開啟`Package Members`隱藏的區域)，並新增下列程式碼呼叫之後`base.Initialize()`。  
  
   ```vb  
   'Create our editor factory and register it.   
   Me.editorFactory = New EditorFactory(Me)  
   MyBase.RegisterEditorFactory(Me.editorFactory)  
   ```  
  
   ```csharp  
   // Create our editor factory and register it.  
   this.editorFactory = new EditorFactory(this);  
   base.RegisterEditorFactory(this.editorFactory);  
  
   ```  
  
8. 編譯程式，並確定沒有任何錯誤。  
  
    此步驟中登錄的實驗登錄區中的編輯器 factory [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如果系統提示您覆寫*resource.h*檔案中，按一下**確定**。  
  
9. 建立名為的範例檔案*TextFile1.myext*。  
  
10. 按下**F5**若要開啟的實驗性執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
11. 在實驗性[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，請在**檔案**功能表上，指向**Open** ，然後按一下**檔案**。  
  
12. 尋找**TextFile1.myext** ，然後按一下**開啟**。  
  
     現在應該載入的檔案。  
  
## <a name="robust-programming"></a>穩固程式設計  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器處理各種不同的文字為基礎的檔案類型和密切搭配語言服務提供一組豐富的功能，例如語法醒目提示、 括號對稱和 IntelliSense 文字自動完成，並列出成員自動完成。 如果您正在使用以文字為基礎的檔案，您可以使用核心編輯器，以及支援您的特定檔案類型的自訂語言服務。  
  
 VSPackage 可以叫用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器所提供的編輯器 factory。 此編輯器 factory 會使用任何具有與其相關聯的檔案載入的時間。 如果檔案是專案的一部分，核心編輯器會自動叫用，但覆寫 VSPackage。 不過，如果檔案已載入專案外，核心編輯器必須明確地叫用 VSPackage。  
  
 如需有關核心編輯器的詳細資訊，請參閱[核心編輯器內](../extensibility/inside-the-core-editor.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在核心編輯器](../extensibility/inside-the-core-editor.md)   
 [使用舊版 API 具現化核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)