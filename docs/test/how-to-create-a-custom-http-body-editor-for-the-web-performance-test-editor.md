---
title: 建立 web 效能測試的 HTTP 主體編輯器
description: 瞭解如何建立自訂內容編輯器，讓您能夠編輯 web 服務要求的字串內容或二進位內容。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d6da75b24a982c420b475815f665851ebf06504
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440125"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>如何：建立 Web 效能測試編輯器的自訂 HTTP 內容編輯器

您可以建立自訂內容編輯器，讓您能夠編輯 Web 服務要求的字串內容或二進位內容，例如 SOAP、REST、asmx、wcf、RIA 和其他 Web 服務要求類型。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您可以實作下列類型的編輯器：

- **字串內容編輯器**：這個編輯器是使用 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> 介面實作。

- **二進位內容編輯器**：這個編輯器是使用 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 介面實作。

這些介面包含在 <xref:Microsoft.VisualStudio.TestTools.WebTesting> 命名空間中。

## <a name="create-a-windows-control-library-project"></a>建立 Windows 控制項程式庫專案

1. 在 Visual Studio 中，建立新的 **Windows Forms 控制項程式庫** 專案。 將專案命名為 **MessageEditors**。

   專案會加入至新的方案中，而且設計工具中會出現名為 *UserControl1.cs* 的 <xref:System.Windows.Forms.UserControl>。

1. 從 [工具箱] 的 [通用控制項] 分類底下，將 <xref:System.Windows.Forms.RichTextBox> 拖曳至 UserControl1 介面上。

1. 選擇 <xref:System.Windows.Forms.RichTextBox> 控制項右上角的 [動作] 標籤圖像 (![智慧標籤圖像](../test/media/vs_winformsmttagglyph.gif))，然後選取並且 [停駐於父容器中]。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [Windows Forms 程式庫] 專案，然後選取 [ **屬性**]。

1. 在 [ **屬性**] 中，選取 [ **應用程式** ] 索引標籤。

1. 在 [目標 Framework] 下拉式清單中選取 .NET Framework 4 (或更新版本)。

1. [目標 Framework 變更] 對話方塊隨即出現。

1. 選擇 [ **是**]。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **參考** ] 節點，然後選取 [ **加入參考**]。

1. [新增參考] 對話方塊隨即顯示。

1. 選擇 [.NET] 索引標籤並向下捲動，然後選取 **Microsoft.VisualStudio.QualityTools.WebTestFramework**，再選擇 [確定]。

1. 如果 [ **View designer** ] 尚未開啟，請在 **方案總管** 中，以滑鼠右鍵按一下 [ **UserControl1.cs** ]，然後選取 [ **視圖設計** 工具]。

1. 以滑鼠右鍵按一下設計介面，然後選取 [檢視程式碼]。

1. (選擇性) 將類別和建構函式的名稱從 UserControl1 變更為有意義的名稱，例如 MessageEditorControl：

    > [!NOTE]
    > 範例中會使用 MessageEditorControl。

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. 加入下列屬性，以便取得並設定 RichTextBox1 中的文字。 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> 介面將使用 EditString，而 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 將使用 EditByteArray：

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>在 Windows 控制項程式庫專案中加入類別

將類別加入至專案。 它會用來實作 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> 和 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 介面。

**此程序之程式碼的概觀**

前述程序中建立的 MessageEditorControl <xref:System.Windows.Forms.UserControl> 會具現化為 messageEditorControl：

```csharp
private MessageEditorControl messageEditorControl
```

messageEditorControl 執行個體會裝載於 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> 方法建立的外掛程式對話方塊內。 此外，messageEditorControl 的 <xref:System.Windows.Forms.RichTextBox> 中會填入 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> 的內容。 不過，除非 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> 傳回 `true`，否則無法建立外掛程式。 以此編輯器為例，如果 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> 中的 `true` 包含 "xml"，則 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> 會傳回 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>。

當完成編輯字串內容而且使用者按一下外掛程式對話方塊中的 [確定] 時，便會呼叫 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*>，以取得作為字串的已編輯文字，並且更新 [Web 測試效能編輯器] 之要求中的 [字串內容]。

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>建立類別並實作 IStringHttpBodyEditorPlugin 介面

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [Windows Forms 控制項程式庫] 專案，然後選取 [ **加入新專案**]。

   [ **加入新項目** ] 對話方塊隨即出現。

