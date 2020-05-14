---
title: 向設計師提供撤銷支援 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699667"
---
# <a name="supply-undo-support-to-designers"></a>提供設計人員提供復原支援

設計人員(如編輯器)通常需要支援撤消操作,以便用戶可以在修改代碼元素時撤銷其最近的更改。

在 Visual Studio 中實現的大多數設計人員都有環境自動提供的「撤銷」 支援。

需要支援到復原功能提供支援的設計器實現:

- 通過實現抽象基類提供撤銷管理<xref:System.ComponentModel.Design.UndoEngine>

- 通過實現<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>類來提供持久性和 CodeDOM 支援。

有關使用 .NET 架構編寫設計器的詳細資訊,請參閱[延伸設計時間支援](/previous-versions/37899azc(v=vs.140))。

使用[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]以下選項提供預設復原基礎結構:

- 通過<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>和<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>類提供撤銷管理實現。

- 通過預設值<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>和實現提供持久<xref:System.ComponentModel.Design.IComponentChangeService>性和 CodeDOM 支援。

## <a name="obtain-undo-support-automatically"></a>自動取得復原支援

在 Visual Studio 中建立的任何設計器都具有自動和完全復原支援,如果:

- 使用<xref:System.Windows.Forms.Control>基於它的類進行用戶介面。

- 使用基於 CodeDOM 的標準代碼生成和分析系統來生成和持久化。

   有關使用 Visual Studio CodeDOM 支援的詳細資訊,請參閱[動態源碼產生和編譯](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)。

## <a name="when-to-use-explicit-designer-undo-support"></a>何時使用繪圖式設計器復原支援
 如果設計人員使用圖形使用者介面(稱為視圖適配器)(而不是提供的<xref:System.Windows.Forms.Control>用戶介面),則必須提供自己的撤銷管理。

 例如,創建具有基於 Web 的圖像設計介面而不是基於 .NET 框架的圖形介面的產品。

 在這種情況下,需要使用向<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>Visual Studio 註冊此檢視適配器,並提供顯式撤銷管理。

 如果設計人員不使用<xref:System.CodeDom>名稱空間中提供的 Visual Studio 代碼生成模型,則需要提供 CodeDOM 和持久性支援。

## <a name="undo-support-features-of-the-designer"></a>復原設計器的支援功能
 環境 SDK 提供提供撤銷支援所需的預設介面實現,設計人員可以使用這些支援,這些支援可用於不<xref:System.Windows.Forms.Control>使用 基於其使用者介面的類或標準 CodeDOM 和持久性模型。

 類<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>派生自 .NET<xref:System.ComponentModel.Design.UndoEngine>Framework<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>類,使用 類的實現來管理撤銷操作。

 Visual Studio 為設計器復原提供以下功能:

- 跨多個設計器連結的撤消功能。

- 設計器中的子單位可以通過<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit><xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>和 在與其父母進行交互。

環境 SDK 透過提供以下功能提供 CodeDOM 和持久性支援:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>作為<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- 由<xref:System.ComponentModel.Design.IComponentChangeService>視覺工作室設計主機提供。

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>使用環境 SDK 功能提供復原支援

要獲得撤銷支援,實現設計器的物件必須實例化和初始化具有有效<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine><xref:System.IServiceProvider>實現的類的實例。 此類<xref:System.IServiceProvider>必須提供以下服務:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   使用 Visual Studio CodeDOM 序列化<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]設計人員可以<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>選擇使用 作為 的使用者 。

   在這種情況下,<xref:System.IServiceProvider>提供給建構函數<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>的 類應返回此<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>物件作為類的實現。

- <xref:System.ComponentModel.Design.IComponentChangeService>

   使用 Visual <xref:System.ComponentModel.Design.DesignSurface> Studio 設計主機提供的預設值的設計<xref:System.ComponentModel.Design.IComponentChangeService>人員保證具有 類的預設實現。

實現基於復原<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>機制的設計人員在:

- 屬性更改通過<xref:System.ComponentModel.TypeDescriptor>對象進行。

- <xref:System.ComponentModel.Design.IComponentChangeService>提交可撤銷的更改時,將手動生成事件。

- 變更器的變更是在的上下文中建立的<xref:System.ComponentModel.Design.DesignerTransaction>。

- 設計<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>器選擇使用 實現提供的標準撤銷單元或特定於 Visual Studio 的實現顯式創建撤銷單元,<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>該單<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>元 派<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>生<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>並同時提供和的實現。

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [延伸設計時間支援](/previous-versions/37899azc(v=vs.140))
