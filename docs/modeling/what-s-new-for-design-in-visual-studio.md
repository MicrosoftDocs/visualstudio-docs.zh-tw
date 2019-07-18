---
title: 在 Visual Studio 2017 中設計的新功能
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: dc75c7414e0fff18f76d14f8f9a4e0779a9e7a2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476541"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>在 Visual Studio 2017 中設計的新功能

## <a name="live-dependency-validation"></a>即時相依性驗證

移除不必要的相依性是很重要的一部分管理您的技術債務。 Visual Studio 提供即時驗證相依性，包括相關問題，例如它們的所在位置的精確資訊。 即時相依性驗證會採用完整的優點 錯誤清單 和 編輯器的新功能。

![作用中的即時相依性驗證](media/dep-validation-whatsnew-01.png)

編寫體驗已變更為更容易被找到也更容易存取，讓相依性驗證。 術語已從 「 圖層圖表 」 變成 「 相依性圖表 」。

**架構**功能表現在包含直接建立相依性圖表的命令：

![在 [架構] 功能表上的即時相依性項目](media/dep-validation-whatsnew-02.png)

圖層屬性名稱和描述已變更，使其更有意義：

![即時更新的相依性屬性名稱](media/dep-validation-whatsnew-03.png)

您立刻看到您的變更，在方案中目前的程式碼分析結果的影響每次您儲存圖表。 您不需要等候完成**驗證相依性**命令。

如需詳細資訊，請參閱 <<c0> [ 此部落格文章](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)。

## <a name="uml-designers-have-been-removed"></a>已移除 UML 設計工具

已從 Visual Studio 移除 UML 設計工具。

* UML 圖表現在會顯示為 XML 檔案
* UML 模型總管 不存在
* 模型的專案參考不再用於相依性驗證
* 在 [方案總管] 中的 「 圖層參考 」 節點不會再顯示
* 相依性 （分層） 圖表上的 [驗證] 建置動作已不再使用-已移除建置工作
* 專案結構保留在版本之間的來回行程
* 您可以仍然開啟、 建立、 編輯和儲存為 XML 的相依性 （分層） 圖表
* TFS 工作項目連結至相依性 （分層） 圖表便無法存取在設計介面上
* 不再支援後從連結到 DSL 或圖層
* Modeling SDK 中的 UML 擴充性已不再支援

以視覺化方式呈現的.NET 架構的支援和C++程式碼也可透過[code map](map-dependencies-across-your-solutions.md)。

如果您是 UML 設計工具的大量使用者時，您可以繼續使用 Visual Studio 2015 或更早版本，而您決定針對您的 UML 需求的替代工具。

如需詳細資訊，請參閱 <<c0> [ 此部落格文章](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Architecture and modeling tools 的版本支援

Visual Studio 有數個版本。 並非所有版本都提供 architecture and modeling tools 的支援。 下表顯示每個工具的可用性。

|**功能**|**企業版**|**專業版**|**Community 版本**|
|-|-|-|-|
|**Code Map**|是|只支援讀取程式碼對應，對應篩選程式碼，加入新的泛型節點，並從選取範圍建立新的導向圖形。|-|
|**相依性圖表**|是|只支援讀取相依性圖表。|只支援讀取相依性圖表。|
|**有向圖形**（DGML 圖表）|是|是|是|
|**程式碼複製品**|是|-|-|