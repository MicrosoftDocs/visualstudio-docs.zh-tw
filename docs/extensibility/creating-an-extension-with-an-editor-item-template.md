---
title: 使用編輯器專案範本建立延伸模組 |Microsoft Docs
description: 瞭解如何在 Visual Studio SDK 中使用專案範本，以建立可將分類器、裝飾和邊界新增至編輯器的基本編輯器延伸模組。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06c3fbfabb4eccc08e528aef913e1c1ba502cbf1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089130"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>使用編輯器專案範本建立擴充功能
您可以使用 Visual Studio SDK 中包含的專案範本，來建立可將分類器、裝飾和邊界新增至編輯器的基本編輯器延伸模組。 編輯器專案範本適用于 Visual c # 或 Visual Basic VSIX 專案。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-classifier-extension"></a>建立分類器擴充功能
 編輯器分類專案範本會建立編輯器分類器，以在此案例中為適當的文字進行色彩， (在任何文字檔中) 的所有專案。

1. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** ]， **然後按一下 [** 擴充性]。 在 [ **範本** ] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]  方塊中，輸入 `TestClassifier`。 按一下 [確定]  。

2. 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [Visual c **# 擴充** 性] 節點，然後選取 [ **編輯器分類器**]。 將預設的檔案名保留 (*EditorClassifier1* ]) 。

3. 有四個程式碼檔案，如下所示：

    - *EditorClassifier1* 包含 `EditorClassifier1` 類別。

    - *EditorClassifier1ClassificationDefinition* 包含 `EditorClassifier1ClassificationDefinition` 類別。

    - *EditorClassifier1Format* 包含 `EditorClassifier1Format`  類別。

    - *EditorClassifier1Provider* 包含 `EditorClassifier1Provider` 類別。

4. 建置此專案並開始偵錯。 Visual Studio 的實驗實例隨即出現。

     如果您開啟文字檔，所有文字都會加上紫色背景的底線。

## <a name="create-a-text-relative-adornment-extension"></a>建立文字相對裝飾擴充功能
 編輯器文字裝飾範本會建立文字相對裝飾，以使用具有紅色外框和藍色背景的方塊裝飾文字字元 ' a ' 的所有實例。 它是文字相關的，因為 box 一律會覆迭 ' a ' 字元，即使它們是移動或重新格式化。

1. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** ]， **然後按一下 [** 擴充性]。 在 [ **範本** ] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]  方塊中，輸入 `TestAdornment`。 按一下 [確定]  。

2. 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [ **編輯器文字裝飾**]。 保留預設檔案名 (*TextAdornment1 .cs/vb*) 。

3. 有兩個程式碼檔，如下所示：

    - *TextAdornment1* 包含 `TextAdornment1` 類別。

    - *TextAdornment1TextViewCreationListener* 包含 `TextAdornment1TextViewCreationListener` 類別。

4. 建置此專案並開始偵錯。 實驗實例隨即出現。 如果您開啟文字檔，則文字中的所有 ' a ' 字元都會以紅色標示為藍色背景。

## <a name="create-a-viewport-relative-adornment-extension"></a>建立視口相關裝飾擴充功能
 「編輯器區裝飾」範本會建立一個區相關裝飾，此裝飾會將具有紅色外框的紫色方塊新增至區右上角。

> [!NOTE]
> 此圖 **區** 是目前顯示之文字視圖的區域。

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>使用編輯器區裝飾範本建立視口裝飾擴充功能

1. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** ]， **然後按一下 [** 擴充性]。 在 [ **範本** ] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]  方塊中，輸入 `ViewportAdornment`。 按一下 [確定]  。

2. 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [ **編輯器區裝飾**]。 保留預設檔案名 (*ViewportAdornment1 .cs/vb*) 。

3. 有兩個程式碼檔，如下所示：

    - *ViewportAdornment1* 包含 `ViewportAdornment1` 類別。

    - *ViewportAdornment1TextViewCreationListener* 包含 `ViewportAdornment1TextViewCreationListener` 類別

4. 建置此專案並開始偵錯。 實驗實例隨即出現。 如果您建立新的文字檔，則會在此區的右上角顯示具有紅色外框的紫色方塊。

## <a name="create-a-margin-extension"></a>建立邊界延伸
 編輯器邊界範本會建立與單字 **Hello world！* 一起出現的綠色邊界 下方的水準捲軸。

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>使用編輯器邊界範本建立邊界延伸模組

1. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** ]， **然後按一下 [** 擴充性]。 在 [ **範本** ] 窗格中，選取 [ **VSIX 專案**]。 在 [名稱]  方塊中，輸入 `MarginExtension`。 按一下 [確定]  。

2. 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [ **編輯器邊界**]。 保留預設檔案名 (EditorMargin1 .cs/vb) 。

3. 有兩個程式碼檔，如下所示：

    - *EditorMargin1* 包含 `EditorMargin1` 類別。

    - *EditorMargin1Factory* 包含 `EditorMargin1Factory` 類別。

4. 建立此專案並開始進行調試。 實驗實例隨即出現。 如果您開啟文字檔，則會在水準捲軸下方顯示具有 **Hello EditorMargin1** 單字的綠色邊界。

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
