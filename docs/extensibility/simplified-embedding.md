---
title: 簡化的嵌入 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700079"
---
# <a name="simplified-embedding"></a>簡化嵌入
當其文件檢視物件父級為 (即創建子 物件[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)])<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>時, 在編輯器中啟用簡化的嵌入,並且介面被實現以處理其視窗命令。 簡化的嵌入編輯器無法承載活動控制件。 用於使用簡化嵌入創建編輯器的物件如下圖所示。

 ![簡化的嵌入編輯器圖形](../extensibility/media/vssimplifiedembeddingeditor.gif "vs 簡化嵌入編輯器")具有簡化嵌入的編輯器

> [!NOTE]
> 在此圖中的物件中,只需創建`CYourEditorFactory`基於檔案的標準編輯器即可創建物件。 如果要創建自定義編輯器,則不需要實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>,因為編輯器可能有自己的私有持久性機制。 但是,對於非自定義編輯器,您必須這樣做。

 建立建立具有簡化嵌入的編輯器而實現的所有介面都包含在物件中`CYourEditorDocument`。 但是,要支持文檔數據的多個檢視,可以將介面拆分為單獨的數據,並按照下表所示查看物件。

|介面|介面位置|使用|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|檢視|提供與父窗口的連接。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|檢視|處理命令。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|檢視|啟用狀態列更新。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|檢視|啟用**工具箱**專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|資料|檔更改時發送通知。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|資料|為檔類型啟用"保存為"功能。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|資料|啟用文件的持續性。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|資料|允許抑制檔更改事件,如重新載入觸發。|
