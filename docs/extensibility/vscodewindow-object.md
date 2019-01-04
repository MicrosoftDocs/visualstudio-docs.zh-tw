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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 118941fe60a589bdacef07de1734f419717b261a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943125"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 物件
程式碼視窗是一種特殊的文件視窗，通常可以包含一或多個文字檢視，<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
 在架構上，程式碼視窗會在視窗框架內的文件視窗。 在功能上，程式碼視窗只是文件視窗以及額外的功能。 在多重文件介面 (MDI) 模式中，程式碼視窗會是 MDI 子框架。 如需詳細資訊，請參閱 <<c0> [ 使用舊版 API 來自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)。  
  
 下表包含中的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>物件。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供一般存取機制，來找出全域唯一識別碼 (GUID) 識別服務。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示多個文件介面 (MDI) 子系包含一個或多個程式碼檢視。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填滿視窗框架。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [圖形編輯](https://www.microsoft.com/download/details.aspx?id=55984)