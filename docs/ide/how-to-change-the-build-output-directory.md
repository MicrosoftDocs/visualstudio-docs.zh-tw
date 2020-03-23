---
title: 如何：變更組建輸出目錄
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37342796f2dd94138136bb837cf6007d19d350c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114262"
---
# <a name="how-to-change-the-build-output-directory"></a>如何：變更組建輸出目錄

您可以根據組態 (針對偵錯及/或版本) 指定專案所產生的輸出位置。

## <a name="change-the-build-output-directory"></a>變更組建輸出目錄

1. 若要開啟專案屬性頁面，請以滑鼠右鍵按一下 [方案總管]**** 中的專案節點，然後選取 [屬性]****。

2. 根據您的專案類型，選取適當的索引標籤：

   - 若是 C#，請選取 [建置]**** 索引標籤。
   - 若是 Visual Basic，請選取 [編譯]**** 索引標籤。
   - 若是 C++ 或 JavaScript，請選取 [一般]**** 索引標籤。

3. 在頂端的組態下拉式清單中，選擇您想要變更其輸出檔位置的組態 ([偵錯]****、[發行]**** 或 [所有組態]****)。

4. 在頁面中尋找輸出路徑項目&mdash;因您的專案類型而異：

   - **輸出路徑**適用於 C++ 和 JavaScript 專案
   - **組建輸出路徑**適用於 Visual Basic 專案
   - **輸出目錄**適用於 Visual C++ 專案

   鍵入要產生輸出的目標路徑 (絕對或相對於根專案目錄)，或改為選擇 [瀏覽]**** 以瀏覽至該資料夾。

   ![適用於 Visual Studio C# 專案的輸出路徑](media/output-path.png)
   
   > [!NOTE]
   > 預設情況下，某些專案將在生成路徑中包括框架和運行時。 要更改此項，請按右鍵**解決方案資源管理器**中的專案節點，選擇 **"編輯專案檔案**"，然後添加以下內容：
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> 如果您指定的位置並未產生輸出，請確定您已正確選取 Visual Studio 的功能表列來建置對應組態 (例如 [偵錯]**** 或 [發行]****)。
>
> ![Visual Studio 2019 中的 [建置] 組態選擇器](media/build-configuration-chooser.png)

## <a name="see-also"></a>另請參閱

- [生成頁，專案設計器 （C#）](../ide/reference/build-page-project-designer-csharp.md)
- [一般屬性頁（專案）](/cpp/build/reference/general-property-page-project)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
