---
title: 在 Visual Studio 2017 中設計的新功能
description: 瞭解 Visual Studio 2017 提供的程式碼設計新功能，例如即時相依性驗證。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ed67836507d8328a4ba394986564820c6af7308f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388096"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>在 Visual Studio 2017 中設計的新功能

## <a name="live-dependency-validation"></a>即時相依性驗證

移除不必要的相依性是管理技術債務的重要部分。 Visual Studio 提供相依性的即時驗證，包括有關問題的精確資訊，例如它們所在的位置。 即時相依性驗證會在 [錯誤清單] 和 [編輯器] 中充分發揮新功能的優點。

![作用中的即時相依性驗證](media/dep-validation-whatsnew-01.png)

撰寫經驗已改變，讓相依性驗證更容易探索且更容易存取。 術語已從「分層圖」變更為「相依性圖表」。

[ **架構** ] 功能表現在包含可直接建立相依性圖表的命令：

![[架構] 功能表上的 [即時相依性] 專案](media/dep-validation-whatsnew-02.png)

圖層屬性名稱和描述已變更，使其更有意義：

![即時相依性更新屬性名稱](media/dep-validation-whatsnew-03.png)

當您每次儲存圖表時，您都會立即看到針對方案中目前程式碼的變更所帶來的影響。 您不必等待 [驗證相依性 **]** 命令完成。

如需詳細資訊，請參閱[此部落格文章](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)。

## <a name="uml-designers-have-been-removed"></a>UML 設計工具已移除

UML 設計工具已從 Visual Studio 中移除。

* UML 圖表現在會顯示為 XML 檔案
* UML 模型 Explorer 不再存在
* 模型專案參考不再用於相依性驗證
* 方案總管中的 [圖層參考] 節點不再顯示
* 相依性 () 圖層上的「驗證」組建動作不再使用-已移除組建工作
* 保留專案結構以在版本之間進行來回往返
* 您仍然可以開啟、建立、編輯和儲存相依性 (圖層) 圖表為 XML
* 無法在設計介面上存取連結至相依性 (圖層) 圖表的 TFS 工作專案
* 不再支援從後到 DSL 或圖層的上一頁連結
* 不再支援模型化 SDK 中的 UML 擴充性

您可以透過 [code map](map-dependencies-across-your-solutions.md)取得視覺化 .Net 和 c + + 程式碼架構的支援。

如果您是 UML 設計師的重要使用者，則可以繼續使用 Visual Studio 2015 或更舊的版本，同時為您的 UML 需求決定替代工具。

如需詳細資訊，請參閱[此部落格文章](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />架構和模型工具的版本支援

Visual Studio 可以在數個版本中使用。 並非所有這些都提供架構和模型工具的支援。 下表顯示每個工具的可用性。

|**功能**|**Enterprise edition**|**Professional edition**|**社區版**|
|-|-|-|-|
|**Code Map**|是|只支援讀取 code map、篩選 code map、加入新的泛型節點，以及從選取專案建立新的有向圖形。|-|
|**相依性圖表**|是|只支援讀取相依性圖表。|只支援讀取相依性圖表。|
| (DGML 圖表的 **導向圖形**) |是|是|是|
|**程式碼複製**|是|-|-|
