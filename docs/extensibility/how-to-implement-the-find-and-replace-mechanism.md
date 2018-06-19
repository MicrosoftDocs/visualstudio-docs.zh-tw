---
title: 如何： 實作 尋找和取代機制 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26d1866d9b816dfca3f82f98db372865f9d27a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128934"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>如何： 實作 尋找和取代機制
Visual Studio 提供兩種實作尋找/取代。 一種方式為傳遞到殼層文字映像，並讓它處理搜尋、 反白顯示和取代文字。 這可讓使用者指定多個文字範圍。 或者，您的 VSPackage 可以控制這項功能本身。 在這兩種情況下，您必須通知殼層有關目前的目標和所有開啟的文件的目標。  
  
### <a name="to-implement-findreplace"></a>若要實作尋找/取代  
  
1.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>上的框架屬性所傳回的物件的其中一個介面<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>或<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。 如果您要建立自訂編輯器，您應該實作這個介面做為自訂編輯器類別的一部分。  
  
2.  使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>方法以指定您的編輯器支援的選項，並指出是否實作搜尋的文字映像。  
  
     如果您的編輯器支援文字的影像搜尋，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>。  
  
     否則，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>。  
  
3.  如果您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>方法，您可以藉由呼叫簡化您的搜尋工作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>介面。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>