---
title: XAML 錯誤和警告
description: 瞭解 Visual Studio 中的 XAML 錯誤和警告，包括錯誤的分類方式、如何取得錯誤資訊，以及如何尋找修正這些錯誤的選項。
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33cdc11eb5531fd2325bd90912dc22a105711c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903649"
---
# <a name="xaml-errors-and-warnings"></a>XAML 錯誤和警告

撰寫 XAML 時，Visual Studio 會在您鍵入的同時分析程式碼。 偵測到錯誤時，程式碼行上會出現曲線。 將滑鼠指標停留在曲線上時，即會顯示錯誤或警告的詳細資訊。 針對某些錯誤和警告，會顯示快速動作燈泡，並使用 **Ctrl** + **。** 鍵盤快速鍵以顯示可修正問題的選項。

## <a name="error-types"></a>錯誤類型

系統中的多項工具會在幕後平行分析 XAML。 依據偵測到錯誤的工具來看，XAML 錯誤可以區分為下列三種類型：

|**偵測到錯誤的項目**|**錯誤碼格式**|**Visual Studio 版本**|
| - |-----------------| - |
|XAML 語言服務 (XAML 編輯器)|XLSxxxx| 所有版本 |
|XAML 設計工具|XDGxxxx| 所有版本 | 
|XAML 編輯後繼續|XECxxxx| Visual Studio 2019 16.1 版或更早版本 |
|XAML 熱重新載入 | XHRxxxx | Visual Studio 2019 16.2 版或更新版本 |

如需 XAML 編輯品牌再造的詳細資訊 & 繼續 XAML 熱重新載入的詳細資訊，請參閱我們的[版本](/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling)資訊

> [!Note]
> 並非所有錯誤或警告都有對應的程式碼。 這種錯誤通常是 XAML 設計工具的錯誤。

## <a name="suppress-xaml-designer-errors"></a>隱藏 XAML 設計工具的錯誤

選取 [工具] > [選項]，然後選取 [文字編輯器] > [XAML] > 其他]，以開啟 [選項] 對話方塊。

取消選取 [Show errors detected by the XAML designer] (顯示 XAML 設計工具所偵測到的錯誤) 核取方塊。

![隱藏 XAML 設計工具的錯誤](media/suppress_xaml_designer_errors.png)