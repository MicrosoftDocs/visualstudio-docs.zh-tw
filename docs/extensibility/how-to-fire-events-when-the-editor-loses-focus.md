---
title: HOW TO：引發事件當編輯器失去焦點時 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec28c704cb8fecb38395c0c7b3f3e3d22ead389b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863001"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>HOW TO：引發事件當編輯器失去焦點時
有時候就必須知道當編輯器失去焦點，視窗框架上。 比方說，您可能需要擷取從程式碼視窗的程式碼之後，編輯器不再將焦點放在其上。 下列程序會提供要接收通知的編輯器失去焦點遵循的步驟。

## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>引發事件以回應編輯器失去焦點

1. 取得監視選取的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>物件從<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>。

2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>，並提供您<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>物件。

3. 在您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>，尋找`elementid==SEID_WindowFrame`。

4. 測試`varValueNew`參數兩件事：

    1. 您所需的視窗框架。

    2. 在您的程式遺失選取範圍至該視窗框架的點。