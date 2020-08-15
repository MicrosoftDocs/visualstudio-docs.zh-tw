---
title: 設定受控碼的即時程式碼分析範圍
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6df882d50d0c1d052191246605af856743ffdf3d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249185"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>如何：設定受控碼的即時程式碼分析範圍

## <a name="what-is-live-code-analysis-for-managed-code"></a>Managed 程式碼的「即時程式碼分析」是什麼？
當您在編輯器中編輯原始程式檔時，Visual Studio 會執行一堆即時程式碼分析（也稱為 *背景分析*）。 其中有部分需要最少的分析，以符合可接受的 Visual Studio IDE 編輯體驗。 其中一些是為了改善 IDE 功能的回應性。 其中有些是啟用其他 IDE 功能，例如來自 Roslyn 分析器的診斷和程式碼修正。 根據功能，這些分析可以分組如下：

- **診斷的背景計算**：在原始程式檔中計算錯誤、警告和建議的分析。 這些診斷會顯示為 [錯誤清單] 中的專案，以及編輯器中的波浪線。 它們可以分類為兩個類別：
  - C # 和 Visual Basic 編譯器診斷
  - Roslyn 分析器診斷，其中包括：

    - 適用于程式碼樣式建議和的內建 IDE 分析器
    - 針對目前解決方案中的專案所 [安裝](./install-roslyn-analyzers.md) 的協力廠商分析器套件。

- **其他背景分析**：改善 IDE 功能的回應性和 Visual Studio 互動的分析。 這類分析的一些範例如下：
  - 開啟檔案的背景剖析。
  - 具有開啟檔案之專案的背景編譯，以實現特定 IDE 功能的回應性改善符號。
  - 建立語法和符號快取。
  - 正在偵測原始程式檔的設計工具關聯，例如表單、控制項等等。

## <a name="default-analysis-scope"></a>預設分析範圍

根據預設，診斷背景計算的即時程式碼分析會針對在 Visual Studio 中 _開啟_ 的所有檔案執行。 以上所述的一些 _其他背景分析_ 會針對所有專案執行，其中至少有一個開啟的檔案。 雖然會對整個解決方案執行少數的背景分析。

## <a name="custom-analysis-scope"></a>自訂分析範圍

每個背景分析的預設範圍已針對大多數客戶案例和解決方案的最佳使用者體驗、功能和效能進行微調。 不過，在某些情況下，客戶可能會想要自訂此範圍來減少或增加背景分析。 例如：

- 省電模式：如果使用者是以膝上型電腦電池執行，他們可能會想要將電力耗用量降到較長的電池壽命。 在此案例中，他們會想要將背景分析降至最低。
- 隨選程式碼分析：如果使用者偏好關閉即時分析器執行，並視需要手動執行程式碼分析，他們會想要將背景分析降至最低。 請參閱 [如何：視需要手動執行程式碼分析](./how-to-run-code-analysis-manually-for-managed-code.md)。
- 完整解決方案分析：如果使用者想要隨時查看方案中所有檔案的所有診斷，不論它們是否已在編輯器中開啟。 在此案例中，他們會想要將背景分析範圍最大化至整個解決方案。

從 Visual Studio 2019 16.5 版開始，使用者可以明確自訂所有即時程式碼分析的範圍，包括 c # 和 Visual Basic 專案的診斷計算。 可用的分析範圍包括：

- **目前**的檔：最小化即時程式碼分析範圍，只針對編輯器中的目前或可見檔案執行。
- **開啟檔**：預設的即時程式碼分析範圍，如上一節所述。
- **整個解決方案**：最大化即時程式碼分析範圍，以針對整個方案中的所有檔案和專案執行。

您可以遵循下列步驟，在 [工具選項] 對話方塊中選擇上述其中一個自訂分析範圍：

1. 若要開啟 [**選項**] 對話方塊，請在 Visual Studio 的功能表列上選擇 [**工具**] [  >  **選項**]。

2. 在 [**選項**] 對話方塊中，選擇 [**文字編輯器**  >  **c #** ] 或 [**基本**] [  >  **Advanced**]。

3. 選取所需的 **背景分析範圍** ，以自訂分析範圍。 當您完成時，請選擇 **[確定]** 。

![分析範圍。](./media/background-analysis-scope.png)

> [!NOTE]
> 在 Visual Studio 2019 16.5 版之前，使用者可以使用 [**工具**] [選項] [文字編輯器] [ **Enable full solution analysis**  >  **Options**  >  **Text Editor**  >  **c #** ] 或 [**基本**  >  ] [**高級**] 索引標籤中的 [啟用完整解決方案分析] 核取方塊，自訂診斷計算的分析範圍在先前的 Visual Studio 版本中，不支援將背景分析範圍降至最低。

## <a name="automatically-minimize-live-code-analysis-scope"></a>自動將即時程式碼分析範圍降至最低

如果 Visual Studio 偵測到 200 MB 或更少的系統記憶體可供使用，它會自動將即時程式碼分析範圍降至「目前的檔」。 如果發生這種情況，則會出現警示，通知您 Visual Studio 已停用某些功能。 按鈕可讓您視需要切換回先前的分析範圍。

![警示文字最小化分析範圍](./media/fsa_alert.png)

## <a name="see-also"></a>另請參閱

- [自動功能暫停](./automatic-feature-suspension.md)
- [省電模式功能要求](https://github.com/dotnet/roslyn/issues/38429)
