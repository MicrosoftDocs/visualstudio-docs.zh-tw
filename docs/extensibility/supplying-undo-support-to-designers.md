---
title: 為設計工具提供復原支援 |Microsoft Docs
description: 瞭解如何使用 Visual Studio SDK 中的功能，在設計工具中自動提供復原支援。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b56eb762cf4a2746af04ed69c7c4c49afc15dec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056307"
---
# <a name="supply-undo-support-to-designers"></a>為設計工具提供復原支援

設計工具（例如編輯器）通常需要支援復原作業，以便使用者在修改程式碼專案時，可以反轉其最近的變更。

在 Visual Studio 中執行的大部分設計工具都有環境自動提供的「復原」支援。

需要提供復原功能支援的設計工具：

- 藉由執行抽象基類來提供復原管理 <xref:System.ComponentModel.Design.UndoEngine>

- 藉由執行和類別來提供持續性和 CodeDOM 支援 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  <xref:System.ComponentModel.Design.IComponentChangeService> 。

如需使用 .NET Framework 撰寫設計工具的詳細資訊，請參閱 [擴充 Design-Time 支援](/previous-versions/37899azc(v=vs.140))。

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供預設的復原基礎結構，方式如下：

- 透過和類別提供復原管理 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> 。

- 透過預設和實現提供持續性和 CodeDOM 支援 <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> 。

## <a name="obtain-undo-support-automatically"></a>自動取得復原支援

在 Visual Studio 中建立的任何設計工具，在設計工具時都具有自動和完整復原支援：

- 使用型類別做 <xref:System.Windows.Forms.Control> 為其使用者介面。

- 採用標準的 CodeDOM 型程式碼產生和剖析系統，以產生程式碼和持續性。

   如需有關使用 Visual Studio CodeDOM 支援的詳細資訊，請參閱 [動態原始程式碼產生和編譯](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)。

## <a name="when-to-use-explicit-designer-undo-support"></a>使用明確設計工具復原支援的時機
 如果設計人員使用圖形化使用者介面（稱為 view adapter）（而非提供者），則必須提供自己的復原管理 <xref:System.Windows.Forms.Control> 。

 其中一個範例可能是以 web 為基礎的圖形設計介面來建立產品，而不是以 .NET Framework 為基礎的圖形化介面。

 在這種情況下，您需要使用 Visual Studio 註冊此 view adapter <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> ，並提供明確的復原管理。

 如果設計工具未使用命名空間中提供的 Visual Studio 程式碼產生模型，則需要提供 CodeDOM 和持續性支援 <xref:System.CodeDom> 。

## <a name="undo-support-features-of-the-designer"></a>復原設計工具的支援功能
 環境 SDK 提供所需的預設介面介面，以提供復原支援，而設計工具可使用 <xref:System.Windows.Forms.Control> 其使用者介面或標準 CodeDOM 和持續性模型，而不使用型類別。

 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>類別衍生自 .NET Framework 類別，其 <xref:System.ComponentModel.Design.UndoEngine> 使用類別的實 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 來管理復原作業。

 Visual Studio 提供下列功能給設計工具復原：

- 跨多個設計工具連結的復原功能。

- 設計工具內的子單位可以藉由實和來與其父系互動 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> 。

環境 SDK 提供 CodeDOM 和持續性支援，方法是提供：

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 作為的實作為 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- <xref:System.ComponentModel.Design.IComponentChangeService>由 Visual Studio 設計主控制項提供。

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>使用環境 SDK 功能來提供復原支援

若要取得復原支援，執行設計工具的物件必須具現化，並 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 使用有效的實初始化類別的實例 <xref:System.IServiceProvider> 。 此 <xref:System.IServiceProvider> 類別必須提供下列服務：

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   使用 Visual Studio CodeDOM 序列化的設計工具，可能會選擇使用 <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 提供的 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 做為的實作為 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> 。

   在此情況下， <xref:System.IServiceProvider> 提供給此函 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 式的類別應該會傳回這個物件做為類別的實作為 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> 。

- <xref:System.ComponentModel.Design.IComponentChangeService>

   使用 <xref:System.ComponentModel.Design.DesignSurface> Visual Studio design host 提供之預設值的設計工具保證具有類別的預設實值 <xref:System.ComponentModel.Design.IComponentChangeService> 。

執行以復原機制為基礎的設計工具 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 會在下列情況自動追蹤變更：

- 屬性變更是透過物件進行 <xref:System.ComponentModel.TypeDescriptor> 。

- <xref:System.ComponentModel.Design.IComponentChangeService> 認可哥撤銷的變更時，會以手動方式產生事件。

- 設計工具上的修改是在的內容中建立的 <xref:System.ComponentModel.Design.DesignerTransaction> 。

- 設計工具選擇使用的執行所提供的標準復原單位 <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> 或衍生自的 Visual Studio 特定的實作為來明確建立復原單位 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> ，而且 <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> 也提供和的實作為 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> 。

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [擴充 Design-Time 支援](/previous-versions/37899azc(v=vs.140))
