---
title: 編輯器中的 Managed Extensibility Framework |Microsoft Docs
description: 瞭解 Managed Extensibility Framework，可讓您建立自己的元件，以擴充 Visual Studio SDK 中的編輯器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5965ca211710b0710626118f016b2cb3fec116b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915148"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>編輯器中的 Managed Extensibility Framework
編輯器是使用 Managed Extensibility Framework (MEF) 元件所建立。 您可以建立自己的 MEF 元件以延伸編輯器，而且您的程式碼也可以使用編輯器元件。

## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework 總覽
 MEF 是 .NET 程式庫，可讓您新增和修改遵循 MEF 程式設計模型的應用程式或元件的功能。 Visual Studio 編輯器可以提供和取用 MEF 元件部分。

 MEF 包含在 .NET Framework 第4版 *System.ComponentModel.Composition.dll* 元件中。

 如需 MEF 的詳細資訊，請參閱 [Managed Extensibility Framework (mef) ](/dotnet/framework/mef/index)。

### <a name="component-parts-and-composition-containers"></a>元件元件和組合容器
 元件元件是類別或類別的成員，可執行下列其中一個 (或兩個) ：

- 使用另一個元件

- 由另一個元件使用

  例如，假設有一個購物應用程式，其訂單輸入元件相依于倉儲清查元件所提供的產品可用性資料。 在 MEF 詞彙中，清查部分可以 *匯出* 產品可用性資料，而訂單輸入部分可以匯 *入* 資料。 訂單輸入部分和清查部分不需要知道彼此;主應用程式所提供的 *組合容器* () 負責維護一組匯出，以及解析匯出和匯入。

  組合容器（ <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> ）通常是由主控制項所擁有。 組合容器會維護匯出元件部分的 *目錄* 。

### <a name="export-and-import-component-parts"></a>匯出和匯入元件部分
 您可以匯出任何功能，只要它是實作為公用類別，或是類別 (屬性或方法) 的 public 成員。 您不需要從衍生元件部分 <xref:System.ComponentModel.Composition.Primitives.ComposablePart> 。 相反地，您必須將 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性加入至您要匯出的類別或類別成員。 這個屬性會指定另一個元件元件可以匯入您功能的 *合約* 。

### <a name="the-export-contract"></a>匯出合約
 <xref:System.ComponentModel.Composition.ExportAttribute>會定義要匯出的實體 (類別、介面或結構) 。 一般而言，export 屬性會採用指定匯出類型的參數。

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 根據預設， <xref:System.ComponentModel.Composition.ExportAttribute> 屬性會定義屬於匯出類別型別的合約。

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 在此範例中，預設 `[Export]` 屬性相當於 `[Export(typeof(TestAdornmentLayerDefinition))]` 。

 您也可以匯出屬性或方法，如下列範例所示。

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>匯入 MEF 匯出
 當您想要使用 MEF 匯出時，您必須知道合約 (通常是匯出它的類型) ，然後新增 <xref:System.ComponentModel.Composition.ImportAttribute> 具有該值的屬性。 根據預設，匯入屬性會接受一個參數，也就是它所修改之類別的型別。 下列幾行程式碼會匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> 類型。

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>從 MEF 元件部分取得編輯器功能
 如果您現有的程式碼是 MEF 元件的一部分，您可以使用 MEF 中繼資料來取用編輯器元件部分。

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>從 MEF 元件部分取用編輯器功能

1. 將參考新增至 *System.Composition.ComponentModel.dll*（位於全域組件快取 (GAC) ）和編輯器元件。

2. 加入相關的 using 指示詞。

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. 將 `[Import]` 屬性新增至您的服務介面，如下所示。

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. 當您取得服務之後，您就可以使用其中任何一個元件。

5. 當您編譯元件之後，請將它放在 *. 中。\* Visual Studio 安裝的 \Common7\IDE\Components 資料夾。

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
