---
title: 選項對話方塊、環境、快速啟動
description: 瞭解如何使用 [環境] 區段中的 [快速啟動] 頁面，快速搜尋和執行 IDE 資產（例如選項、範本和功能表）的動作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: f1889b20f96e051867d470bc96df36b7018abdc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958202"
---
# <a name="quick-launch-environment-options-dialog-box"></a>選項對話方塊、環境、快速啟動

您可以使用 [快速啟動] 快速搜尋選項、範本、功能表這類 IDE 資產，並對其執行動作。 但無法使用 [快速啟動] 來搜尋程式碼和符號。 [快速啟動] 搜尋方塊位於功能表列的右上角，而且按 **Ctrl**+**Q** 即可存取。 在方塊中輸入搜尋字串即可。 若要搜尋包含 @ 的字串，請使用 ”@@”。

當您安裝 Visual Studio 時，預設會啟用 [快速啟動]。 您可以在功能表列上顯示或隱藏 [快速啟動]，方法是選擇 [工具] > [選項]。 展開 [環境] 節點，然後選擇 [快速啟動]。 選取或清除 [啟用快速啟動] 核取方塊。 您也可以啟用或停用這個頁面上的搜尋分類。

## <a name="category-list"></a>類別目錄清單

[快速啟動] 搜尋結果會出現在四個分類中：[最近用過的函式]、[功能表]、[選項] 和 [開啟文件]，並提供該分類的項目數。 若要依類別逐頁流覽搜尋結果，請選擇 **Ctrl** + **Q** 鍵，以顯示下一個類別的所有結果。 最後一個分類出現之後， **Ctrl** + **Q** 會顯示每個類別的一些結果。 按下 **Ctrl** + **Shift** + **Q** 以反向順序流覽類別。 若要檢視某個分類底下的所有搜尋結果，請選擇該分類名稱。

您可以使用下列快速鍵，限制搜尋特定分類。

|類別|快速鍵|快速鍵描述|
|--------------|--------------| - |
|最近使用|@mru<br /><br /> 例如， `@mru font`|最多顯示您 [最近用過的函式] 的五個項目。|
|功能表|@menu<br /><br /> 例如， `@menu project`|限制搜尋功能表項目。|
|選項|@opt<br /><br /> 例如， `@opt font`|限制搜尋 [選項] 對話方塊中的設定。|
|文件|@doc<br /><br /> 例如， `@doc program.cs`|限制搜尋符合搜尋準則之開啟文件的檔案名稱和路徑，但不會搜尋檔案本身內的文字。|

> [!NOTE]
> 您可以在 [   >  **選項**] 對話方塊的 [一般 **鍵盤**] 頁面上，變更快速鍵。

## <a name="show-previous-results"></a>顯示先前的結果

根據預設，您輸入的搜尋字詞不會在搜尋工作階段之間保留。 如果您搜尋某個字詞，然後將游標移出 [快速啟動] 區域再移回，則會清除搜尋字串。 若要保留搜尋結果，請移至 [選項] 對話方塊，並選擇 [快速啟動]，然後選取 [啟用快速啟動時顯示前一個搜尋的搜尋結果]。 核取方塊。 下次您執行搜尋、離開 [快速啟動] 區域並返回時，[快速啟動] 將會保留上次使用的搜尋字詞，也會顯示搜尋結果。
