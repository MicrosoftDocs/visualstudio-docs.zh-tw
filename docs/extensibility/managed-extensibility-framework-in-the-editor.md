---
title: 編輯器中的 Managed Extensibility Framework |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f376a43b6d59ba494db2ad4e5ef26b260d91f6ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632613"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>在編輯器中 Managed Extensibility Framework
編輯器是使用 Managed Extensibility Framework （MEF）元件所建立。 您可以建立自己的 MEF 元件來擴充編輯器，而您的程式碼也可以使用編輯器元件。

## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework 的總覽
 MEF 是一種 .NET 程式庫，可讓您新增及修改遵循 MEF 程式設計模型的應用程式或元件功能。 Visual Studio 編輯器可以提供和取用 MEF 元件部分。

 MEF 包含在 .NET Framework 版本 4 *system.workflow.componentmodel.activity*元件中。

 如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework （mef）](/dotnet/framework/mef/index)。

### <a name="component-parts-and-composition-containers"></a>元件部分和組合容器
 元件部分是類別或可以執行下列其中一項（或兩者）的成員：

- 使用另一個元件

- 由另一個元件使用

  例如，假設有一個訂單輸入元件的購物應用程式，其相依于倉儲清查元件所提供的產品可用性資料。 在 MEF 詞彙中，清查元件可以*匯出*產品可用性資料，而訂單輸入部分則可以匯*入*資料。 訂單輸入部分和清查部分不需要知道彼此，*組合容器*（由主應用程式提供）負責維護一組匯出，以及解析匯出和匯入。

  組合容器（<xref:System.ComponentModel.Composition.Hosting.CompositionContainer>）通常是由主機所擁有。 組合容器會維護已匯出元件部分的*目錄*。

### <a name="export-and-import-component-parts"></a>匯出和匯入元件部分
 您可以匯出任何功能，只要它實作為公用類別或類別的公用成員（屬性或方法）即可。 您不需要從 <xref:System.ComponentModel.Composition.Primitives.ComposablePart> 衍生元件部分。 相反地，您必須將 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性加入至您要匯出的類別或類別成員。 這個屬性會指定另一個元件部分可以匯入您的功能的*合約*。

### <a name="the-export-contract"></a>匯出合約
 @No__t_0 會定義要匯出的實體（類別、介面或結構）。 匯出屬性通常會使用參數來指定匯出的類型。

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 根據預設，<xref:System.ComponentModel.Composition.ExportAttribute> 屬性會定義一個合約，這是匯出類別的類型。

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 在此範例中，預設 `[Export]` 屬性相當於 `[Export(typeof(TestAdornmentLayerDefinition))]`。

 您也可以匯出屬性或方法，如下列範例所示。

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>匯入 MEF 匯出
 當您想要使用 MEF 匯出時，您必須知道其匯出的合約（通常是類型），並加入具有該值的 <xref:System.ComponentModel.Composition.ImportAttribute> 屬性。 根據預設，import 屬性會接受一個參數，也就是它所修改之類別的型別。 下列幾行程式碼會匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> 類型。

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>從 MEF 元件部分取得編輯器功能
 如果您現有的程式碼是 MEF 元件部分，您可以使用 MEF 中繼資料來取用編輯器元件部分。

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>使用 MEF 元件部分的編輯器功能

1. 將*system.workflow.componentmodel.activity*的參考加入至 [全域組件快取（GAC）] 和 [編輯器] 元件。

2. 新增相關的 using 指示詞。

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. 將 `[Import]` 屬性新增至您的服務介面，如下所示。

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. 當您取得服務時，您可以使用它的任何一個元件。

5. 當您編譯過元件之後，請將它放在 *.。\Common7\IDE\Components Visual Studio 安裝 \* 資料夾。

## <a name="see-also"></a>請參閱
- [語言服務和編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