2. 選取 [ **類別**]。

3. 在 [名稱] 文字方塊中鍵入有意義的類別名稱，例如 `MessageEditorPlugins`。

4. 選擇 [新增]  。

   Class1 會加入至專案，並顯示在 [程式碼編輯器] 中。

5. 在 [程式碼編輯器] 中，加入以下 `using` 陳述式：

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. 貼上以下程式碼以實作介面：

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>將 IBinaryHttpBodyEditorPlugin 加入至類別

實作 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 介面。

**此程序之程式碼的概觀**

<xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 介面的程式碼實作類似前述程序中涵蓋的 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>。 不過，二進位版會使用位元組陣列處理二進位資料，而不會使用字串。

第一個程序中建立的 MessageEditorControl <xref:System.Windows.Forms.UserControl> 會具現化為 messageEditorControl：

```csharp
private MessageEditorControl messageEditorControl
```

messageEditorControl 執行個體會裝載於 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> 方法建立的外掛程式對話方塊內。 此外，messageEditorControl 的 <xref:System.Windows.Forms.RichTextBox> 中會填入 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> 的內容。 不過，除非 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> 傳回 `true`，否則無法建立外掛程式。 以此編輯器為例，如果 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> 中的 `true` 包含 "msbin1"，則 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> 會傳回 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>。

當完成編輯字串內容而且使用者按一下外掛程式對話方塊中的 [確定] 時，便會呼叫 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*>，以取得作為字串的已編輯文字，並且更新 [Web 測試效能編輯器] 之要求中的 **BinaryHttpBody.Data**。

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>將 IBinaryHttpBodyEditorPlugin 加入至類別

- 在前述程序中加入的 XmlMessageEditor 類別底下撰寫或複製下列程式碼，以便從 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 介面具現化 Msbin1MessageEditor 類別，並實作需要的方法：

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>建置和部署外掛程式

1. 在 [**組建**] 功能表上，選擇 [**建立 \<Windows Form Control Library project name>**]。

2. 關閉所有 Visual Studio 執行個體。

   > [!NOTE]
   > 關閉 Visual Studio 可確保在您嘗試複製 *.dll* 檔之前，這個檔案不會遭到鎖定。

3. 從專案的 *bin\debug* 資料夾複製產生的 *.dll* 檔案 (例如 *MessageEditors.dll*) 以 *%ProgramFiles%\Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE\PrivateAssemblies\WebTestPlugins*。

4. 開啟 Visual Studio。

   *.dll* 現在已向 Visual Studio 註冊。

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>使用 Web 效能測試驗證外掛程式

1. 建立測試專案。

2. 建立 Web 效能測試，並在瀏覽器中輸入 Web 服務的 URL。

3. 當您完成錄製時，請在 Web 效能測試編輯器中展開 Web 服務的要求，並選取 **字串主體** 或 **二進位主體**。

4. 在 [ **屬性** ] 視窗中，選取 [字串主體] 或 [二進位內容]，然後選擇省略號 **( ... )**。

   [編輯 HTTP 內容資料] 對話方塊隨即顯示。

5. 現在您可以編輯資料並選擇 [確定]。 這樣會叫用適用的 GetNewValue 方法，以更新 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> 中的內容。

## <a name="compile-the-code"></a>編譯程式碼

確認 Windows 控制項程式庫專案的目標 Framework 是 .NET Framework 4.5。 根據預設，Windows 控制項程式庫專案的目標為 .NET Framework 4.5 Client Framework，它不允許包含 Microsoft.VisualStudio.QualityTools.WebTestFramework 參考。

如需詳細資訊，請參閱[專案設計工具、應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [如何：建立要求層級外掛程式](../test/how-to-create-a-request-level-plug-in.md)
- [為 Web 效能測試撰寫自訂擷取規則程式碼](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [為 Web 效能測試撰寫自訂驗證規則程式碼](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [如何：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)
- [產生和執行 Web 效能測試程式碼](../test/generate-and-run-a-coded-web-performance-test.md)
- [如何：建立 Web 效能測試結果檢視器的 Visual Studio 增益集](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
