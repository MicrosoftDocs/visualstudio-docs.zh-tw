---
title: 如何：在其他編輯器中裝載編輯器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204164"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>如何：在其他編輯器中裝載編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 您可以將裝載視窗指定為父視窗，以在另一個編輯器中裝載一個編輯器。 若要這樣做，請 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 在子視窗框架上設定參數和。  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>設定視窗框架以裝載編輯器  
  
1. 藉由建立子視窗窗格，將編輯器指定為託管編輯器。  
  
     此窗格是編輯器的文字將移至的位置。  
  
2. 使用或方法建立裝載編輯器 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> 。  
  
3. 將 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 這些屬性作為參數的參數分別傳遞給方法，以在主控編輯器的視窗框架執行中設定和屬性 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> 。  
  
     如果您需要取出這些參數，請將這些屬性傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 方法。  
  
4. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 包含之編輯器的方法。  
  
     編輯器會出現在包含編輯器的 [主控] 窗格中。  
  
## <a name="robust-programming"></a>穩固程式設計  
 架構設計人員 Visual Studio Team Edition 中的 **應用程式設計工具** 是裝載另一個編輯器之編輯器視窗框架的範例。 **應用程式設計工具**會在其右窗格中裝載其他設計工具。 每個包含的設計工具 (或 **屬性** 頁面) 的設計工具，都會加入至包含的視窗框架中。
