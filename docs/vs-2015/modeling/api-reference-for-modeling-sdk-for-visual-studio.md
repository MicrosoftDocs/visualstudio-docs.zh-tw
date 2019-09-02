---
title: Modeling SDK 的 API 參考
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a290227b120958b5bb3407393dcff33b247b20d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872028"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Modeling SDK for Visual Studio 的 API 參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 的視覺效果和模型化 SDK 提供了建立特定領域語言 (DSL) 和 UML 工具的平臺。

> [!NOTE]
> 如需 UML 模型化 API 的相關資訊, 請參閱[Uml 模型擴充性的 API 參考](../modeling/api-reference-for-uml-modeling-extensibility.md)。 如需文字轉換的詳細資訊, 請參閱[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)。

 本章節包含命名空間名稱開頭為"Microsoft.VisualStudio.Modeling 」 參考的資料。

|命名空間|內容|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|例如 ModelElement，也就是您在 DSL 中定義的所有網域類別的基底類別的類別。|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|形成 DSL 定義的一部分的類別。|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|模型存放區檢視和效能的測量工具。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|例如 ShapeElement，也就是您在 DSL 中定義的所有形狀的基底類別的類別。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|筆勢和選取的方法。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|在 DSL 定義設計工具的 API。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|在 DSL 定義設計工具的內部類別。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|可讓您使用命令、手勢和驗證來擴充 DSL 設計工具的屬性。|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|擴充方法 ModelElement 可實作 DSL 擴充性。|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|擴充性屬性|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|可讓您將模型的部分為唯讀。|
|[VisualStudio。整合](/previous-versions/ee904412(v=vs.140))|Modelbus API，可協助您整合不同的模型。|
|[VisualStudio。選擇器的整合](/previous-versions/ee904394(v=vs.140))|對話方塊中，可讓使用者瀏覽至模型和建立 Modelbus 參考的項目。|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|選擇器服務。|
|[VisualStudio。命令介面](/previous-versions/ee869435(v=vs.140))|適用于的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Modelbus 介面卡架構。|
|[VisualStudio。選擇器的整合](/previous-versions/ee886769(v=vs.140))|選擇器 對話方塊，可讓使用者瀏覽至模型和建立 Modelbus 參考的項目。|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Dsl 和[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]之間的介面。|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|可讓您定義捷徑 （操作） 功能表命令。|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|可讓您定義驗證條件約束。|

## <a name="see-also"></a>另請參閱

- [UML 模型擴充性的 API 參考](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)
