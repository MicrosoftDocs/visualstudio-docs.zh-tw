---
title: " (web 效能測試建立要求層級外掛程式) "
description: 瞭解個別要求的 web 效能測試外掛程式如何讓您在 web 效能測試的主要宣告式語句之外重複使用程式碼。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f546d0433ff5fa3a55f49f559597f1c7a45b1596
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877924"
---
# <a name="how-to-create-a-request-level-plug-in"></a>如何：建立要求層級外掛程式

*要求* 是構成 web 效能測試的宣告式語句。 Web 效能測試外掛程式可以讓您在 Web 效能測試的主要宣告式陳述式之外找出及重複使用程式碼。 您可以建立外掛程式，並將其加入到個別的要求中，也可以加入到包含要求的 Web 效能測試中。 自訂的「要求外掛程式」提供您一種方式，可以在特別要求於 Web 效能測試中執行時呼叫程式碼。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

每個 Web 效能測試要求外掛程式都有 PreRequest 方法和 PostRequest 方法。 將要求外掛程式附加至特定 http 要求後，會在發出要求前引發 PreRequest 事件，並會在收到回應後引發 PostRequest。

您可以建立自訂的 Web 效能測試要求外掛程式，方法是從 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> 基底類別中衍生自己的類別。

您可以使用自訂的 Web 效能測試要求外掛程式搭配您已經記錄的 Web 效能測試。 自訂的 Web 效能測試要求外掛程式讓您可以撰寫極少量的程式碼，即可達成對 Web 效能測試的更高層級控制。 但是，自訂的 Web 效能測試外掛程式也可以與 Web 效能測試程式碼搭配使用。 請參閱[產生和執行自動程式化 Web 效能測試](../test/generate-and-run-a-coded-web-performance-test.md)。

## <a name="to-create-a-request-level-plug-in"></a>若要建立要求層級外掛程式

1. 在 **方案總管** 中，以滑鼠右鍵按一下方案，選取 [ **加入** ]，然後選擇 [ **新增專案**]。

2. 建立新的 **類別庫** 專案。

3. 在 **方案總管** 中，以滑鼠右鍵按一下新類別庫中的 [ **參考** ] 資料夾，然後選取 [ **加入參考**]。

     [新增參考] 對話方塊隨即顯示。

4. 選擇 [.NET] 索引標籤並向下捲動，然後選取 **Microsoft.VisualStudio.QualityTools.WebTestFramework**，再選擇 [確定]

     **VisualStudio** 的參考會加入至 **方案總管** 的 [**參考**] 資料夾中。

5. 在 **方案總管** 中，以滑鼠右鍵按一下 web 效能和負載測試專案的頂端節點，此專案包含您要加入 web 效能測試要求測試外掛程式的負載測試。 選取 [新增參考]。

     [ **加入參考] 對話方塊隨即顯示**。

6. 選擇 [ **專案** ] 索引標籤，選取 [ **類別庫] 專案** ，然後選擇 **[確定]** 。

7. 在 [程式碼編輯器] 中，撰寫外掛程式的程式碼。 首先，建立衍生自 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> 的新公用類別。

8. 在 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> 和 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> 這兩個事件處理常式的其中一個或同時在兩個內實作程式碼。 如需範例實作，請參閱下列的＜範例＞一節。

9. 程式碼撰寫完成之後，請建置新專案。

10. 開啟您想加入要求外掛程式的 Web 效能測試。

11. 以滑鼠右鍵按一下要在其中新增要求外掛程式的要求，然後選取 [新增要求外掛程式]。

     [新增 Web 要求外掛程式] 對話方塊隨即顯示。

12. 在 [選取外掛程式] 底下，選取新的外掛程式。

13. 在 [所選外掛程式的屬性] 窗格中，設定外掛程式要在執行階段中使用的初始值。

    > [!NOTE]
    > 您可以從外掛程式公開任意數目的屬性，只要讓這些屬性成為公用、可設定且屬於基底型別 (例如整數、布林或字串) 的屬性即可。 您之後也可以使用 [屬性] 視窗來變更 Web 效能測試外掛程式屬性。

14. 選擇 [確定]。

     外掛程式就會新增至 [要求外掛程式] 資料夾，這是 HTTP 要求的子資料夾。

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

您可以使用下列程式碼建立自訂的 Web 效能測試外掛程式，該外掛程式會顯示兩個對話方塊。 一個對話方塊會顯示 URL，此 URL 與附加要求增益集的要求相關聯。 另一個對話方塊則顯示代理程式的電腦名稱。

> [!NOTE]
> 下列程式碼會要求您加入 System.Windows.Forms 的參考。

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [為 Web 效能測試撰寫自訂擷取規則程式碼](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [為 Web 效能測試撰寫自訂驗證規則程式碼](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [如何：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)
- [產生和執行 Web 效能測試程式碼](../test/generate-and-run-a-coded-web-performance-test.md)
