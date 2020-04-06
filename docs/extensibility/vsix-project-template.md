---
title: VSIX 專案樣本 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697927"
---
# <a name="vsix-project-template"></a>VSIX 專案範本

您可以使用 VSIX 專案範本在 VSIX 專案中包裝一個或多個 Visual Studio 擴展,然後在[可視化工作室應用商店](https://marketplace.visualstudio.com/)網站上發佈包。

 VSIX 部署支援 VS 組件、程式集、MEF 元件、專案範本、專案範本、工具箱控制項和自訂擴充類型。

> [!NOTE]
> 要使用 VSIX 項目,必須安裝視覺化工作室 SDK。 有關可視化工作室 SDK 的詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="where-to-find-the-vsix-project-template"></a>在哪裡可以找到 VSIX 專案樣本

通過搜索"vsix","**新專案**"對話框中提供了 VSIX 專案範本。  有 C# 和可視化基本版本。

> [!TIP]
> 應確保在 **「新專案」** 對話框頂部的下拉列表框中指定 .NET Framework 4.5 或更高版本。

## <a name="uses-of-the-vsix-project-template"></a>VSIX 專案樣本的使用

VSIX 專案樣本有兩個主要用途:

- 部署專案範本、專案範本和擴展。

- 將多個擴展的輸出包裝到一個部署包中。

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>在空 VSIX 專案中包裝擴充

通過將現有擴展或尚未具有 VSIX 支援的擴展打包在空 VSIX 專案中,可以打包現有擴展或尚未具有 VSIX 支援的擴展。 要包裝的擴展必須為[VSIX 架構](../extensibility/vsix-extension-schema-2-0-reference.md)支援的類型。

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>使用 VSIX 專案包裝擴充

1. 生成構成擴展的專案。

2. 使用 VSIX 專案樣本建立**VSIX 專案**。

    *源.擴展.vsixmanifest*在**清單設計器**中打開。

3. 在「**資產**」選項卡上,選擇「**新建」** 按鈕。

    將顯示「**添加新資產**」對話框。

4. 在**型態型態清單**中,選擇要新增的擴充型態。

5. 要新增目前解決方案中包含的延伸或內容元素(例如,項範本或已編譯的程式集),執行以下步驟:

   1. 在 **「來源」** 清單中,選擇**目前解決方案中的項目**。

   2. 在**項目清單**中,選擇副檔名的名稱。

   3. **在此資料夾框中的「嵌入」** 框中,輸入要嵌入資產的資料夾的名稱,然後選擇 **「確定**」按鈕。

6. 要新增目前解決方案中未包含的延伸或內容元素,執行以下步驟:

   1. 在 **「源」** 清單框中,選擇**檔案系統上的「 檔案**」 。

   2. 在 **「路徑」** 欄位中,輸入已編譯或壓縮擴展檔的完整路徑,或使用 **「瀏覽」** 按鈕瀏覽到該檔。

   3. **在此資料夾框中的「嵌入」** 框中,輸入要嵌入資產的資料夾的名稱,然後選擇 **「確定**」按鈕。

7. 如果希望包包含其他擴展,請以相同的方式添加它們。

8. 建置方案。

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成包含 VSIX 清單檔、[Content_Types]*.xml*檔案以及添加到專案的所有擴展資源的所有 *.vsix*檔。

## <a name="see-also"></a>另請參閱

- [VSIX 延伸架構 2.0 引用](../extensibility/vsix-extension-schema-2-0-reference.md)
- [尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)
