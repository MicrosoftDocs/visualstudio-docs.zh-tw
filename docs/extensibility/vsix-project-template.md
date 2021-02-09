---
title: VSIX 專案範本 |Microsoft Docs
description: 瞭解如何使用 VSIX 專案範本將 Visual Studio 擴充功能包裝在 VSIX 專案中，然後在 Visual Studio Marketplace 上發佈封裝。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d346826c97bfa0ed885579d4816c452dbed9a2d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905717"
---
# <a name="vsix-project-template"></a>VSIX 專案範本

您可以使用 VSIX 專案範本，將一個或多個 Visual Studio 擴充功能包裝在 VSIX 專案中，然後在 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 的網站上發行封裝。

 VSIX 部署支援 Vspackage、元件、MEF 元件、專案範本、專案範本、工具箱控制項和自訂延伸模組類型。

> [!NOTE]
> 若要使用 VSIX 專案，您必須安裝 Visual Studio SDK。 如需 Visual Studio SDK 的詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="where-to-find-the-vsix-project-template"></a>要在哪裡尋找 VSIX 專案範本

您可以在 [ **新增專案** ] 對話方塊中，藉由搜尋 "vsix" 來取得 VSIX 專案範本。  C # 和 Visual Basic 版本都有。

> [!TIP]
> 您應該確定已在 [ **新增專案** ] 對話方塊頂端的下拉式清單方塊中指定 .NET Framework 4.5 或更高版本。

## <a name="uses-of-the-vsix-project-template"></a>使用 VSIX 專案範本

VSIX 專案範本有兩個主要用途：

- 部署專案範本、專案範本和延伸模組。

- 將多個擴充功能的輸出包裝成一個部署套件。

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>封裝空白 VSIX 專案中的延伸模組

您可以將現有的延伸模組或尚未具有 VSIX 支援的擴充功能包裝在空白 VSIX 專案中。 要包裝的副檔名必須是 [VSIX 架構](../extensibility/vsix-extension-schema-2-0-reference.md)所支援的類型。

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>使用 VSIX 專案封裝擴充功能

1. 建立構成您延伸模組的專案。

2. 使用 **Vsix 專案** 範本建立 vsix 專案。

    *Extension.vsixmanifest* 會在 **資訊清單設計** 工具中開啟。

3. 在 [ **資產** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

    [ **加入新資產** ] 對話方塊隨即出現。

4. 在 [ **類型** ] 清單中，選擇要新增的延伸模組類型。

5. 若要加入目前方案中包含的延伸模組或內容元素 (例如，專案範本或已編譯的元件) ，請執行下列步驟：

   1. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

   2. 在 [ **專案** ] 清單中，選擇延伸模組的名稱。

   3. 在 [ **內嵌于這個資料夾** ] 方塊中，輸入要在其中內嵌資產的資料夾名稱，然後選擇 [ **確定]** 按鈕。

6. 若要加入目前解決方案中未包含的延伸模組或內容元素，請執行下列步驟：

   1. 在 [ **來源** ] 清單方塊中，選擇 **檔案系統上** 的 [檔案]。

   2. 在 [ **路徑** ] 欄位中，輸入已編譯或壓縮的延伸模組檔案的完整路徑，或使用 [ **流覽]** 按鈕流覽至該檔案。

   3. 在 [ **內嵌于這個資料夾** ] 方塊中，輸入要在其中內嵌資產的資料夾名稱，然後選擇 [ **確定]** 按鈕。

7. 如果您想要讓套件包含其他擴充功能，請以相同的方式加入它們。

8. 建置方案。

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建立包含 VSIX 資訊清單檔的 *.vsix* 檔案、[Content_Types]*.xml* 檔案，以及您新增至專案的所有延伸模組資產。

## <a name="see-also"></a>另請參閱

- [VSIX 延伸架構2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)
- [尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)
