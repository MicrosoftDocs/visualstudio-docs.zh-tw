---
title: 使用編輯器專案範本建立擴充功能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91daa7e195435f33b93e6286cb19d820b4418d48
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903835"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>使用編輯器專案範本建立擴充功能
您可以使用包含在 Visual Studio SDK 中的專案範本來建立基本編輯器延伸模組，以將分類器、裝飾和邊界新增至編輯器。 編輯器專案範本適用于 Visual c # 或 Visual Basic VSIX 專案。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-classifier-extension"></a>建立分類器延伸模組
 編輯器分類器專案範本會建立編輯器分類器，以在任何文字檔中為適當的文字（在此案例中為所有專案）著色。

1. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或**Visual Basic** ，**然後按一下 [** 擴充性]。 在 [**範本**] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]**** 方塊中，輸入 `TestClassifier`。 按一下 [確定] 。

2. 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [**編輯器分類器**]。 保留預設檔案名（*EditorClassifier1.cs*）。

3. 有四個程式碼檔案，如下所示：

    - *EditorClassifier1.cs*包含 `EditorClassifier1` 類別。

    - *EditorClassifier1ClassificationDefinition.cs*包含 `EditorClassifier1ClassificationDefinition` 類別。

    - *EditorClassifier1Format.cs*包含 `EditorClassifier1Format` 類別。

    - *EditorClassifier1Provider.cs*包含 `EditorClassifier1Provider` 類別。

4. 建置此專案並開始偵錯。 Visual Studio 的實驗實例隨即出現。

     如果您開啟文字檔，所有文字都會以紫紅色背景加上底線。

## <a name="create-a-text-relative-adornment-extension"></a>建立文字相對裝飾擴充功能
 [編輯器文字裝飾] 範本會使用具有紅色外框和藍色背景的方塊，來建立文字相對裝飾，以裝飾文字字元 ' a ' 的所有實例。 它是文字相對的，因為方塊一律會重迭 ' a ' 字元，即使它們已移動或重新格式化亦然。

1. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或**Visual Basic** ，**然後按一下 [** 擴充性]。 在 [**範本**] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]**** 方塊中，輸入 `TestAdornment`。 按一下 [確定] 。

2. 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [**編輯器文字修飾**]。 保留預設檔案名（*TextAdornment1.cs/vb*）。

3. 有兩個程式碼檔案，如下所示：

    - *TextAdornment1.cs*包含 `TextAdornment1` 類別。

    - *TextAdornment1TextViewCreationListener.cs*包含 `TextAdornment1TextViewCreationListener` 類別。

4. 建置此專案並開始偵錯。 實驗實例隨即出現。 如果您開啟文字檔，文字中的 ' a ' 字元就會以紅色標示為藍色背景。

## <a name="create-a-viewport-relative-adornment-extension"></a>建立視口相對裝飾擴充功能
 [編輯器] [視口] [裝飾] 範本會建立一個 [視口] 相對裝飾，將具有紅色外框的紫色方塊加入至 [視口] 的右上角。

> [!NOTE]
> [**視口**] 是目前顯示的文字視圖區域。

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>使用編輯器的視口裝飾範本建立視口裝飾擴充功能

1. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或**Visual Basic** ，**然後按一下 [** 擴充性]。 在 [**範本**] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]**** 方塊中，輸入 `ViewportAdornment`。 按一下 [確定] 。

2. 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [編輯器] [**視口修飾**]。 保留預設檔案名（*ViewportAdornment1.cs/vb*）。

3. 有兩個程式碼檔案，如下所示：

    - *ViewportAdornment1.cs*包含 `ViewportAdornment1` 類別。

    - *ViewportAdornment1TextViewCreationListener.cs*包含 `ViewportAdornment1TextViewCreationListener` 類別

4. 建置此專案並開始偵錯。 實驗實例隨即出現。 如果您建立新的文字檔，則會在視口的右上角顯示具有紅色外框的紫色方塊。

## <a name="create-a-margin-extension"></a>建立邊界延伸模組
 [編輯器邊界] 範本會建立與 [*Hello world！* ] 字樣一起出現的綠色邊界 水準捲軸底下。

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>若要使用編輯器邊界範本建立邊界延伸

1. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或**Visual Basic** ，**然後按一下 [** 擴充性]。 在 [**範本**] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]**** 方塊中，輸入 `MarginExtension`。 按一下 [確定] 。

2. 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [**編輯器邊界**]。 保留預設檔案名（EditorMargin1.cs/vb）。

3. 有兩個程式碼檔案，如下所示：

    - *EditorMargin1.cs*包含 `EditorMargin1` 類別。

    - *EditorMargin1Factory.cs*包含 `EditorMargin1Factory` 類別。

4. 建立此專案並開始進行調試。 實驗實例隨即出現。 如果您開啟文字檔，則會在水準捲軸下方顯示具有「 **Hello EditorMargin1** 」字樣的綠色邊界。

## <a name="see-also"></a>另請參閱
- [語言服務和編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
