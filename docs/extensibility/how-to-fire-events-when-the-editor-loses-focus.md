---
title: 如何： 引發事件，當編輯器失去焦點時 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bb20adf3950e87c37e2ca64bcd78913839f89d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>如何： 引發事件，當編輯器失去焦點時
有時則需要知道當編輯器失去焦點視窗框架上。 例如，您可能需要擷取從程式碼視窗的程式碼編輯器不會再著重於它之後。 下列程序會提供要接收通知的編輯器失去焦點遵循的步驟。  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>引發事件以回應編輯器失去焦點  
  
1.  監視選取的事件取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>物件從<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>，並提供您<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>物件。  
  
3.  在您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>，尋找`elementid==SEID_WindowFrame`。  
  
4.  測試`varValueNew`參數兩件事：  
  
    1.  您所需的視窗框架。  
  
    2.  在您的程式失去該視窗框架選取範圍點。