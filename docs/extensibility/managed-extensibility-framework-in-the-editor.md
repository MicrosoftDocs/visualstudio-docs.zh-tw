---
title: 編輯器中的托管擴充性框架 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702873"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>編輯器中的托管擴充性框架
編輯器是透過使用託管擴展框架 (MEF) 元件建構的。 您可以建構自己的 MEF 元件來擴充編輯器,並且程式碼也可以使用編輯器元件。

## <a name="overview-of-the-managed-extensibility-framework"></a>託管延伸性框架概述
 MEF 是一個 .NET 庫,允許您添加和修改遵循 MEF 程式設計模型的應用程式或元件的功能。 Visual Studio 編輯器既可以提供也可以使用 MEF 元件部件。

 MEF 包含在 .NET 框架版本 4*系統.元件模型.合成.dll*程式集中。

 有關 MEF 的詳細資訊,請參閱[託管擴展性框架 (MEF)。](/dotnet/framework/mef/index)

### <a name="component-parts-and-composition-containers"></a>元件零件與合成容器
 元件元件是類或類的成員,可以執行以下一項(或兩者)::

- 使用另一個元件

- 由其他元件使用

  例如,考慮一個購物應用程式,該應用程式具有依賴於倉庫庫存元件提供的產品可用性數據的訂單輸入元件。 在 MEF 術語中,庫存部件可以*匯出*產品可用性數據,訂單輸入部分可以*導入*數據。 訂單輸入部分和庫存部分不必相互瞭解;*組合容器*(由宿主應用程式提供)負責維護匯出集和解決匯出和導入問題。

  組合容器<xref:System.ComponentModel.Composition.Hosting.CompositionContainer>通常由主機擁有。 組合容器維護匯出的零組件的*目錄*。

### <a name="export-and-import-component-parts"></a>進出口零部件
 只要它是作為公共類或類(屬性或方法)的公共成員實現的,就可以匯出任何功能。 不必從<xref:System.ComponentModel.Composition.Primitives.ComposablePart>派生元件部件。 相反,您必須向要匯出<xref:System.ComponentModel.Composition.ExportAttribute>的類或類成員添加屬性。 這個屬性指定其他元件元件可以匯入功能*的協定*。

### <a name="the-export-contract"></a>出口合同
 定義<xref:System.ComponentModel.Composition.ExportAttribute>要匯出的實體(類、介面或結構)。 通常,匯出屬性採用指定匯出類型的參數。

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 默認情況下,該<xref:System.ComponentModel.Composition.ExportAttribute>屬性定義作為匯出類類型的協定。

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 這個選項, 預設`[Export]`屬性等效於`[Export(typeof(TestAdornmentLayerDefinition))]`。

 您還可以匯出屬性或方法,如以下示例所示。

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>匯入 MEF 匯出
 當您想要使用 MEF 匯出時,必須知道匯出它的協定(通常是類型),並添加具有<xref:System.ComponentModel.Composition.ImportAttribute>該值的屬性。 默認情況下,導入屬性採用一個參數,這是它修改的類的類型。 以下代碼行匯入類型<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>。

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>從 MEF 元件元件取得編輯器功能
 如果現有代碼是 MEF 元件部件,則可以使用 MEF 元數據使用編輯器元件元件。

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>使用 MEF 元件元件的編輯器功能

1. 新增對位於全域程式集快取 (GAC) 與編輯器程式集的*參考*。

2. 添加相關的使用指令。

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. 將`[Import]`屬性添加到服務介面,如下所示。

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. 獲得服務后,可以使用其任一元件。

5. 編譯程式集后,將其放入 *中。[公共7_IDE_元件\*資料夾的可視化工作室安裝。

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
