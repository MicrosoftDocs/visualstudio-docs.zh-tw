---
title: 在 Visual Studio 2017 中設計的新功能
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302949"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>在 Visual Studio 2017 中設計的新功能

## <a name="live-dependency-validation"></a>即時依賴項驗證

刪除不需要的依賴項是管理技術債務的一個重要部分。 Visual Studio 提供依賴項的即時驗證，包括有關問題（如問題位於何處）的準確資訊。 即時依賴項驗證充分利用了錯誤清單和編輯器中的新功能。

![即時依賴項驗證在操作中](media/dep-validation-whatsnew-01.png)

創作體驗已更改，使依賴項驗證更易於發現和更易於訪問。 術語從"層圖"更改為"依賴關係圖"。

**體系結構**功能表現在包含直接創建依賴關係關係圖的命令：

![體系結構功能表上的即時依賴項項](media/dep-validation-whatsnew-02.png)

圖層屬性名稱和說明已更改，使其更有意義：

![即時依賴項更新的屬性名稱](media/dep-validation-whatsnew-03.png)

每次保存關係圖時，您都會立即看到解決方案中當前代碼的分析結果中更改的影響。 您不必等待**驗證依賴項**命令的完成。

如需詳細資訊，請參閱[此部落格文章](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)。

## <a name="uml-designers-have-been-removed"></a>UML 設計器已被刪除

UML 設計器已從視覺化工作室中刪除。

* UML 關係圖現在作為 XML 檔顯示
* UML 模型資源管理器不再存在
* 建模專案引用不再用於依賴項驗證
* 解決方案資源管理器中的"圖層引用"節點不再顯示
* 不再使用依賴項（層）關係圖上的"驗證"生成操作 - 已刪除生成任務
* 專案結構維護，用於在版本之間往返
* 您仍然可以打開、創建、編輯和保存依賴項（層）關係圖作為 XML
* 連結到依賴項（層）圖的 TFS 工作項在設計圖上不可訪問
* 不再支援從 DSL 或圖層進行回連結
* 建模 SDK 中的 UML 可擴充性不再受支援

可通過[代碼映射](map-dependencies-across-your-solutions.md)支援視覺化 .NET 和C++代碼的體系結構。

如果您是 UML 設計人員的重要使用者，則可以在決定滿足 UML 需求的替代工具時繼續使用 Visual Studio 2015 或更早版本。

如需詳細資訊，請參閱[此部落格文章](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />對體系結構和建模工具的版式支援

Visual Studio 有多種版本版本。 並非所有這些都為體系結構和建模工具提供支援。 下表顯示每個工具的可用性。

|**特徵**|**企業版**|**專業版**|**社區版**|
|-|-|-|-|
|**Code Map**|是|僅支援讀取代碼映射、篩選代碼映射、添加新的泛型節點以及從所選內容創建新的定向圖。|-|
|**依賴關係圖**|是|僅支援讀取依賴關係關係圖。|僅支援讀取依賴關係關係圖。|
|**定向圖**（DGML 圖表）|是|是|是|
|**代碼克隆**|是|-|-|
