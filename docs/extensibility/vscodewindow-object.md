---
title: VSCodeWindow 物件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36b7e0e6806f88efe373dffa3f21ba79baefb281
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189048"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 物件
程式碼視窗是特殊的文件視窗，可以包含一或多個文字視圖，通常是 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 物件。

 在架構上，程式碼視窗是在視窗框架內的文件視窗。 就功能而言，程式碼視窗只是包含額外功能的文件視窗。 在多重文件介面（MDI）模式中，程式碼視窗是 MDI 子框架。 如需詳細資訊，請參閱[使用舊版 API 自訂程式碼視窗](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)。

 下表包含 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 物件中的介面。

|方法|描述|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供一般存取機制，以找出全域唯一識別碼（GUID）識別的服務。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示多重文件介面（MDI）子系，其中包含一或多個程式碼視圖。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填滿視窗框架。|

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [圖形編輯](https://www.microsoft.com/download/details.aspx?id=55984)