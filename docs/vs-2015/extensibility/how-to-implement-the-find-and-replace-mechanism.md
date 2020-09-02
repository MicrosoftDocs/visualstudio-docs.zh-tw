---
title: 如何：執行尋找和取代機制 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548689"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>如何：實作尋找和取代機制
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 提供兩種方式來執行尋找/取代。 其中一種方式是將文字影像傳遞給 shell，並讓它處理搜尋、反白顯示和取代文字。 這可讓使用者指定多個文字範圍。 或者，您的 VSPackage 可以自行控制此功能。 在這兩種情況下，您都必須向 shell 通知目前的目標和所有開啟檔的目標。  
  
### <a name="to-implement-findreplace"></a>若要執行尋找/取代  
  
1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>在框架屬性或所傳回的其中一個物件上，執行 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 介面 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 。 如果您要建立自訂編輯器，您應該將這個介面實作為自訂編輯器類別的一部分。  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>您可以使用方法來指定編輯器支援的選項，並指出它是否會執行文字影像搜尋。  
  
     如果您的編輯器支援文字影像搜尋，請執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> 。  
  
     否則，請執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> 。  
  
3. 如果您執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> 方法，您可以藉由呼叫介面來簡化搜尋工作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> 。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
