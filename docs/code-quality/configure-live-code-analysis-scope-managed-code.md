---
title: 為託管代碼配置即時代碼分析範圍
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432235"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>如何：為託管代碼配置即時代碼分析範圍

## <a name="what-is-live-code-analysis-for-managed-code"></a>什麼是託管代碼的"即時代碼分析"？
Visual Studio 執行大量即時代碼分析，也稱為*背景分析*，同時在編輯器中編輯原始檔案。 對於可接受的視覺化工作室 IDE 編輯體驗，其中一些需要最少的分析。 其中一些是為了提高 IDE 功能的回應能力。 雖然其中一些功能是為了啟用其他 IDE 功能，例如來自 Roslyn 分析器的診斷和代碼修復。 根據功能，這些分析可以按如下方式分組：

- **診斷的後臺計算**：分析以計算原始檔案中的錯誤、警告和建議。 這些診斷程式在錯誤清單中顯示為條目，並在編輯器中顯示。 它們可以分為兩類：
    - C# 和視覺化基本編譯器診斷
    - 羅斯林分析儀診斷，包括：

        - 內置 IDE 分析器，用於代碼樣式建議和
        - 為當前解決方案中的專案[安裝](./install-roslyn-analyzers.md)的協力廠商分析器包。

- **其他背景分析**：分析，以提高IDE功能的回應性和視覺化工作室交互。 這種分析的一些例子包括：
    - 打開檔的背景分析。
    - 具有打開檔的專案的後臺編譯，以實現某些 IDE 功能的回應能力提高的符號。
    - 構建語法和符號緩存。
    - 檢測原始檔案的設計器關聯，如表單、控制項等。

## <a name="default-analysis-scope"></a>預設分析範圍

預設情況下，對 Visual Studio 中_打開_的所有檔執行用於診斷後台計算的即時代碼分析。 上面提到的_其他背景分析_很少對所有專案執行，這些專案至少有一個打開的檔。 雖然對整個解決方案執行的背景分析很少。

## <a name="custom-analysis-scope"></a>自訂分析範圍

已針對大多數客戶方案和解決方案優化了每個背景分析的預設範圍，以實現最佳的使用者體驗、功能和性能。 但是，在某些情況下，客戶可能希望自訂此範圍以減少或增加背景分析。 例如：

- 節能模式：如果使用者使用筆記本電腦電池運行，他們可能希望將功耗降至最低，從而延長電池使用時間。 在這種情況下，他們希望最小化後臺分析。
- 按需代碼分析：如果使用者喜歡關閉即時分析器執行並按需手動運行代碼分析，則他們希望將後臺分析降至最低。 請參閱[操作方式：按需手動運行代碼分析](./how-to-run-code-analysis-manually-for-managed-code.md)。
- 完整解決方案分析：如果使用者希望始終查看解決方案中的所有檔中的所有診斷，無論它們是否在編輯器中打開。 在這種情況下，他們希望將後臺分析範圍最大化到整個解決方案。

從 Visual Studio 2019 版本 16.5 開始，使用者可以顯式自訂 C# 和 Visual Basic 專案的所有即時代碼分析的範圍，包括診斷計算。 可用的分析範圍包括：

- **當前文檔**：最小化即時代碼分析範圍，以便僅對編輯器中的當前或可見檔執行。
- **打開的文檔**：預設即時代碼分析範圍，如上一節所述。
- **整個解決方案**：最大化即時代碼分析範圍，以執行整個解決方案中的所有檔和專案。

您可以通過以下步驟在"工具選項"對話方塊中選擇上述自訂分析範圍之一：

1. 要打開"**選項"** 對話方塊，在視覺化工作室的功能表列上選擇 **"工具** > **選項**"。

2. 在"**選項**"對話方塊中，**選擇文字編輯器** > **C#** 或**基本** > **高級**。

3. 選擇所需的**背景分析範圍**以自訂分析範圍。 完成後選擇 **"確定**"。

![分析範圍。](./media/background-analysis-scope.png)

> [!NOTE]
> 在 Visual Studio 2019 版本 16.5 之前，使用者可以使用 **"啟用工具** > **選項** > **文字編輯器** > **C#** 或**基本** > **高級**"選項卡的 **"啟用完整解決方案分析**"核取方塊，將診斷計算分析範圍自訂到整個解決方案。不支援將以前的 Visual Studio 版本中的背景分析範圍降至最低。

## <a name="automatically-minimize-live-code-analysis-scope"></a>自動最小化即時代碼分析範圍

如果 Visual Studio 檢測到其可以使用 200 MB 或更少的系統記憶體，它會自動將即時代碼分析範圍最小化為"當前文檔"。 如果發生這種情況，將顯示一個警報，通知您 Visual Studio 已禁用某些功能。 如果需要，一個按鈕允許您切換回以前的分析範圍。

![警報文本最小化分析範圍](./media/fsa_alert.png)

## <a name="see-also"></a>另請參閱

- [自動功能暫停](./automatic-feature-suspension.md)
- [節能模式功能請求](https://github.com/dotnet/roslyn/issues/38429)
