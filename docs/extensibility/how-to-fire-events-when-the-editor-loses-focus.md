---
title: 如何： 引發事件，當編輯器失去焦點時 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbdcf30443bc548fd8d182db301cbc7119d8ceae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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