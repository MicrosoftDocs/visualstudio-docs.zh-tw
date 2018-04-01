---
title: How to： 裝載在其他編輯器中的編輯器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 685ad1d619fdf9f04fe1a9cd1122a9e6ed3ba025
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-an-editor-in-another-editor"></a>How to： 裝載在其他編輯器中的編輯器
在 Visual Studio 中您可以藉由主控視窗指定為父視窗來裝載一個編輯器內的另一個。 若要這樣做，請設定參數<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>子視窗框架上。  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>若要設定裝載編輯器的視窗框架  
  
1.  指定做為裝載編輯器的編輯器，藉由建立子視窗窗格。  
  
     此窗格是編輯器的文字位置。  
  
2.  建立使用主控編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>方法。  
  
3.  設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>屬性中做為參數傳遞這些屬性的裝載編輯器的視窗框架實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>方法，分別。  
  
     如果您要擷取這些參數，請將傳遞給這些屬性，以<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>自主編輯器的方法。  
  
     編輯器隨即出現在裝載包含編輯器的窗格中。  
  
## <a name="robust-programming"></a>穩固程式設計  
 **應用程式設計工具**在 Visual Studio Team Edition for 架構設計人員是裝載另一個編輯器的編輯器視窗框架的範例。 **應用程式設計工具**裝載它的右窗格中的其他設計工具。 設計工具 面板 (或**屬性**頁面) 所包含的設計工具的每個都會加入至包含視窗框架。