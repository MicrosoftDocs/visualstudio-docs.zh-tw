---
title: VSCodeWindow 物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690765"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼視窗是一個特製化的文件視窗，其中可包含一或多個文字視圖，通常是 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 物件。  
  
 在架構上，程式碼視窗是視窗框架內的文件視窗。 在功能上，程式碼視窗只是包含額外功能的文件視窗。 在多重文件介面 (MDI) 模式中，程式碼視窗是 MDI 子框架。 如需詳細資訊，請參閱 [使用舊版 API 自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)。  
  
 下表包含物件中的介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供泛型存取機制，以找出全域唯一識別碼 (GUID) 識別的服務。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示多個檔介面 (MDI) 子系，其中包含一個或多個程式碼視圖。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填滿視窗框架。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [編輯圖形](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
