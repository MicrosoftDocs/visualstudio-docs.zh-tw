---
title: 建立負載測試外掛程式
description: 瞭解如何建立負載測試外掛程式，以便在負載測試執行時于不同的時間執行程式碼，這可以擴充或修改負載測試的功能。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fee903c9fd2001b6c6d229e5786dd7ffb9037b9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441087"
---
# <a name="how-to-create-a-load-test-plug-in"></a>如何：建立負載測試外掛程式

您可以建立負載測試外掛程式，以便在執行負載測試的不同時刻執行。 您可以建立外掛程式，以擴充或修改負載測試的內建功能。 例如，您可以撰寫負載測試外掛程式，以便在執行負載測試時，設定或修改負載測試模式。 若要這麼做，就必須建立繼承自 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 介面的類別。 這個類別必須實作此介面的 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> 方法。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>。

> [!TIP]
> 您也可以建立 Web 效能測試的外掛程式。 如需詳細資訊，請參閱 [如何：建立 web 效能測試外掛程式](../test/how-to-create-a-web-performance-test-plug-in.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>在 C# 中建立負載測試外掛程式
<!-- markdownlint-enable MD003 MD020 -->

1. 開啟包含 Web 效能測試的 Web 效能和負載測試專案。

2. 將負載測試加入至測試專案，並將它設定為執行 Web 效能測試。

     如需詳細資訊，請參閱[快速入門：建立負載測試專案](../test/quickstart-create-a-load-test-project.md)。

3. 將新的 **類別庫** 專案新增至方案。  (在 **方案總管** 中，以滑鼠右鍵按一下方案並選取 [ **加入** ]，然後選擇 [ **新增專案**]。 ) 

4. 在 **方案總管** 中，以滑鼠右鍵按一下新類別庫中的 [ **參考** ] 資料夾，然後選取 [ **加入參考**]。

   [新增參考] 對話方塊隨即顯示。

5. 選擇 [.NET] 索引標籤並向下捲動，然後選取 **Microsoft.VisualStudio.QualityTools.LoadTestFramework**。

6. 選擇 [確定]。

   **VisualStudio** 的參考會加入至 **方案總管** 的 [**參考**] 資料夾中。

7. 在 **方案總管** 中，以滑鼠右鍵按一下 web 效能和負載測試專案的頂端節點，此專案包含要新增負載測試外掛程式的負載測試，然後選取 [ **加入參考**]。

   [ **加入參考] 對話方塊隨即顯示**。

8. 選擇 [專案] 索引標籤並選取 [類別庫專案]。

9. 選擇 [確定]。

10. 在 [程式碼編輯器] 中，加入 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 命名空間的 `using` 陳述式。

11. 實作在類別庫專案中所建立之類別的 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 介面。 如需範例實作，請參閱下列的＜範例＞一節。

12. 程式碼撰寫完成之後，請建置新專案。

13. 以滑鼠右鍵按一下負載測試的頂端節點，然後選擇 [新增負載測試外掛程式]。

     [新增負載測試外掛程式] 對話方塊隨即顯示。

14. 在 [選取外掛程式] 底下，選取您的負載測試外掛程式類別。

15. 在 [所選外掛程式的屬性] 窗格中，設定外掛程式要在執行階段中使用的初始值。

    > [!NOTE]
    > 您可以從外掛程式公開任意數目的屬性，只要讓這些屬性成為公用、可設定且屬於基底型別 (例如整數、布林或字串) 的屬性即可。 您之後也可以使用 [ **屬性** ] 視窗來變更 web 效能測試外掛程式屬性。

16. 選擇 [確定]。

     此外掛程式就會新增至 [負載測試外掛程式] 資料夾。

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

下列程式碼會顯示在 LoadTestFinished 事件發生後，執行自訂程式碼的負載測試外掛程式。 如果這段程式碼是在遠端電腦的測試代理程式上執行，而且測試代理程式沒有 localhost SMTP 服務，負載測試就會維持在「進行中」的狀態，因為系統將會開啟訊息方塊。

> [!NOTE]
> 下列程式碼會要求您加入 System.Windows.Forms 的參考。

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

有八個事件與負載測試相關聯，而且負載測試外掛程式可以處理這些事件，以便搭配負載測試執行自訂程式碼。 下面是一份事件清單，這些事件可讓您存取負載測試回合的不同期間：

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [如何：建立 Web 效能測試外掛程式](../test/how-to-create-a-web-performance-test-plug-in.md)
