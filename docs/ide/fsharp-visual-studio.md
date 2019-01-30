---
title: F# 工具
description: 了解 F# 支援哪些 Visual Studio 功能。
ms.date: 07/11/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0eaaf9f82bea6fdba86b6404cfc0ab36384805ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920626"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>在 Visual Studio 中使用 Visual F# 進行開發

本文包含適用於 F# 開發的 Visual Studio 功能相關資訊。

## <a name="install-f-support"></a>安裝 F# 支援

若要在 Visual Studio 中使用 F# 進行開發，請先安裝 **.NET 桌面開發**工作負載 (若尚未安裝的話)。 您可以透過 Visual Studio 安裝程式安裝 Visual Studio 工作負載，選取 [工具] > [取得工具與功能] 即可開啟該安裝程式。

![Visual Studio 中的 .NET 桌面開發工作負載](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F# 專案功能

有各種專案和項目範本可供 Visual Studio 中的 F# 使用。 下圖顯示適用於 .NET Core 和 .NET Standard　的一些 F# 專案範本：

![Visual Studio 中的 F# 專案範本](media/fsharp-project-templates.png)

下圖顯示一些 F# 項目範本：

![Visual Studio 中的 F# 項目範本](media/fsharp-item-templates.png)

如需資料存取之項目範本的詳細資訊，請參閱[F# 型別提供者](/dotnet/fsharp/tutorials/type-providers/index)。

下表摘要說明 F# 專案屬性中的功能：

|專案設定|F# 支援？|注意|
|---------------|----------------|-----|
|資源檔|是||
|建置、偵錯和參考設定|是||
|多目標|是||
|圖示和資訊清單|否|透過編譯器命令列選項提供。|
|ASP.NET 用戶端服務|否||
|ClickOnce|否|適用時，請使用另一種 .NET Framework 語言的用戶端專案。|
|強式命名|否|透過編譯器命令列選項提供。|
|組件的發佈和版本控制|否||
|程式碼分析|否|程式碼分析工具可以手動執行，或作為建置後命令一部分執行。|
|安全性 (變更信任層級)|否||

## <a name="project-designer"></a>專案設計工具

[專案設計工具] 包含依相關功能分組的數個專案屬性頁。 可用於 F# 專案的頁面大部分是可用於其他語言的頁面子集，下表將描述這些頁面。 還提供了對應至 C# [專案設計工具] 頁面的連結。

|[專案設計工具] 頁面|相關連結|說明|
| - |-------------|-----------|
|應用程式|[專案設計工具、應用程式頁面](reference/application-page-project-designer-csharp.md)|可讓您指定應用程式層級設定和屬性，例如您正在建立程式庫還是可執行檔、應用程式是以哪些 .NET Framework 版本為目標，以及應用程式使用的資源檔儲存所在位置的相關資訊。|
|組建|[專案設計工具、建置頁](reference/build-page-project-designer-csharp.md)|可讓您控制如何編譯程式碼。|
|建置事件|[專案設計工具、建置事件頁面](reference/build-events-page-project-designer-csharp.md)|可讓您指定要在編譯前後執行的命令。|
|偵錯|[專案設計工具、偵錯頁面](reference/debug-page-project-designer.md)|可讓您控制應用程式在偵錯期間執行的方式。 這包括要使用哪些命令與應用程式的啟動目錄為何，以及您要啟用的任何特殊偵錯模式，例如原生程式碼和 SQL。|
|套件 (僅限 .NET SDK)|N/A|可讓您在以 NuGet 套件形式發佈時，定義 NuGet 套件的中繼資料。|
|參考路徑|[管理專案中的參考](managing-references-in-a-project.md)|可讓您指定要搜尋程式碼相依組件的位置。|
|資源 (僅限 .NET SDK)|N/A|可讓您產生並管理預設資源檔。|

### <a name="f-specific-settings"></a>F#-特定設定

下表摘要說明 F# 專用的設定：

|[專案設計工具] 頁面|設定|說明|
| - |-------|-----------|
|組建|產生 tail 呼叫|如果選取此設定，則可讓您使用尾端 Microsoft Intermediate Language (MSIL) 指令。 這會導致堆疊框架重複用於尾端遞迴函式。 相當於 `--tailcalls` 編譯器選項。|
|組建|其他旗標|可讓您指定其他編譯器命令列選項。|

## <a name="code-and-text-editor-features"></a>程式碼和文字編輯器功能

F# 支援 Visual Studio 程式碼和文字編輯器的下列功能：

|功能|說明|F# 支援？|
|-------|-----------|----------------|
|自動註解|可讓您註解或取消註解程式碼區段。|是|
|自動格式化|使用標準的縮排和樣式重新格式化程式碼。|否|
|書籤|可讓您在編輯器中儲存位置。|是|
|變更縮排|將選取行縮排或取消縮排。|是|
|智慧縮排|根據 F# 範圍規則，自動縮排和取消縮排資料指標。|是|
|[尋找及取代文字](finding-and-replacing-text.md)|可讓您在檔案、專案或解決方案中搜尋，並且可能變更文字。|是|
|移至 .NET Framework API 的定義|當資料指標位於 .NET Framework API 時，會顯示從 .NET Framework 中繼資料產生的程式碼。|否|
|移至使用者定義 API 的定義|當資料指標位於您定義的程式實體時，將資料指標移至您的程式碼中定義該實體的位置。|是|
|移至行|可讓您依據行號移至檔案中的特定行。|是|
|檔案頂端的巡覽列|可讓您依據函式名稱 (舉例來說) 跳至程式碼中的位置。|是|
|區塊結構輔助線|顯示表示 F# 範圍的輔助線，也可以將滑鼠停留在其上以進行預覽。|是|
|[大綱](outlining.md)|可讓您摺疊程式碼區段以建立更精簡的檢視。|是|
|定位點化|將空格轉換為定位點。|是|
|輸入顏色標示|以特殊的色彩顯示定義的類型名稱。|是|
|快速尋找。 請參閱 [尋找] 和 [尋找及取代] 視窗。|可讓您在檔案或專案中搜尋。|是|
|**Ctrl**+**按一下**以前往 [移至定義]|可讓您按住 **Ctrl** 並按一下 F# 符號，以叫用 [移至定義]。|是|
|從 QuickInfo 移至定義|工具提示內可叫用 [移至定義] 的可按式符號。|是|
|移至全部|透過 **Ctrl**+**T** 為所有的 F# 建構啟用全域、模糊比對巡覽。|是|
|內嵌重新命名|重新命名符號內嵌的所有項目。|是|
|尋找所有參考|在程式碼基底中尋找符號的所有項目。|是|
|簡化名稱程式碼修正|移除 F# 符號不必要的限定詞。|是|
|移除未使用的 `open` 陳述式程式碼修正|移除文件中所有不必要的 `open` 陳述式。|是|
|未使用的值程式碼修正|建議將未使用的識別項重新命名為底線。|是|

如需在 Visual Studio 中編輯程式碼和文字編輯器功能的一般資訊，請參閱[在編輯器中撰寫程式碼](writing-code-in-the-code-and-text-editor.md)。

## <a name="intellisense-features"></a>Intellisense 功能

下表摘要說明 F# 支援和不支援的 IntelliSense 功能：

|功能|說明|F# 支援？|
|-------|-----------|----------------|
|自動實作介面|產生介面方法的程式碼虛設常式。|是|
|程式碼片段|將來自常見程式碼建構程式庫的程式碼插入主題中。|否|
|自動完成文字|在您鍵入時完成單字和名稱，藉以省去鍵入工作。|是|
|自動完成|啟用此設定時，會導致文字自動完成在您鍵入時選取第一個相符項目，而不是等到您選取其中一個項目，或按下 **Ctrl**+**空格鍵**。|是|
|為未開啟命名空間中的符號提供自動完成|利用自動完成，建議使用位於未開啟之命名空間中的相符符號，提供以在選取時使用對應的 `open` 陳述式完成。|是|
|產生程式碼項目|可讓您產生各種建構的虛設常式程式碼。|否|
|列出成員|當您鍵入成員存取運算子 (.) 時，顯示類型的成員。|是|
|組合管理 Using/Open|組織 C# 中的 **using** 陳述式或 F# 中的 **open** 指示詞所參考的命名空間。|否|
|參數資訊|當您鍵入函式呼叫時，顯示參數的實用資訊。|是|
|快速諮詢|顯示程式碼中任一識別項的完整宣告。|是|
|自動以大括號完成|以交易方式自動完成 F# 大括弧類型的語法建構。|是|

如需 IntelliSense 的一般資訊，請參閱[使用 IntelliSense](using-intellisense.md)。

## <a name="debugging-features"></a>偵錯功能

下表摘要說明對 F# 程式碼進行偵錯時可供使用的功能：

|功能|說明|F# 支援？|
|-------|-----------|----------------|
|自動變數視窗|顯示自動或暫存變數。|否|
|中斷點|可讓您在偵錯期間的特定時間點暫停程式碼執行。|是|
|條件式中斷點|啟用中斷點，以測試可判斷是否應該暫停執行的條件。|是|
|編輯後繼續|可讓您對執行中的程式進行偵錯時，不需停止再重新啟動偵錯工具，即可修改和編譯程式碼。|否|
|運算式評估工具|在執行階段評估並執行程式碼。|否，但是可以使用 C# 運算式評估工具，雖然您必須使用 C# 語法。|
|歷程偵錯|可讓您逐步執行先前執行的程式碼。|是|
|[區域變數] 視窗|顯示本機定義的值和變數。|是|
|執行至游標處|可讓您執行程式碼，直到觸逹包含資料指標的那一行為止。|是|
|逐步執行|可讓您繼續執行，並移入任何函式呼叫。|是|
|不進入函式|可讓您在目前的堆疊框架中繼續執行，並跳過任何函式呼叫。|是|

如需 Visual Studio 偵錯工具的一般資訊，請參閱[在 Visual Studio 中偵錯](../debugger/index.md)。

## <a name="additional-tools"></a>其他工具

下表摘要說明 Visual Studio 工具中的 F# 支援。

|工具|說明|F# 支援？|
|----|-----------|----------------|
|呼叫階層|顯示程式碼中函式呼叫的巢狀結構。|否|
|程式碼度量|收集程式碼的相關資訊，例如行數。|否|
|類別檢視|提供專案中以類型為基礎的程式碼檢視。|否|
|[錯誤清單視窗](reference/error-list-window.md)|顯示程式碼中的錯誤清單。|是|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|可讓您鍵入 (或複製並貼上) F# 程式碼並立即執行它，這與建置專案無關。 F# 互動式視窗是讀取、評估、列印迴圈 (REPL)。|是|
|物件瀏覽器|可讓您檢視組件中的類型。|已編譯組件中顯示的 F# 類型與您撰寫的 F# 類型不完全相同。 您可以瀏覽 F# 類型的已編譯表示方式，但您無法檢視從 F# 顯示的類型。|
|[輸出視窗](reference/output-window.md)|顯示組建輸出。|是|
|效能分析|提供工具來測量程式碼的效能。|是|
|屬性視窗|在擁有焦點的開發環境中顯示物件的屬性，並啟用其編輯功能。|是|
|伺服器總管|提供與各種伺服器資源互動的方式。|是|
|底下提供說明，包括方案總管|可讓您檢視及管理專案和檔案。|是|
|工作清單|可讓您管理與程式碼相關的工作項目。|否|
|測試專案|提供協助您測試程式碼的功能。|否|
|工具箱|顯示包含可拖曳物件的索引標籤，例如控制項和文字或程式碼區段。|是|

## <a name="see-also"></a>另請參閱

- [F# 指南 (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio 中的 F# 使用者入門](/dotnet/fsharp/get-started/get-started-visual-studio)