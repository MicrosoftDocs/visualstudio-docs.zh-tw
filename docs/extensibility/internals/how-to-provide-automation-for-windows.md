---
title: 如何：為 Windows 提供自動化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fec2b9ef6612a294dc70d129cf4bdd3dde843262
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905261"
---
# <a name="how-to-provide-automation-for-windows"></a>如何：為 windows 提供自動化

您可以為檔和工具視窗提供自動化功能。 當您想要讓 automation 物件在視窗上可供使用，而且環境尚未提供現成的自動化物件時，建議您提供自動化功能，就像使用工作清單一樣。

## <a name="automation-for-tool-windows"></a>工具視窗的自動化

環境會藉由傳回標準 <xref:EnvDTE.Window> 物件（如下列程式所述），在工具視窗上提供自動化功能：

1. 透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> __VSFPROPID 的環境呼叫方法[。VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>)做為 `VSFPROPID` 參數來取得 `Window` 物件。

2. 當呼叫端透過來要求您工具視窗的 VSPackage 特定 automation 物件時 <xref:EnvDTE.Window.Object%2A> ，環境會呼叫 `QueryInterface` `IExtensibleObject` 、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> 或 `IDispatch` 介面。 `IExtensibleObject`和都 `IVsExtensibleObject` 提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 方法。

3. 當環境接著呼叫傳遞的 `GetAutomationObject` 方法時 `NULL` ，會傳回您的 VSPackage 特定物件來回應。

4. 如果呼叫 `QueryInterface` `IExtensibleObject` 和 `IVsExtensibleObject` 失敗，則環境會呼叫 `QueryInterface` `IDispatch` 。

## <a name="automation-for-document-windows"></a>文件視窗的自動化

標準 <xref:EnvDTE.Document> 物件也可以從環境中取得，不過，編輯器可透過 <xref:EnvDTE.Document> 執行 `IExtensibleObject` 介面和回應，來擁有自己的物件執行 `GetAutomationObject` 。

此外，編輯器也可以藉 <xref:EnvDTE.Document.Object%2A> 由執行或介面，提供 VSPackage 特有的自動化物件，並透過方法抓取 `IVsExtensibleObject` `IExtensibleObject` 。 [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)會提供 RTF 檔特定的 automation 物件。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
