---
title: 逐步解說：建立核心編輯器和註冊編輯器檔案類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687641"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>逐步解說：建立核心編輯器和註冊編輯器檔案類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何建立 VSPackage，以 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 在載入副檔名為 myext 的檔案時啟動核心編輯器。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 套件專案範本的位置  
 Visual Studio Package 專案範本位在 [新增專案] **** 對話方塊的三個不同位置：  
  
1. 位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。  
  
2. 位在 C# 擴充性下。 專案的預設語言為 C#。  
  
3. 位在其他專案類型擴充性下。 專案的預設語言為 C++。  
  
### <a name="to-create-the-vspackage"></a>若要建立 VSPackage  
  
- 啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 並建立 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 名為的 VSPackage `MyPackage` ，如 [逐步解說：建立功能表命令 VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32)中所述。  
  
### <a name="to-add-the-editor-factory"></a>若要加入編輯器 factory  
  
1. 以滑鼠右鍵按一下 **MyPackage** 專案，指向 [ **加入** ]，然後按一下 [ **類別**]。  
  
2. 在 [ **加入新專案** ] 對話方塊中，確定已選取 [ **類別** ] 範本，輸入 `EditorFactory.cs` 名稱，然後按一下 [ **新增** ]，將類別加入至您的專案。  
  
     EditorFactory.cs 檔案應該會自動開啟。  
  
3. 從您的程式碼參考下列元件。  
  
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
  
4. 在類別宣告之前加入屬性，以將 GUID 加入至 `EditorFactory` 類別 `Guid` 。  
  
     您可以在命令提示字元中使用 guidgen.exe 程式 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，或按一下 [**工具**] 功能表上的 [**建立 GUID** ]，以產生新的 guid。 此處使用的 GUID 只是範例：請勿在您的專案中使用。  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. 在類別定義中，加入兩個私用變數以包含父封裝和服務提供者。  
  
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
  
6. 新增公用類別的函式，此函式會接受一個類型為的參數 <xref:Microsoft.VisualStudio.Shell.Package> ：  
  
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
  
7. 修改 `EditorFactory` 要從介面衍生的類別宣告 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 。  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. 以滑鼠右鍵按一下 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> ，按一下 [ **執行介面**]，然後按一下 [ **明確地執行介面**]。  
  
     這會加入必須在介面中實作為的四個方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 。  
  
9. 將 `IVsEditorFactory.Close` 方法的內容取代為下列程式碼。  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. 以下列程式碼取代的內容 `IVsEditorFactory.SetSite` 。  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. 將 `IVsEditorFactory.MapLogicalView` 方法的內容取代為下列程式碼。  
  
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
  
12. 將 `IVsEditorFactory.CreateEditorInstance` 方法的內容取代為下列程式碼。  
  
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
  
13. 請編譯專案，並確定沒有任何錯誤。  
  
### <a name="to-register-the-editor-factory"></a>註冊編輯器 factory  
  
1. 在 **方案總管**中，按兩下 Resources .resx 檔案，將它開啟至字串資料表，其中會選取專案 **String1** 。  
  
2. 將識別碼的名稱變更為 `IDS_EDITORNAME` ，並將文字變更為 **MyPackage 編輯器。** 這個字串將會顯示為編輯器的名稱。  
  
3. 開啟 VSPackage .resx 檔，並加入新的字串，將名稱設為 **101** ，並將值設定為 `IDS_EDITORNAME` 。 這會提供具有資源識別碼的套件，以存取您剛才建立的字串。  
  
    > [!NOTE]
    > 如果 VSPackage .resx 檔案包含 `name` 屬性設為 **101**的另一個字串，請在這裡和下列步驟中取代另一個唯一的數值。  
  
4. 在 **方案總管**中，開啟 MyPackagePackage.cs 檔案。  
  
     這是主要的封裝檔案。  
  
5. 請在屬性之前加入下列使用者屬性 `Guid` 。  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>屬性會將 myext 副檔名與編輯器 factory 產生關聯，如此一來，每當載入副檔名的檔案時，就會叫用您的編輯器 factory。  
  
6. 將私用變數新增至 `MyPackage` 類別，在此函式之前，並為其提供型別 `EditorFactory` 。  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. 尋找 `Initialize` (您可能必須開啟 `Package Members` 隱藏區域) 的方法，並在呼叫之後加入下列程式碼 `base.Initialize()` 。  
  
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
  
     此步驟會在的實驗登錄 hive 中註冊編輯器 factory [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如果系統提示您覆寫資源 .h 檔案，請按一下 **[確定]**。  
  
9. 建立名為 Textfile1.txt 的範例檔案。 myext。  
  
10. 按 **F5** 以開啟實驗性的實例 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
11. 在實驗性的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [檔案**File** ] 功能表上，指向 [**開啟**]， **File**然後按一下 [檔案]。  
  
12. 尋找 Textfile1.txt myext，然後按一下 [ **開啟**]。  
  
     現在應該會載入檔案。  
  
## <a name="robust-programming"></a>穩固程式設計  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]核心編輯器會處理各種以文字為基礎的檔案類型，並與語言服務密切配合，以提供一組豐富的功能，例如語法醒目提示、括弧對稱，以及 IntelliSense 字完成和成員完成清單。 如果您使用以文字為基礎的檔案，則可以搭配使用核心編輯器與支援特定檔案類型的自訂語言服務。  
  
 VSPackage 可以藉 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 由提供編輯器 factory 來叫用核心編輯器。 每當載入與它相關聯的檔案時，就會使用這個編輯器 factory。 如果檔案是專案的一部分，則會自動叫用核心編輯器，除非您的 VSPackage 覆寫。 但是，如果檔案是在專案外載入，則您的 VSPackage 必須明確地叫用核心編輯器。  
  
 如需核心編輯器的詳細資訊，請參閱 [核心編輯器中的](../extensibility/inside-the-core-editor.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在核心編輯器中](../extensibility/inside-the-core-editor.md)   
 [使用舊版 API 將核心編輯器具現化](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
