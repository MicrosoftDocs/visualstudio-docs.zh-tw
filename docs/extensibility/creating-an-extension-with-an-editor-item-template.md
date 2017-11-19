---
title: "使用編輯器項目範本建立擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebfb54a289fe085f00c40df34256cfb2174f98fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>使用編輯器項目範本建立擴充功能
您可以使用隨附於 Visual Studio SDK 來建立基本的編輯器延伸模組加入至編輯器的分類器、 裝飾和邊界的項目範本。 編輯器項目範本可供 Visual C# 或 Visual Basic VSIX 專案。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-classifier-extension"></a>建立分類器擴充功能  
 編輯器分類器項目範本建立適當的文字的色彩編輯器分類器 (在此情況下，所有項目) 中的任何文字檔案。  
  
1.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic** ，然後按一下 **擴充性**。 在**範本**窗格中，選取**VSIX 專案**。 在 [名稱] 方塊中，輸入 `TestClassifier`。 按一下 [確定]。  
  
2.  在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 移至 Visual C#**擴充性**節點，然後選取**編輯器分類器**。 保留預設的檔案名稱 (EditorClassifier1.cs)。  
  
3.  有三個程式碼檔案，如下：  
  
    -   包含 EditorClassifier1.cs`EditorClassifier1`類別。  
  
    -   包含 EditorClassifier1ClassificationDefinition.cs`OEditorClassifier1ClassificationDefinition`類別。  
  
    -   包含 EditorClassifier1Format.cs`EditorClassifier1Format`類別。  
  
    -   包含 EditorClassifier1Provider.cs`EditorClassifier1Provider`類別。  
  
4.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
     如果您開啟文字檔，所有的文字會加上底線針對紫色的背景。  
  
## <a name="creating-a-text-relative-adornment-extension"></a>建立文字相對裝飾擴充功能  
 編輯器文字裝飾範本建立裝飾文字字元的所有執行個體相對文字的裝飾 'a' 使用具有紅色外框和藍色背景的方塊。 它是文字的相對因為方塊一律覆疊 'a' 字元，即使它們是移動或重新格式化。  
  
1.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic** ，然後按一下 **擴充性**。 在**範本**窗格中，選取**VSIX 專案**。 在 [名稱] 方塊中，輸入 `TestAdornment`。 按一下 [確定]。  
  
2.  在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 移至 Visual C#**擴充性**節點，然後選取**編輯器的文字裝飾**。 保留預設的檔案名稱 (TextAdornment1.cs/vb)。  
  
3.  有兩個程式碼檔案，如下：  
  
    -   包含 TextAdornment1.cs`TextAdornment1`類別。  
  
    -   包含 extAdornment1TextViewCreationListener.cs`TextAdornment1TextViewCreationListener`類別。  
  
4.  建置此專案並開始偵錯。 實驗執行個體隨即出現。 如果您開啟文字檔，以藍色背景的紅色描述文字中的所有 'a' 字元。  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>建立檢視區相對裝飾擴充功能  
 編輯器檢視區裝飾範本建立的檢視區相對裝飾，將它新增至具有檢視區的右上角的紅色外框的紫色方塊。  
  
> [!NOTE]
>  *檢視區*是目前顯示的文字 檢視的區域。  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>若要使用的編輯器檢視區裝飾範本建立的檢視區裝飾延伸模組  
  
1.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic** ，然後按一下 **擴充性**。 在**範本**窗格中，選取**VSIX 專案**。 在 [名稱] 方塊中，輸入 `ViewportAdornment`。 按一下 [確定]。  
  
2.  在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 移至 Visual C#**擴充性**節點，然後選取**編輯器檢視區裝飾**。 保留預設的檔案名稱 (ViewportAdornment1.cs/vb)。  
  
3.  有兩個程式碼檔案，如下：  
  
    -   包含 ViewportAdornment1.cs`ViewportAdornment1`類別。  
  
    -   包含 ViewportAdornment1TextViewCreationListener.cs`ViewportAdornment1TextViewCreationListener`類別  
  
4.  建置此專案並開始偵錯。 實驗執行個體隨即出現。 如果您建立新的文字檔，具有紅色外框紫色方塊會顯示在檢視區的右上角。  
  
## <a name="creating-a-margin-extension"></a>建立邊界擴充功能  
 編輯器邊界範本會建立與單字"Hello world ！"會出現綠色邊界 水平捲軸下方。  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>若要使用編輯器邊界範本建立的邊界延伸模組  
  
1.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic** ，然後按一下 **擴充性**。 在**範本**窗格中，選取**VSIX 專案**。 在 [名稱] 方塊中，輸入 `MarginExtension`。 按一下 [確定]。  
  
2.  在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 移至 Visual C#**擴充性**節點，然後選取**編輯器檢視區裝飾**。 保留預設的檔案名稱 (EditorMargin1.cs/vb)。  
  
3.  有兩個程式碼檔案，如下：  
  
    -   包含 EditorMargin1.cs`EditorMargin1`類別。  
  
    -   包含 EditorMargin1Factory.cs`EditorMargin1Factory`類別。  
  
4.  建置此專案，並開始偵錯。 實驗執行個體隨即出現。 如果您開啟文字檔，具有文字"Hello EditorMargin1 」 的綠色邊界會顯示水平捲軸下方。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)