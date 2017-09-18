---
title: "Visual Studio 中的 Live Unit Testing | Microsoft Docs"
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: 0a939044b9806236cf55333c30bce24ae0fdb28a
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>Visual Studio 2017 的 Live Unit Testing

當您開發應用程式時，Live Unit Testing 會在背景自動執行任何受影響的單元測試，並立即在 Visual Studio IDE 中呈現即時的結果和程式碼涵蓋範圍。 當您修改程式碼時，Live Unit Testing 會針對您的變更如何影響現有測試，以及您所增加的新程式碼是否受到一或多個現有測試所涵蓋提供反饋。 這可在您進行錯誤修正或新增功能時，委婉地提醒您撰寫單元測試。

> [!NOTE]
> Live Unit Testing 適用於以 Visual Studio 2017 Enterprise Edition 中的 .NET Core 或 .NET Framework 為目標的 C# 和 Visual Basic 專案。

## <a name="supported-test-frameworks"></a>支援的測試架構
Live Unit Testing 適用於下表所列的三種熱門單元測試架構。 其配接器與架構所支援的最小版本也列於表格中。 單元測試架構全都可從 NuGet.org 取得。
 
<table> 
<tr>
   <th>測試架構</th>
   <th>Visual Studio 配接器最小版本</th>
   <th>架構最小版本</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio 版本 2.2.0-beta3-build1187</td>
   <td>xunit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter 版本 3.5.1</td>  
   <td>NUnit 版本 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.11</td>
   <td>MSTest.TestFramework 1.1.11</td>
</tr>
</table>

如果您有來自現有專案的舊版配接器和測試架構參考，請務必移除它們。 (如果您使用 MSTest，請務必移除對 `Microsoft.VisualStudio.QualityTools.UnitTestFramework` 的參考)。如果 Live Unit Testing 無法運作，請加入新的參考。 

在某些情況下，您可能需要明確地還原方案中的專案所參考的 NuGet 封裝，才能使 Live Unit Testing 運作。 若要執行此動作，您可以在啟用 Living Unit Testing 之前，明確地建置方案 (從最上層的 Visual Studio 功能表中依序選取 [建置] 和 [重建方案])，或是在方案中還原封裝 (以滑鼠右鍵按一下方案，然後選取 [還原 NuGet 封裝])。 

#   <a name="configuring-live-unit-testing"></a>設定 Live Unit Testing

您可以設定 Live Unit Testing，方法是從最上層的 Visual Studio 功能表中依序選取 [工具] 和 [選項]，然後在 [選項] 對話方塊的左窗格中選取 [Live Unit Testing]。 下圖顯示對話方塊中提供的 Live Unit Testing 組態選項。

  ![Image](./media/lut-options.png)

可設定的選項包括：

- Live Unit Testing 是否會在方案開啟時自動執行。
- Live Unit Testing 是否會在方案完成建置及偵錯後暫停，或是在系統的電池電力低於指定的臨界值時暫停。
- 測試案例逾時的時間間隔；預設值為 30 秒。 
- Live Unit Testing 建立的測試處理序數目。 
- 寫入至 Live Unit Testing [輸出] 視窗的資訊層級。 選項包括不記錄 ([無])、僅限錯誤訊息 ([錯誤])、錯誤與資訊訊息 ([資訊]，預設值) 或所有詳細資料 ([詳細資訊])。

您也可以在 Live Unit Testing 的 [輸出] 視窗中顯示詳細資訊輸出，方法是將 "1" 的值指派給名為 `VS_UTE_DIAGNOSTICS` 的使用者層級環境變數，然後重新啟動 Visual Studio。 

若要將來自 Live Unit Testing 的詳細 MSBuild 記錄訊息擷取到檔案，請將 `LiveUnitTesting_BuildLog` 使用者層級環境變數設為該檔案的名稱，以包含記錄。

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>啟動、暫停和停止 Live Unit Testing

您可以從最上層的 Visual Studio 功能表依序選取 [測試]，[Live Unit Testing] 及 [啟動]，來啟用 Live Unit Testing。 啟用 Live Unit Testing 時，[Live Unit Testing] 功能表上的可用選項會從單一項目 ([啟動]) 變更為 [暫停]、[停止] 及 [重新啟動]。

您隨時都能暫時停止或完全停止 Live Unit Testing。 例如，如果您正在進行重構，並知道測試會因此中斷一段時間，則您可能會想要執行此動作。 這三個功能表選項如下：

- **暫停**：它會暫時停止 Live Unit Testing。 
    暫停 Live Unit Testing 時，您涵蓋範圍的視覺效果不會出現在編輯器中，但會保留所有已收集的資料。 若要繼續進行 Live Unit Testing，請選取 [Live Unit Testing] 功能表中的 [繼續]。 Live Unit Testing 會執行必要的工作來更新所有在暫停期間所做出的編輯，並會適當地更新字符。 
- **停止**：可完全停止 Live Unit Testing。 Live Unit Testing 會捨棄所有已收集的資料。
- **重新啟動**：相當於選取 [Live Unit Testing] 功能表中的 [停止]，並接著選取 [啟動]。

