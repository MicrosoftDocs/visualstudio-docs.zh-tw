---
title: 如何： 裝載在其他編輯器中的編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6390f5550c445239fbd8f8f72f9c8c4ad013665a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487863"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>如何： 裝載在其他編輯器中的編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 在其他編輯器中的主應用程式編輯器](https://docs.microsoft.com/visualstudio/extensibility/how-to-host-an-editor-in-another-editor)。  
  
在 Visual Studio 中您可以藉由指定為父視窗的 裝載的視窗裝載在另一個編輯器。 若要這樣做，請設定參數<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>子視窗框架上。  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>若要設定裝載編輯器的視窗框架  
  
1.  指定做為裝載編輯器的編輯器，藉由建立子視窗窗格。  
  
     此窗格是編輯器 的文字會去的地方。  
  
2.  建立使用主控編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>方法。  
  
3.  設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>並<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>做為參數傳遞這些屬性的裝載編輯器的視窗框架實作中的屬性<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>方法，分別。  
  
     如果您需要擷取這些參數，傳遞至這些屬性<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>自主編輯器的方法。  
  
     編輯器會出現在裝載包含編輯器窗格中。  
  
## <a name="robust-programming"></a>穩固程式設計  
 **應用程式設計師**在 Visual Studio Team Edition for Architects 是裝載另一個編輯器編輯器視窗框架的範例。 **應用程式設計師**裝載在其右窗格中的其他設計工具。 設計工具面板 (或**屬性**頁面) 包含的設計工具的每個都會加入至包含的視窗框架。

