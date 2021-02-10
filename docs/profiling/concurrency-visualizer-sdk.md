---
title: 並行視覺化檢視 SDK | Microsoft Docs
description: 瞭解如何使用並行視覺化 SDK 來檢測您的程式碼，以顯示標記。 標記是顯示在並行視覺化中以標記事件的圖示。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7b7cf8883e1a0c94756f7dcd9cc3a0a99744c9c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941095"
---
# <a name="concurrency-visualizer-sdk"></a>並行視覺化檢視 SDK
您可以使用並行視覺化檢視 SDK 檢測原始程式碼，以便在並行視覺化檢視中顯示其他資訊。 您可以在程式碼中將其他資料與階段和事件關聯。 這些額外的視覺效果稱為 *標記*。  如需入門逐步解說，請參閱[並行視覺化檢視 SDK 簡介](/archive/blogs/visualizeparallel/introducing-the-concurrency-visualizer-sdk)。

## <a name="properties"></a>屬性
 旗標、範圍和訊息各有兩個屬性︰分類和重要性。 在 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊中，您可以使用這些屬性來篩選顯示的標記集。 此外，這些屬性會影響標記的視覺化表示。 例如，旗標的大小用來表示重要性。 此外，色彩用來表示分類。

## <a name="basic-usage"></a>基本使用方式
 並行視覺化檢視會顯示您可以用來產生標記的預設提供者。 提供者已經和並行視覺化檢視一起註冊，您不需要執行任何動作就能在 UI 中顯示標記。

### <a name="c-and-visual-basic"></a>C# 和 Visual Basic
 在 C#、Visual Basic 和其他受控程式碼中，透過呼叫 [Markers](/previous-versions/hh694099(v=vs.140)) 類別中的方法來使用預設提供者。 它會公開四個產生標記的方法： [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29)、 [>enterspan](/previous-versions/hh694205(v=vs.140))、 [WriteMessage](/previous-versions/hh694161(v=vs.140))和 [WriteAlert](/previous-versions/hh694180(v=vs.140))。 視您是否要使用屬性的預設值而定，這些函式有多個多載。  最簡單的多載採用只有字串的參數，指定事件的描述。 描述會顯示在並行視覺化檢視報表中。

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>在 C# 或 Visual Basic 專案中加入 SDK 支援

1. 在功能表列上依序選擇 [分析]、[並行視覺化檢視]、[將 SDK 加入專案]。

2. 選取您要存取 SDK 的專案，然後選擇 [將 SDK 加入選取的專案] 按鈕。

3. 在程式碼中加入 imports 或 using 陳述式。

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 在 C++ 中，建立[marker_series 類別](../profiling/marker-series-class.md)物件，並使用它來呼叫函式。  `marker_series` 類別會顯示出三個函式來產生標記：[marker_series:: write_flag 方法](../profiling/marker-series-write-flag-method.md)、[marker_series:: write_message 方法](../profiling/marker-series-write-message-method.md) 和 [marker_series:: write_alert 方法](../profiling/marker-series-write-alert-method.md)。

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>在 C++ 或 C 專案中加入 SDK 支援

1. 在功能表列上依序選擇 [分析]、[並行視覺化檢視]、[將 SDK 加入專案]。

2. 選取您要存取 SDK 的專案，然後選擇 [將 SDK 加入選取的專案] 按鈕。

3. 對於 C++，請包含 `cvmarkersobj.h`。 對於 C，請包含 `cvmarkers.h`。

4. 在程式碼中加入 using 陳述式。

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. 建立 `marker_series` 物件，並將它傳遞至 `span` 建構函式。

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>自訂使用方式
 對於進階案例，並行視覺化檢視 SDK 會顯示出更多控制項。  有兩個主要概念與更進階的案例相關聯︰標記提供者和標記系列。 標記提供者是不同的 ETW 提供者 (各有不同的 GUID)。 標記系列是由一個提供者所產生的事件序列通道。 您可以使用它們來組織由標記提供者所產生的事件。

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>在 C# 或 Visual Basic 專案中使用新的標記提供者

1. 建立 [MarkerWriter](/previous-versions/hh694138(v=vs.140)) 物件。  建構函式取用 GUID。

2. 若要註冊提供者，請開啟並行視覺化檢視的 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊。  選取 [標記] 索引標籤，然後選擇 [加入新提供者] 按鈕。 在 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊中，輸入用來建立提供者的 GUID 和提供者的描述。

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>在 C++ 或 C 專案中使用新的標記提供者

1. 使用 `CvInitProvider` 函式來初始化 PCV_PROVIDER。  建構函式取用 GUID* 和 PCV_PROVIDER\*。

2. 若要註冊提供者，請開啟 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊。  選取 [標記] 索引標籤，然後選擇 [加入新提供者] 按鈕。 在此對話方塊中，輸入用來建立提供者的 GUID 和提供者的描述。

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>在 C# 或 Visual Basic 專案中使用標記系列

1. 若要使用新的 [MarkerSeries](/previous-versions/hh694127(v=vs.140))，請先使用 [MarkerWriter](/previous-versions/hh694138(v=vs.140)) 物件來建立它，然後直接從新系列產生標記事件。

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>在 C++ 專案中使用標記系列

1. 建立 `marker_series` 物件。  您可以從這個新系列產生事件。

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>在 C 專案中使用標記系列

1. 使用 `CvCreateMarkerSeries` 函式建立 PCV_MARKERSERIES。

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>另請參閱

|標題|描述|
|-----------|-----------------|
|[C + + 程式庫參考](../profiling/cpp-library-reference.md)|描述 C++ 的並行視覺化檢視 API。|
|[C 程式庫參考](../profiling/c-library-reference.md)|描述 C 的並行視覺化檢視 API。|
|[儀錶](/previous-versions/hh694104(v=vs.140))|描述 Managed 程式碼的並行視覺化檢視 API。|
|[並行視覺化檢視](../profiling/concurrency-visualizer.md)|使用並行方法所產生且包含執行緒執行資料的程式碼剖析資料檔案之檢視和報告的參考資訊。|