##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>在輸入期間於編輯器中檢視涵蓋範圍的視覺效果

一旦啟用之後，Live Unit Testing 就會更新 Visual Studio 編輯器中的每個程式碼行，以顯示單元測試是否會涵蓋您撰寫的程式碼，以及涵蓋該程式碼的測試是否順利通過。  下圖顯示顯示具有通過及失敗測試的程式碼行，以及不受測試涵蓋的程式碼行。 僅由通過的測試所涵蓋的程式碼行會以綠色的 "✓" 裝飾，由一或多個失敗測試所涵蓋的程式碼行會以紅色 "🞩" 裝飾，而沒有受任何測試涵蓋的程式碼行則會以藍色 "" 裝飾。

  ![Image](./media/lut-codewindow.png)

當您在程式碼編輯器中修改程式碼時，系統會立即更新 Live Unit Testing 涵蓋範圍的視覺效果。 處理編輯時，視覺效果會變更來表示資料不是最新狀態，並會在通過、失敗及未涵蓋符號下方新增圓形計時器圖案，如下圖所示。

  ![Image](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>取得成功或失敗測試的相關資訊

藉由將滑鼠暫留在程式碼視窗中的成功或失敗符號上方，您就能看到已針對該行做出多少測試。 如果您按一下該符號，就能看見個別測試的狀態，如下圖所示。
 
  ![Image](./media/lut-failedinfo.png) 

當您將滑鼠暫留在工具提示中的失敗測試上方時，工具提示會展開以提供有關失敗的其他資訊，如下圖所示。 如果您按一下工具提示中的失敗測試，就能直接瀏覽至該測試。

  ![Image](./media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>診斷並修正測試失敗

從失敗的測試，您可以輕鬆地針對產品程式碼進行偵錯、做出編輯，並繼續開發應用程式。 由於 Live Unit Testing 是在背景執行，因此您不需要在偵錯、編輯和繼續的循環期間停止並重新啟動 Live Unit Testing。

例如，上圖所示的測試失敗，是因測試方法中錯誤假設非字母字元在傳遞到 [Char.IsLower](xref:System.Char.IsLower(System.Char)) 方法時，會傳回 `true` 而導致。 當我們更正測試方法之後，就發現所有測試均會通過。 當我們執行此動作時，不需暫停或停止 Live Unit Testing。

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing 和測試總管

一般而言，[測試總管] 會提供介面，讓您能夠針對測試結果進行執行、偵錯及分析。 Live Unit Testing 會與 [測試總管] 整合。 若未啟用或已停止 Live Unit Testing，[測試總管] 就會顯示上次執行測試時的單元測試狀態。 原始程式碼變更需要您重新執行測試。 相反地，啟用 Live Unit Testing 時，[測試總管] 中的單元測試狀態會立即更新。 您不再需要明確地執行單元測試。 

不過，在 Live Unit Testing 自動執行並更新測試結果，以及從 [測試總管] 明確執行測試之間，具有一些差異。 它們包括：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。 
- Live Unit Testing 不會建立新的應用程式定義域來執行測試，而是從預設的定義域執行測試。 從 [測試總管] 視窗執行的測試會建立新的應用程式定義域。
- Live Unit Testing 會循序執行每個測試組件中的測試。 如果您從 [測試總管] 視窗執行多個測試，並選取 [平行執行測試] 按鈕，測試將會平行執行。

## <a name="including-and-excluding-test-projects-and-test-methods"></a>包含和排除測試專案與測試方法

針對具有許多測試專案的方案，您可以控制要讓哪些專案，以及專案中的哪些個別方法參與 Live Unit Testing。 

例如，如果您的方案具有數百個測試專案，則您可以選取一組目標測試專案來參與 Live Unit Testing。 若要在單元測試中選取個別專案，請在啟動 Live Unit Testing 之後執行下列動作：

1.  以滑鼠右鍵按一下 [方案總管] 中的方案，然後依序選擇 [即時測試] 和 [排除] 來排除整個方案。
2.  以滑鼠右鍵按一下您想要包含於測試中的每個測試專案，然後依序選擇 [即時測試] 和 [包含]。
 
您可以使用程式碼編輯器視窗來包含或排除個別的測試方法。 以滑鼠右鍵按一下程式碼編輯器視窗中的測試方法特徵標記，然後依序選取 [即時測試] 和 [包含]，或是 [即時測試] 和 [排除]。 

或者，您也可以套用 [<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx) 屬性，來以程式設計方式排除方法、類別或結構，使它們無法在 Live Unit Testing 中報告它們的涵蓋範圍。

Live Unit Testing 會將包含/排除狀態儲存為使用者設定，並在關閉並重新開啟方案時記住該狀態。 

## <a name="see-also"></a>請參閱

[Live Unit Testing 部落格 (英文)](https://go.microsoft.com/fwlink/?linkid=842514)   
[Live Unit Testing 常見問題集](live-unit-testing-faq.md)    
[Channel 9 影片：Visual Studio 2017 中的 Live Unit Testing (英文)](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)


