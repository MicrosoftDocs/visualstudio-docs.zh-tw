---
title: 設定 .NET 的即時程式碼分析範圍
ms.date: 09/01/2020
description: 瞭解 Visual Studio 中的背景分析。 瞭解如何限制對可見檔、所有開啟的檔，或所有檔案和專案的分析。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7a6a7253d4104fbcde09b96b86f5f83a864677cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860395"
---
# <a name="configure-live-code-analysis-for-net"></a>設定 .NET 的即時程式碼分析

當您在編輯器中編輯原始程式檔時，Visual Studio 會執行一堆即時程式碼分析，也稱為 *背景分析*。 其中有部分是可接受的 Visual Studio IDE 編輯體驗所需的基本分析。 其中有些是為了改善 IDE 功能的回應性。 雖然其中有些是啟用其他 IDE 功能，例如來自 Roslyn 分析器的診斷和程式碼修正。 根據功能，這些分析可以分組如下：

- **診斷的背景計算**：在來源檔案中計算錯誤、警告和建議的分析。 這些診斷會顯示為 [錯誤清單] 中的專案，以及編輯器中的波浪線。 可以分為兩種類別：
  - C # 和 Visual Basic 編譯器診斷
  - Roslyn 分析器診斷，其中包括：

    - 適用于程式碼樣式建議的內建 IDE 分析器
    - 適用于程式碼品質建議的內建 CA 分析器
    - 針對目前方案中的專案所 [安裝](./install-roslyn-analyzers.md) 的協力廠商分析器套件。

- **其他背景分析**：改善 IDE 功能的回應性和 Visual Studio 互動的分析。 這類分析的一些範例如下：
  - 開啟檔案的背景剖析。
  - 具有開啟的檔案之專案的背景編譯，以實現符號來改善某些 IDE 功能的回應性。
  - 建立語法和符號快取。
  - 偵測來源檔案的設計工具關聯，例如表單、控制項等等。

## <a name="default-analysis-scope"></a>預設分析範圍

根據預設，會針對在 Visual Studio 中 _開啟_ 的所有檔案，執行診斷之背景計算的即時程式碼分析。 上面提及的一些 _其他背景分析_ 會針對所有專案執行，其中至少有一個開啟的檔案。 雖然會對整個解決方案執行一些背景分析。

## <a name="custom-analysis-scope"></a>自訂分析範圍

每個背景分析的預設範圍已經過調整，以獲得最佳的使用者體驗、功能，以及大部分客戶案例和解決方案的效能。 不過，在某些情況下，客戶可能會想要自訂此範圍來減少或增加背景分析。 例如：

- 省電模式：如果使用者以膝上型電腦電池執行，可能會想要將耗電量延長的耗電量降至最低。 在此案例中，他們想要將背景分析降至最低。
- 隨選程式碼分析：如果使用者偏好關閉即時分析器執行，並視需要手動執行程式碼分析，則會想要將背景分析降至最低。 請參閱 [如何：依需求手動執行程式碼分析](./how-to-run-code-analysis-manually-for-managed-code.md)。
- 完整解決方案分析：如果使用者想要一律查看解決方案中所有檔案的所有診斷，不論它們是否已在編輯器中開啟。 在此案例中，他們想要將背景分析範圍最大化至整個方案。

從 Visual Studio 2019 16.5 版開始，使用者可以明確自訂 c # 和 Visual Basic 專案的所有即時程式碼分析範圍，包括診斷計算。 可用的分析範圍如下：

- **目前** 的檔：將即時程式碼分析範圍最小化，只對編輯器中目前或可見的檔案執行。
- **開啟檔**：預設即時程式碼分析範圍，如上一節中所述。
- **整個解決方案**：將即時程式碼分析範圍最大化，以針對整個方案中的所有檔案和專案執行。

您可以依照下列步驟，在 [工具選項] 對話方塊中選擇上述其中一個自訂分析範圍：

1. 若要開啟 [**選項**] 對話方塊，請在 Visual Studio 的功能表列上選擇 [**工具**  >  **選項**]。

2. 在 [**選項**] 對話方塊中，選擇 [**文字編輯器**  >  **c #** ] 或 [**基本**]  >  **Advanced**。

3. 選取所需的 **背景分析範圍** ，以自訂分析範圍。 當您完成時，請選擇 **[確定]** 。

![分析範圍。](./media/background-analysis-scope.png)

> [!NOTE]
> 在 Visual Studio 2019 16.5 版之前，使用者可以從 [**工具** 選項文字編輯器  >    >    >  **c #** ] 或 [**基本**  >  ]**Advanced** 索引標籤中使用 [啟用完整解決方案分析] 核取方塊，自訂診斷計算至整個方案的分析範圍。在先前的 Visual Studio 版本中，不支援將背景分析範圍降至最低。

## <a name="automatically-minimize-live-code-analysis-scope"></a>自動將即時程式碼分析範圍降至最低

如果 Visual Studio 偵測到有 200 MB 或更少的系統記憶體可供使用，它會自動將即時程式碼分析範圍降至最低：「目前檔」。 如果發生這種情況，則會出現警示，通知您 Visual Studio 已停用某些功能。 如果您想要的話，按鈕可讓您切換回先前的分析範圍。

![警示文字最小化分析範圍](./media/fsa_alert.png)

## <a name="see-also"></a>另請參閱

- [自動功能暫停](./automatic-feature-suspension.md)
- [省電模式功能要求](https://github.com/dotnet/roslyn/issues/38429)
