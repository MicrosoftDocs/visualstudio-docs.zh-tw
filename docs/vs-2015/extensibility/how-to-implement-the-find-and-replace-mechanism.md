---
title: 如何： 實作 尋找和取代機制 |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eaae77979fc15954b4480a038c791a15bd95ab65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486797"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>如何： 實作 尋找和取代機制
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 實作尋找和取代機制](https://docs.microsoft.com/visualstudio/extensibility/how-to-implement-the-find-and-replace-mechanism)。  
  
Visual Studio 提供兩種方式來實作尋找/取代。 其中一個方法是傳遞到殼層的文字影像，並讓它處理搜尋、 反白顯示，並取代文字。 這可讓使用者指定多個文字範圍。 或者，您的 VSPackage 可以控制這項功能本身。 在這兩種情況下，您必須通知有關目前的目標和所有開啟的文件的目標殼層。  
  
### <a name="to-implement-findreplace"></a>若要實作尋找/取代  
  
1.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>上的框架屬性所傳回的物件的其中一個介面<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>或<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。 如果您要建立自訂編輯器，您應該實作這個介面的自訂編輯器類別的一部分。  
  
2.  使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>方法來指定您的編輯器支援的選項，並指出是否實作文字影像搜尋。  
  
     如果您的編輯器支援文字的影像搜尋，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>。  
  
     否則，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>。  
  
3.  如果您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>並<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>方法，您可以藉由呼叫來簡化您的搜尋工作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>介面。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>

