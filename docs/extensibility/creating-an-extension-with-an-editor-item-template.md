---
title: 使用編輯器項目樣本建立延伸 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739500"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>使用編輯器項目建立延伸
您可以使用 Visual Studio SDK 中包含的專案範本建立基本編輯器擴展,向編輯器添加分類器、修飾和邊距。 編輯器項範本可用於可視化 C# 或可視化基本 VSIX 專案。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-classifier-extension"></a>建立分類器延伸
 編輯器分類器項目製作編輯器分類器,用於在任何文字檔中為適當的文字(本例中為所有內容)提供顏色。

1. 在 **「新項目**」對話框中,展開**視覺化 C#** 或**視覺化基本,** 然後按下「**可擴充性**」 。。 在 **「樣本」** 窗格中,選擇**VSIX 專案**。 在 [名稱]**** 方塊中，輸入 `TestClassifier`。 按一下 [確定]  。

2. 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 跳到視覺化 C#**擴充性**節點並選擇**編輯器類別器**。 保留預設檔名 *(EditorClassifier1.cs)。*

3. 有四個代碼檔,如下所示:

    - *EditorClassifier1.cs*包含`EditorClassifier1`類別 。

    - *EditorClassifier1ClassificationDefinition.cs*包含`EditorClassifier1ClassificationDefinition`類別 。

    - *EditorClassifier1Format.cs*包含該`EditorClassifier1Format`類。

    - *EditorClassifier1Provider.cs*包含`EditorClassifier1Provider`該 類。

4. 建置此專案並開始偵錯。 視覺工作室的實驗實例出現。

     如果打開文本檔,則所有文本都以紫色背景下劃線。

## <a name="create-a-text-relative-adornment-extension"></a>建立文字的修飾延伸
 編輯器文字修飾範本建立一個文本相關修飾,透過使用具有紅色輪廓和藍色背景的框來修飾文本字元「a」的所有實例。 它是與文本相關的,因為框始終覆蓋"a"字元,即使它們被移動或重新格式化也是如此。

1. 在 **「新項目**」對話框中,展開**視覺化 C#** 或**視覺化基本,** 然後按下「**可擴充性**」 。。 在 **「樣本」** 窗格中,選擇**VSIX 專案**。 在 [名稱]**** 方塊中，輸入 `TestAdornment`。 按一下 [確定]  。

2. 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 跳到視覺化 C#**擴充性**節點並選擇**編輯器文字修飾**。 保留預設檔名 *(TextAdornment1.cs/vb*)。

3. 有兩個代碼檔,如下所示:

    - *TextAdornment1.cs*包含`TextAdornment1`該 類。

    - *TextAdornment1TextViewCreationListener.cs*包含該`TextAdornment1TextViewCreationListener`類。

4. 建置此專案並開始偵錯。 出現實驗實例。 如果打開文字檔,文本中的所有"a"字元在藍色背景中以紅色表示。

## <a name="create-a-viewport-relative-adornment-extension"></a>建立視口相對修飾延伸
 編輯器視口裝飾範本創建一個視口相對修飾,該裝飾在視口右上角添加了一個帶有紅色輪廓的紫色框。

> [!NOTE]
> **視口**是當前顯示的文本視圖的區域。

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>使用編輯器檢視埠裝飾樣本建立視口修飾延伸

1. 在 **「新項目**」對話框中,展開**視覺化 C#** 或**視覺化基本,** 然後按下「**可擴充性**」 。。 在 **「樣本」** 窗格中,選擇**VSIX 專案**。 在 [名稱]**** 方塊中，輸入 `ViewportAdornment`。 按一下 [確定]  。

2. 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 跳到視覺化 C#**擴充性**節點並選擇**編輯器視口修飾**。 保留預設檔名 *(ViewportAdornment1.cs/vb*)。

3. 有兩個代碼檔,如下所示:

    - *ViewportAdornment1.cs*包含`ViewportAdornment1`該 類。

    - *ViewportAdornment1TextViewCreationListener.cs*包含`ViewportAdornment1TextViewCreationListener`類

4. 建置此專案並開始偵錯。 出現實驗實例。 如果創建新的文本檔,則視口右上角將顯示一個帶有紅色輪廓的紫色框。

## <a name="create-a-margin-extension"></a>建立邊界
 編輯器邊距範本創建一個綠色邊距,與單詞 "*你好世界!* 在水平滾動條下方。

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>使用編輯器邊界

1. 在 **「新項目**」對話框中,展開**視覺化 C#** 或**視覺化基本,** 然後按下「**可擴充性**」 。。 在 **「樣本」** 窗格中,選擇**VSIX 專案**。 在 [名稱]**** 方塊中，輸入 `MarginExtension`。 按一下 [確定]  。

2. 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 跳到視覺化 C#**擴充性**節點並選擇**編輯器邊距**。 保留預設檔名 (EditorMargin1.cs/vb)。

3. 有兩個代碼檔,如下所示:

    - *EditorMargin1.cs*包含`EditorMargin1`該 類。

    - *EditorMargin1Factory.cs*包含`EditorMargin1Factory`該 類。

4. 生成此專案並開始調試。 出現實驗實例。 如果打開文字檔,水準滾動欄下方將顯示一個綠色邊距,該邊距的單詞 **"Hello EditorMargin1"。"表示**"

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
