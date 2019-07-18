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
ms.openlocfilehash: b2cbf516b5ed999623c05e7f68656199363906bf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408447"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Modeling SDK for Visual Studio 的 API 參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Visualization and Modeling SDK 提供的平台會建置您的特定領域語言 (DSL) 和 UML 工具。

> [!NOTE]
> 如需 UML 模型 API 的資訊，請參閱[UML 模型擴充性的 API 參考](../modeling/api-reference-for-uml-modeling-extensibility.md)。 文字轉換的相關資訊，請參閱[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)。

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
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|可讓您擴充 DSL 設計工具與命令、 手勢和驗證的屬性。|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|擴充方法 ModelElement 可實作 DSL 擴充性。|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|擴充性屬性|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|可讓您將模型的部分為唯讀。|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Modelbus API，可協助您整合不同的模型。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|對話方塊中，可讓使用者瀏覽至模型和建立 Modelbus 參考的項目。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|選擇器服務。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Modelbus 配接器架構[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|選擇器 對話方塊，可讓使用者瀏覽至模型和建立 Modelbus 參考的項目。|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Dsl 之間的介面和[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|可讓您定義捷徑 （操作） 功能表命令。|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|可讓您定義驗證條件約束。|

## <a name="see-also"></a>另請參閱
 [UML 模型擴充性 API 參考](../modeling/api-reference-for-uml-modeling-extensibility.md)[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)
