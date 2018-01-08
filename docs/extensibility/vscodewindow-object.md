---
title: "VSCodeWindow 物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2de0998a3d89c1af3e18fa60aa3f8511716f6165
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vscodewindow-object"></a>VSCodeWindow 物件
程式碼視窗是一種特殊文件視窗，通常可以包含一或多個文字檢視<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
 在架構上，程式碼視窗是文件視窗的視窗框架內。 在功能上，程式碼視窗是只具有其他功能的文件視窗。 在多重文件介面 (MDI) 模式中，程式碼視窗會是 MDI 子框架。 如需詳細資訊，請參閱[自訂程式碼視窗中，使用舊版 API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)。  
  
 下表包含中的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>物件。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供一般存取機制來尋找服務的全域唯一識別碼 (GUID) 識別。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|代表包含一或多個程式碼檢視多個文件介面 (MDI) 子系。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填滿視窗框架。|  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [編輯圖表](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)