---
title: 自動程式化 UI 測試的最佳作法
description: 瞭解開發自動程式碼 UI 測試的建議。 這些指導方針可協助您建立彈性的自動程式碼 UI 測試。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a4a79ca397b46d06e18c62fde2034551ff7afe0
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441803"
---
# <a name="best-practices-for-coded-ui-tests"></a>自動程式化 UI 測試的最佳做法

本主題描述一些開發自動程式化 UI 測試的建議。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>最佳作法

使用下列指導方針，建立彈性的自動程式化 UI 測試。

- 請盡可能使用 **自動程式碼 UI 測試產生器**。

- 請不要直接修改 UIMap.designer.cs 檔案。 如果您修改此檔案，將會覆寫檔案的變更。

- 將您的測試建立為一系列已錄製的方法。 如需如何錄製方法的詳細資訊，請參閱[建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)。

- 每個錄製的方法應在單一頁面、表單或對話方塊上執行。 建立一個新的測試方法，用於每個新的頁面、表單或對話方塊。

- 當您建立方法時，請使用有意義的方法名稱，而不是預設名稱。 有意義的名稱有助於識別方法的用途。

- 可能的話，請將每個錄製的方法限定在 10 個動作以內。 此模組化方法可讓您在 UI 變更時輕鬆地取代方法。

- 使用 [自動程式化 UI 測試產生器] 建立每個判斷提示，它會自動將判斷提示方法新增至 UIMap.Designer.cs 檔案。

- 如果使用者介面 (UI) 有所變更，請重新錄製測試方法或判斷提示方法，或重新錄製現有測試方法受影響的區段。

- 為您應用程式中受測試的每個模組建立個別的 [UIMap](/previous-versions/dd580454(v=vs.140)) 檔案。 如需詳細資訊，請參閱[測試含有多個 UI 對應的大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)。

- 當您建立 UI 控制項時，應在受測試的應用程式中使用有意義的名稱。 使用有意義的名稱可讓自動產生的控制項名稱更加清楚且容易使用。

- 如果要使用 API 撰寫程式碼以建立判斷提示，請為 [UIMap](/previous-versions/dd580454(v=vs.140)) 類別中屬於 *UIMap.cs* 檔案的每個判斷提示建立一個方法。 若要執行判斷提示，請從您的測試方法中呼叫此方法。

- 如果要直接使用 API 撰寫程式碼，請盡可能在您的程式碼中使用 UIMap.Designer.cs 檔案所產生之類別中的屬性和方法。 這些類別會使您的工作更容易、更可靠，並且有助於您提高生產力。

自動程式碼 UI 測試會隨著使用者介面中的許多變更自動調整。 例如，如果 UI 元素已變更位置或色彩，大多數情況下，自動程式化 UI 測試仍可找到正確的元素。

在測試回合期間，UI 控制項是由測試架構透過使用一組搜尋屬性進行定位。 搜尋屬性會套用至定義中的每個控制項類別，這些定義是由 [自動程式化 UI 測試產生器] 在 UIMap.Designer.cs 檔案中所建立的。 搜尋屬性包含屬性名稱和屬性值的名稱/值組，可用來識別控制項，例如控制項的 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>、<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> 和 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> 屬性。 如果搜尋屬性未變更，自動程式化 UI 測試將會在 UI 中成功找出控制項。 如果搜尋屬性已變更，自動程式化 UI 測試會以套用啟發學習法的智慧比對演算法，來尋找 UI 中的控制項和視窗。 當 UI 已變更時，您可以修改先前已識別之元素的搜尋屬性，以確定已找到這些元素。

## <a name="if-your-user-interface-changes"></a>若您的使用者介面變更

使用者介面在開發期間會經常變更。 下列方法可以減少這些變更的影響：

- 找出已錄製且參考此控制項的方法，並使用 [自動程式化 UI 測試產生器] 重新錄製此方法的動作。 您可以讓方法使用相同名稱，以覆寫現有的動作。

- 如果控制項有不再有效的判斷提示：

  - 刪除包含該判斷提示的方法。

  - 從測試方法移除對此方法的呼叫。

  - 加入新的判斷提示，方法是將交叉線按鈕拖曳至 UI 控制項上，開啟 UI 對應，然後加入新的判斷提示。

如需如何錄製自動程式化 UI 測試的詳細資訊，請參閱[使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)。

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>若必須先完成背景處理序才能繼續執行測試

您可能必須等到處理序完成，才能繼續進行下一個 UI 動作。 若要這樣做，您可以使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> 以在測試繼續前等待，如下列範例所示：

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>另請參閱

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
- [建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)
- [測試含有多個 UI 對應的大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
