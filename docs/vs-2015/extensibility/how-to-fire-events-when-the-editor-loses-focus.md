---
title: 如何：在編輯器失去焦點時引發事件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204199"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>如何：在編輯器失去焦點時引發事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有時，您必須知道編輯器何時失去焦點在視窗框架上。 例如，您可能需要在編輯器不再專注于程式碼視窗之後，將程式碼從程式碼視窗中取出。 下列程式提供的步驟可讓您取得編輯器失去焦點的通知。  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>引發事件以回應遺失焦點的編輯器  
  
1. 從取得物件來監視選取事件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> 並提供您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> 物件。  
  
3. 在您的呼叫中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 尋找 `elementid==SEID_WindowFrame` 。  
  
4. 測試 `varValueNew` 參數是否有兩個專案：  
  
    1. 您要尋找的視窗框架。  
  
    2. 程式失去該視窗框架之選取範圍的點。
