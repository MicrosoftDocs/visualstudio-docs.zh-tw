---
title: 如何： 實作 尋找和取代機制 |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fbd41f8f1a86a0b6177b4a1d1498075d6de77030
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636248"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>如何： 實作尋找和取代機制

Visual Studio 提供兩種方式來實作尋找/取代。 其中一個方法是傳遞到殼層的文字影像，並讓它處理搜尋、 反白顯示，並取代文字。 這可讓使用者指定多個文字範圍。 或者，您的 VSPackage 可以控制這項功能本身。 在這兩種情況下，您必須通知有關目前的目標和所有開啟的文件的目標殼層。

## <a name="to-implement-findreplace"></a>若要實作尋找/取代

1. 實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>上的框架屬性所傳回的物件的其中一個介面<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>或<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>。 如果您要建立自訂編輯器，您應該實作這個介面的自訂編輯器類別的一部分。

2. 使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>方法來指定您的編輯器支援的選項，並指出是否實作文字影像搜尋。

   如果您的編輯器支援文字的影像搜尋，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>。

   否則，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>。

3. 如果您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>並<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>方法，您可以藉由呼叫來簡化您的搜尋工作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>介面。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>