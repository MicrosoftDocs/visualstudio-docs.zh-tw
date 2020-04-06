---
title: VSCode視窗物件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697963"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 物件
代碼視窗是一個專用文檔視窗,可以包含一個或多個文本視圖,通常<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>是 物件。

 在架構結構上,代碼視窗是視窗框架內的文檔視窗。 在功能上,代碼視窗只是具有附加功能的文檔視窗。 在多文件介面 (MDI) 模式下,代碼視窗是 MDI 子幀。 關於詳細資訊,請參閱[使用舊 API 自訂代碼視窗](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)。

 下表包括物件中的<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>介面。

|方法|描述|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供通用存取機制,用於查找全域唯一標識碼 (GUID) 標識的服務。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示包含一個或多個代碼檢視的多個文檔介面 (MDI) 子級。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填充視窗框架。|

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [數位編輯](https://www.microsoft.com/download/details.aspx?id=55984)
