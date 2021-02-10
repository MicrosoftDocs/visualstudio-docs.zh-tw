---
title: 建立 Web 效能測試外掛程式
description: 瞭解 web 效能測試外掛程式如何讓您在 web 效能測試的主要宣告式語句之外重複使用程式碼。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 758f57d3b934298ef397984b174fbf2c38d93d1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952547"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>如何：建立 Web 效能測試外掛程式

Web 效能測試外掛程式可以讓您在 Web 效能測試的主要宣告式陳述式之外找出及重複使用程式碼。 自訂的 Web 效能測試外掛程式則能讓您在執行 Web 效能測試時呼叫某些程式碼。 在每個測試反覆項目中，Web 效能測試外掛程式都會執行一次。 此外，如果您覆寫測試外掛程式中的 PreRequest 或 PostRequest 方法，這些要求外掛程式將會分別在每項要求之前或之後執行。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您可以建立自訂的 Web 效能測試外掛程式，方法是從 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> 基底類別中衍生您自己的類別。

自訂的 Web 效能測試外掛程式可以搭配您所錄製的 Web 效能測試使用，使您能夠以最少量的程式碼，達成對 Web 測試的更高層級控制。 但是，自訂的 Web 效能測試外掛程式也可以與 Web 效能測試程式碼搭配使用。 如需詳細資訊，請參閱[產生和執行 Web 效能測試程式碼](../test/generate-and-run-a-coded-web-performance-test.md)。

> [!NOTE]
> 您也可以建立負載測試外掛程式。請參閱 [如何：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)。

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>建立自訂的 Web 效能測試外掛程式

1. 開啟包含 Web 效能測試的 Web 效能和負載測試專案。

2. 在 **方案總管** 中，以滑鼠右鍵按一下方案並選取 [ **加入** ]，然後選擇 [ **新增專案**]。

3. 建立新的 **類別庫** 專案。

   新的類別庫專案會加入至 [方案總管]，而且新的類別會出現在 [程式碼編輯器] 中。

4. 在 **方案總管** 中，以滑鼠右鍵按一下新類別庫中的 [ **參考** ] 資料夾，然後選取 [ **加入參考**]。

   [新增參考] 對話方塊隨即顯示。

5. 選擇 [.NET] 索引標籤並向下捲動，然後選取 [Microsoft.VisualStudio.QualityTools.WebTestFramework]

6. 選擇 [確定]。

     **VisualStudio** 的參考會加入至 **方案總管** 的 [**參考**] 資料夾中。

7. 在 **方案總管** 中，以滑鼠右鍵按一下 web 效能和負載測試專案的頂端節點，此專案包含您要加入 web 效能測試外掛程式的負載測試，然後選取 [ **加入參考**]。

8. [ **加入參考] 對話方塊隨即顯示**。

9. 選擇 [ **專案** ] 索引標籤，然後選取 [ **類別庫] 專案**。

10. 選擇 [確定]。

11. 在 [程式碼編輯器] 中，撰寫外掛程式的程式碼。 首先，建立衍生自 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> 的新公用類別。

12. 在一或多個事件處理常式內實作程式碼。 如需範例實作，請參閱下列的＜範例＞一節。

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. 程式碼撰寫完成之後，請建置新專案。

14. 開啟 Web 效能測試。

15. 若要加入 web 效能測試外掛程式，請選擇工具列上的 [ **加入 Web 測試外掛程式]** 。

     [新增 Web 測試外掛程式] 對話方塊隨即出現。

16. 在 **[選取外掛程式]** 底下，選取您的 web 效能測試外掛程式類別。

17. 在 [所選外掛程式的屬性] 窗格中，設定外掛程式要在執行階段中使用的初始值。

    > [!NOTE]
    > 您可以從外掛程式公開任意數目的屬性，只要讓這些屬性成為公用、可設定且屬於基底型別 (例如整數、布林或字串) 的屬性即可。 您之後也可以使用 [屬性] 視窗來變更 Web 效能測試外掛程式屬性。

18. 選擇 [確定]。

     此外掛程式就會新增至 [Web 測試外掛程式] 資料夾。

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

下列程式碼會建立自訂的 Web 效能測試外掛程式，它會將項目加入至代表測試反覆項目的 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> 中。

執行 web 效能測試之後，使用此外掛程式即可在 [ **Web 效能結果檢視器**] 的 [**內容**] 索引標籤中，看到已加入名為 **>testiteratnionnumber** 的專案。

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [如何：建立要求層級外掛程式](../test/how-to-create-a-request-level-plug-in.md)
- [為 Web 效能測試撰寫自訂擷取規則程式碼](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [為 Web 效能測試撰寫自訂驗證規則程式碼](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [如何：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)
- [產生和執行 Web 效能測試程式碼](../test/generate-and-run-a-coded-web-performance-test.md)
