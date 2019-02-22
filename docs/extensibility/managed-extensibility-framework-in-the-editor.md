---
title: Managed Extensibility Framework，在編輯器中的 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df5edaeab56a05b6bb3fbafc371ec3ac4089cacc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917963"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>在編輯器中 managed Extensibility Framework
編輯器是使用 Managed Extensibility Framework (MEF) 元件所建置。 您可以建置自己的 MEF 元件來擴充編輯器 中，和您的程式碼可以使用編輯器元件以及。  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed 的 Extensibility Framework 概觀  
 MEF 是.NET 程式庫，可讓您新增及修改應用程式或元件，遵循 MEF 程式設計模型的功能。 Visual Studio 編輯器可提供和取用 MEF 元件組件。  
  
 .NET Framework 第 4 版中包含的 MEF *System.ComponentModel.Composition.dll*組件。  
  
 如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。  
  
### <a name="component-parts-and-composition-containers"></a>元件組件和組合容器  
 將元件組件是類別或類別的成員可以執行其中一個 （或兩者） 下列：  
  
- 使用另一個元件  
  
- 可供另一個元件  
  
  比方說，假設購物應用程式有一種順序項目元件，取決於倉儲庫存元件所提供的產品可用性資料。 MEF 而言，可以清查一部分*匯出*產品可用性的資料，而且訂單項目組件可以*匯入*資料。 訂單項目和清查部分不需要知道彼此;*組合容器*（由主應用程式提供） 會負責維護一組匯出，並解決匯出並匯入。  
  
  組合容器， <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>，通常由主機所擁有。 組合容器會維護*目錄*匯出的元件組件。  
  
### <a name="export-and-import-component-parts"></a>匯出和匯入元件組件  
 您可以匯出任何功能，，只要它會實作為公用類別或公用類別的成員 （屬性或方法）。 您沒有衍生您的元件組件從<xref:System.ComponentModel.Composition.Primitives.ComposablePart>。 相反地，您必須新增<xref:System.ComponentModel.Composition.ExportAttribute>屬性至類別或您想要匯出的類別成員。 這個屬性會指定*合約*的另一個元件組件可以匯入您的功能。  
  
### <a name="the-export-contract"></a>匯出合約  
 <xref:System.ComponentModel.Composition.ExportAttribute>定義正在匯出的實體 （類別、 介面或結構）。 一般而言，匯出屬性會指定匯出的型別參數。  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 根據預設，<xref:System.ComponentModel.Composition.ExportAttribute>屬性定義合約，會匯出類別的型別。  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 在範例中，預設值`[Export]`屬性就相當於`[Export(typeof(TestAdornmentLayerDefinition))]`。  
  
 您也可以匯出的屬性或方法，如下列範例所示。  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="import-a-mef-export"></a>匯入的 MEF 匯出  
 當您想要使用的 MEF 匯出時，您必須知道的合約 （通常是型別） 程式它已匯出，並將其新增<xref:System.ComponentModel.Composition.ImportAttribute>具有該值的屬性。 根據預設，匯入屬性會接受一個參數，也就是它會修改類別的型別。 下列幾行程式碼匯入的<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>型別。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="get-editor-functionality-from-a-mef-component-part"></a>取得從 MEF 元件組件的編輯器功能  
 如果您現有的程式碼是 MEF 元件部分，您可以使用 MEF 中繼資料來取用編輯器元件組件。  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>若要使用的 MEF 元件組件的編輯器功能  
  
1.  將參考加入至*System.Composition.ComponentModel.dll*，這是在全域組件快取 (GAC)，以及編輯器的組件。  
  
2.  加入相關 using 陳述式。  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  新增`[Import]`屬性至您的服務介面，如下所示。  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  當您取得的服務時，您可以使用其元件的任何一個。  
  
5.  當您編譯您的組件中，然後再將它放在 *...\Common7\IDE\Components\* Visual Studio 安裝資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)