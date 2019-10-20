---
title: 在 Visual Studio 2017 中設計的新功能
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 51d4f4d2af5dde398744d926e45200ec16c6214a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666941"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>在 Visual Studio 2017 中設計的新功能

## <a name="live-dependency-validation"></a>即時相依性驗證

移除不想要的相依性是管理技術債務的重要部分。 Visual Studio 提供相依性的即時驗證，包括有關問題的精確資訊，例如它們所在的位置。 即時相依性驗證會充分利用錯誤清單和編輯器中新功能的優點。

![作用中的即時相依性驗證](media/dep-validation-whatsnew-01.png)

撰寫經驗已變更，讓相依性驗證更容易探索且更容易存取。 術語已從「分層圖」變更為「相依性圖表」。

[**架構**] 功能表現在包含直接建立相依性圖表的命令：

![[架構] 功能表上的 [即時相依性專案]](media/dep-validation-whatsnew-02.png)

圖層屬性名稱和描述已經變更，使其更有意義：

![即時相依性已更新屬性名稱](media/dep-validation-whatsnew-03.png)

當您每次儲存圖表時，您會立即看到方案中目前程式碼之分析結果的影響。 您不需要等待 [驗證相依性 **]** 命令完成。

如需詳細資訊，請參閱[這篇 blog 文章](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)。

## <a name="uml-designers-have-been-removed"></a>UML 設計工具已移除

UML 設計工具已從 Visual Studio 中移除。

* UML 圖表現在會以 XML 檔案的形式呈現
* UML 模型瀏覽器已不存在
* 不會再使用模型專案參考來進行相依性驗證
* 方案總管中的 [圖層參考] 節點已不會再顯示
* 相依性（圖層）圖表上的 [驗證] 組建動作已不再使用-已移除組建工作
* 版本之間的往返會保留專案結構
* 您仍然可以將相依性（圖層）圖表開啟、建立、編輯和儲存為 XML
* 在設計介面上無法存取連結至相依性（圖層）圖表的 TFS 工作專案
* 不再支援從到 DSL 或圖層的反向連結
* 不再支援模型化 SDK 中的 UML 擴充性

視覺化 .NET 和C++程式碼架構的支援可透過[code map](map-dependencies-across-your-solutions.md)取得。

如果您是 UML 設計工具的重要使用者，您可以繼續使用 Visual Studio 2015 或更早版本，同時為 UML 需求決定替代工具。

如需詳細資訊，請參閱[這篇 blog 文章](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a>架構和模型工具的 <a name="VersionSupport" />Edition 支援

Visual Studio 在數個版本中都有提供。 並非所有這些都提供架構和模型工具的支援。 下表顯示每個工具的可用性。

|**功能**|**Enterprise edition**|**Professional edition**|**社區版**|
|-|-|-|-|
|**Code Map**|[是]|僅支援讀取 code map、篩選程式代碼對應、加入新的泛型節點，以及從選取範圍建立新的導向圖形。|-|
|**相依性圖表**|[是]|僅支援讀取相依性圖表。|僅支援讀取相依性圖表。|
|**導向的圖形**（DGML 圖表）|[是]|[是]|[是]|
|**程式碼複製**|[是]|-|-|