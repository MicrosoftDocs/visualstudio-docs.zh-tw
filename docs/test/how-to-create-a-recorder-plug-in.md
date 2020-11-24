---
title: 建立 Web 效能測試的錄製器外掛程式
description: 瞭解當您在 Web 效能測試錄製器工具列中選擇 [停止] 之後，WebTestRecorderPlugin 可如何讓您修改已錄製的 web 效能測試。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce4be33e2e29ee0089184a034e56cf3a0539dc76
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440056"
---
# <a name="how-to-create-a-recorder-plug-in"></a>如何：建立錄製器外掛程式

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> 讓您修改錄製的 Web 效能測試。 修改會在您選擇 **Web 效能測試錄製** 器工具列中的 [**停止**] 之後，但在 Web 效能測試編輯器中儲存及呈現測試之前發生。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

錄製器外掛程式可讓您執行自己的自訂動態參數相互關聯。 利用內建的相互關聯功能，web 效能測試會在完成時偵測 web 錄製中的動態參數，或是當您在 **Web 效能測試編輯器** 工具列上使用 [將 **動態參數升至 web 測試參數**] 時偵測動態參數。 不過，內建偵測功能不一定會找到所有動態參數。 例如，它找不到通常在 5 到 30 分鐘之內就會變更值的工作階段 ID。 因此，您必須手動執行相互關聯程序。

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> 讓您撰寫您自己的自訂外掛程式程式碼。 這個外掛程式會在 [Web 效能測試編輯器] 儲存及呈現 Web 效能測試之前，以許多方式執行相互關聯或修改 Web 效能測試。 因此，如果您判斷特定動態變數必須針對許多錄製進行相互關聯，可以自動化此程序。

錄製器外掛程式也有其他使用方式：加入擷取和驗證規則、加入內容參數，或將 Web 效能測試中的註解轉換為異動。

下列程序描述如何建立錄製器外掛程式的基本程式碼、部署外掛程式，以及執行外掛程式。 程序後面的範例程式碼示範如何使用 Visual C# 建立自訂動態參數相互關聯錄製器外掛程式。

## <a name="create-a-recorder-plug-in"></a>建立錄製器外掛程式

### <a name="to-create-a-recorder-plug-in"></a>若要建立錄製器外掛程式

1. 開啟方案，其中包含的 Web 效能和負載測試專案有您要為其建立錄製器外掛程式的 Web 效能測試。

2. 將新的 **類別庫** 專案新增至方案。

3. 在 **方案總管** 的 [新增類別庫專案] 資料夾中，以滑鼠右鍵按一下 [ **參考** ] 資料夾，然後選取 [ **加入參考**]。

    > [!TIP]
    > 新類別庫專案資料夾的範例是 **RecorderPlugins**。

     [新增參考] 對話方塊隨即顯示。

4. 選取 [.NET] 索引標籤。

5. 向下捲動並選取 **Microsoft.VisualStudio.QualityTools.WebTestFramework**，然後選擇 [確定]。

     **VisualStudio** 會加入 **方案總管** 的 [**參考**] 資料夾中。

6. 撰寫錄製器外掛程式的程式碼。 首先，建立衍生自 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> 的新公用類別。

7. 覆寫 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> 方法。

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     事件引數提供兩個可用的物件：錄製的結果和錄製的 Web 效能測試。 這可讓您逐一查看結果尋找特定值，然後跳至 Web 效能測試中的相同要求進行修改。 如果您要加入內容參數或參數化 URL 的組成部分，也可以只修改 Web 效能測試。

    > [!NOTE]
    > 如果修改 Web 效能測試，同時也需要將 <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> 屬性設定為 true：`e.RecordedWebTestModified = true;`

8. 依據您要錄製器外掛程式在 Web 錄製發生之後執行的動作，加入其他程式碼。 例如，您可以加入程式碼以處理自訂相互關聯，如下列範例所示。 此外，也可以建立錄製器外掛程式，以用於將註解轉換為異動，或將驗證規則加入至 Web 效能測試等作業。

9. 在 [**組建**] 功能表上，選擇 [**建立 \<class library project name>**]。

接下來，請部署錄製器外掛程式，以便向 Visual Studio 註冊。

### <a name="deploy-the-recorder-plug-in"></a>部署錄製器外掛程式

在編譯錄製器外掛程式之後，請在下列兩個位置的其中一個放置產生的 DLL：

- *%ProgramFiles(x86)%\Microsoft Visual Studio\\[版本]\\[版別]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [版本]\WebTestPlugins*

> [!WARNING]
> 將錄製器外掛程式複製到這兩個位置之一後，您必須重新啟動 Visual Studio，以便註冊錄製器外掛程式。

### <a name="execute-the-recorder-plug-in"></a>執行錄製器外掛程式

1. 建立新的 Web 效能測試。

     [啟用 WebTestRecordPlugins] 對話方塊隨即顯示。

2. 選取錄製器外掛程式的核取方塊，然後選擇 [確定]。

     在 Web 效能測試完成錄製之後，就會執行新的錄製器外掛程式。

    > [!WARNING]
    > 當您執行使用外掛程式的 Web 效能測試或負載測試時，可能會收到如下錯誤：
    >
    > **要求失敗：事件中 \<plug-in> 發生例外狀況：無法載入檔案或元件 ' \<"Plug-in name".dll file> ，版本 = \<n.n.n.n> ，文化特性 = 中性，PublicKeyToken = null ' 或其相依性的其中之一。系統找不到指定的檔案。**
    >
    > 如果您對任何外掛程式進行程式碼變更並建立新的 DLL 版本 **(Version=0.0.0.0)**，但是外掛程式仍然參考原始的外掛程式版本，就會導致此錯誤發生。 若要更正此問題，請依照下列步驟執行：
    >
    > 1. 在 Web 效能和負載測試專案中，您將會在參考中看見警告。 移除並重新加入外掛程式 DLL 的參考。
    > 2. 從測試或適當的位置中移除外掛程式，然後再重新加入。

## <a name="example"></a>範例

這個範例示範如何建立自訂 Web 效能測試錄製器外掛程式，以執行自訂動態參數相互關聯。

> [!NOTE]
> 範例程式碼完整清單位在本主題底部。

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>逐一查看結果，以尋找有 ReportSession 的第一頁

程式碼範例的這個部分會逐一查看每個錄製的物件並搜尋 ReportSession 的回應主體。

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

### <a name="add-an-extraction-rule"></a>加入擷取規則

現在已找到回應，您需要加入擷取規則。 程式碼範例的這個部分會使用 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> 類別建立擷取規則，然後在 Web 效能測試中尋找要加入擷取規則的正確要求。 每個結果物件中都會加入 DeclarativeWebTestItemId 新屬性，程式碼中使用這個屬性從 Web 效能測試取得正確要求。

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

### <a name="replace-query-string-parameters"></a>取代查詢字串參數

現在程式碼尋找名稱為 ReportSession 的所有查詢字串參數，並將值變更為 {{SessionId}}，如程式碼範例的這個部分所示：

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [產生和執行 Web 效能測試程式碼](../test/generate-and-run-a-coded-web-performance-test.md)
