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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d2cdbe12146dd5d3010b9bf8ffcdd130a0ea4bb
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414356"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 物件
程式碼視窗是一個特製化的文件視窗，其中可包含一或多個文字視圖，通常是 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 物件。

 在架構上，程式碼視窗是視窗框架內的文件視窗。 在功能上，程式碼視窗只是包含額外功能的文件視窗。 在多重文件介面 (MDI) 模式中，程式碼視窗是 MDI 子框架。 如需詳細資訊，請參閱 [使用舊版 API 自訂程式碼視窗](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)。

 下表包含物件中的介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 。

|方法|描述|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供泛型存取機制，以找出全域唯一識別碼 (GUID) 識別的服務。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示多個檔介面 (MDI) 子系，其中包含一個或多個程式碼視圖。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填滿視窗框架。|

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [編輯圖形](https://www.microsoft.com/download/details.aspx?id=55984)