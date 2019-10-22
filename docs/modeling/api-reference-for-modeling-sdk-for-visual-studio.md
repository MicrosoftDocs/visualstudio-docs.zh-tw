---
title: 模型 SDK 的 API 參考
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3915dc0ee7359c8fb0093f397542afb557d0796a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654328"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Modeling SDK for Visual Studio 的 API 參考

Visual Studio 視覺效果和模型化 SDK 會提供您的特定領域語言（DSL）工具建立所在的平臺。

本章節包含名稱開頭為 "VisualStudio" 之命名空間的參考資料。

|命名空間|內容|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|類別（例如 ModelElement），這是您在 DSL 中定義之所有網域類別的基類。|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|形成 DSL 定義一部分的類別。|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|模型存放區檢視器和效能測量工具。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|類別（例如 ShapeElement），也就是您在 DSL 中定義之所有圖形的基本類別。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|手勢和選取方法。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|DSL 定義設計工具的 API。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|DSL 定義設計工具的內部類別。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|可讓您使用命令、手勢和驗證來擴充 DSL 設計工具的屬性。|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|ModelElement 的擴充方法，可執行 DSL 擴充性。|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|擴充性屬性|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|可讓您將模型的部分設為唯讀。|
|[VisualStudio。整合](/previous-versions/ee904412(v=vs.140))|Modelbus API 可協助您整合不同的模型。|
|[VisualStudio。選擇器的整合](/previous-versions/ee904394(v=vs.140))|可讓使用者流覽至模型和專案以建立 Modelbus 參考的對話方塊。|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|選擇器服務。|
|[VisualStudio。命令介面](/previous-versions/ee869435(v=vs.140))|適用于 Visual Studio 的 Modelbus 介面卡架構。|
|[VisualStudio。選擇器的整合](/previous-versions/ee886769(v=vs.140))|[選擇器] 對話方塊，可讓使用者流覽至模型和元素，以建立 Modelbus 參考。|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Dsl 和 Visual Studio 之間的介面。|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|可讓您定義快捷方式（內容）功能表命令。|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|可讓您定義驗證條件約束。|

## <a name="see-also"></a>請參閱

- [自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)
