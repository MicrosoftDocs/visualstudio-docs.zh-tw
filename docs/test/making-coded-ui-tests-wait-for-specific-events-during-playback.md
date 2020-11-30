---
title: 讓自動程式化 UI 測試等候特定事件
description: 瞭解如何指示自動程式化 UI 測試播放測試等候特定事件發生，例如視窗出現或進度列消失。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401888eee7fb5952c69c953824f3959c2b456a4d
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329558"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>讓自動程式化 UI 測試在播放期間等候特定事件

在自動程式化 UI 測試播放中，您可以指示測試等待發生特定事件 (例如出現視窗、進度列消失等)。 若要這樣做，請使用下表所述的適當 UITestControl.WaitForControlXXX() 方法。 如需使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> 方法等候啟用控制項的自動程式化 UI 測試範例，請參閱[逐步解說：建立、編輯和維護自動程式化 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

Visual Studio Enterprise

> [!TIP]
> 您也可以使用自動程式化 UI 測試編輯器，以新增動作之前的延遲。 如需詳細資訊，請參閱[如何：使用自動程式化 UI 測試編輯器，在 UI 動作前插入延遲](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)。

**UITestControl.WaitForControlXXX() 方法**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

等候控制項準備好接受滑鼠和鍵盤輸入。 引擎會先針對所有等待控制項備妥的動作，隱含地呼叫這個 API，然後再進行任何作業。 不過，在某些罕見的情況下，您可能必須執行明確呼叫。

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

當精靈藉由呼叫伺服器來執行輸入的一些非同步驗證時，等候啟用控制項。 例如，您可以命令方法等候精靈的 [下一步] 按鈕啟用 ()。 如需此方法的範例，請參閱[逐步解說：建立、編輯和維護自動程式化 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)。

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

等候要出現在 UI 上的控制項。 比方說，在應用程式完成參數驗證後，您預期會出現錯誤對話方塊。 驗證所花費的時間是變數。 您可以使用這個方法來等候錯誤對話方塊。

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

等候控制項從 UI 消失。 例如，您可以等候進度列消失。

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

等候控制項的指定屬性具有給定值。 例如，等候狀態文字變更為 [完成]。

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

等候控制項的指定屬性具有指定值的相反值。 例如，您等候編輯方塊變成非唯讀狀態，亦即可供您進行編輯。

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

等候指定的述詞傳回 `true`。 這可以用於指定控制項上的複雜等候作業 (例如 OR 條件)。 例如，您可以等到狀態文字變成 [成功] 或 [失敗]，如下列程式碼所示：

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDone(UITestControl control)
{
    WinText statusText = control as WinText;
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";
}

// In test method, wait till the method evaluates to true
statusText.WaitForControlCondition(IsStatusDone);
```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>

所有先前的方法都是 UITestControl 的執行個體方法。 此方法是靜態方法。 這個方法也會等候指定的述詞成為 `true`，但可用於多個控制項上的複雜等候作業 (例如 OR 條件)。 例如，您可以等到狀態文字變成 [成功] 或直到出現錯誤訊息，如下列程式碼所示：

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDoneOrError(UITestControl[] controls)
{
    WinText statusText = controls[0] as WinText;
    WinWindow errorDialog = controls[1] as WinWindow;
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;
}

// In test method, wait till the method evaluates to true
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);
```

所有這些方法都具有下列行為：

如果等候成功，方法會傳回 true；如果等候失敗則傳回 false。

等候作業的隱含逾時是由 <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> 屬性指定。 此屬性的預設值是 60000 毫秒 (一分鐘)。

方法具有可採用明確逾時 (以毫秒為單位) 的多載。 不過，當等候作業導致控制項的隱含搜尋，或當應用程式忙碌時，實際的等候時間可能會超過指定的逾時。

先前的函式功能強大且具有彈性，且幾乎可滿足所有條件。 不過，萬一這些方法無法滿足您的需求，而且您需要在程式碼中編碼 <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> 或 <xref:System.Threading.Thread.Sleep%2A> 時，建議您使用 Playback.Wait() 而非 Thread.Sleep() API。 這樣做的原因是：

您可以使用  <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A> 屬性以修改睡眠的持續時間。 根據預設，此變數是 1，但是您可以增加或減少以變更整個程式碼的等候時間。 例如，如果您要特意透過慢速網路測試，或處於某些效能較慢的情況中，您可以在某個位置上將這個變數 (或甚至在組態檔中) 變為 1.5，在所有位置額外增加 50%。

檢查使用者取消\中斷作業時，Playback.Wait() 會在 for 迴圈的較小區塊中內部呼叫 Thread.Sleep() (在上述計算後)。 換句話說，Playback.Wait() 可讓您在等候結束，且睡眠無法或擲回例外狀況之前，取消播放。

> [!TIP]
> 自動程式碼 UI 測試編輯器可讓您輕鬆地修改自動程式碼 UI 測試。 您可以使用自動程式碼 UI 測試編輯器，尋找、檢視和編輯您的測試方法。 您也可以在 UI 控制項對應中編輯 UI 動作和其相關聯控制項。 如需詳細資訊，請參閱[使用自動程式化 UI 測試編輯器來編輯自動程式化 UI 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

## <a name="see-also"></a>另請參閱

- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
- [建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)
- [逐步解說：建立、編輯和維護自動程式碼 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [自動程式碼 UI 測試的剖析](../test/anatomy-of-a-coded-ui-test.md)
- [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [如何：使用自動程式化 UI 測試編輯器，在 UI 動作前插入延遲](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
