---
title: 如何：為 Windows 提供自動化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848846"
---
# <a name="how-to-provide-automation-for-windows"></a>如何：為 windows 提供自動化

您可以為檔和工具視窗提供自動化功能。 當您想要讓 automation 物件在視窗上可供使用，而且環境尚未提供現成的自動化物件時，建議您提供自動化功能，就像使用工作清單一樣。

## <a name="automation-for-tool-windows"></a>工具視窗的自動化

環境會藉由傳回標準 <xref:EnvDTE.Window> 物件，在工具視窗上提供自動化，如下列程式所述：

1. 透過具有 __VSFPROPID 的環境呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 方法[。VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` 參數來取得 `Window` 物件。

2. 當呼叫端透過 <xref:EnvDTE.Window.Object%2A>要求工具視窗的 VSPackage 特定 automation 物件時，環境會針對 `IExtensibleObject`、<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>或 `IDispatch` 介面呼叫 `QueryInterface`。 `IExtensibleObject` 和 `IVsExtensibleObject` 都提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 方法。

3. 當環境接著呼叫傳遞 `NULL`的 `GetAutomationObject` 方法時，就會傳回 VSPackage 特定的物件來回應。

4. 如果呼叫 `IExtensibleObject` 的 `QueryInterface`，而 `IVsExtensibleObject` 失敗，則環境會呼叫 `IDispatch`的 `QueryInterface`。

## <a name="automation-for-document-windows"></a>文件視窗的自動化

您也可以從環境中取得標準 <xref:EnvDTE.Document> 物件，不過，編輯者可透過執行 `IExtensibleObject` 介面和回應 `GetAutomationObject`，來擁有自己的 <xref:EnvDTE.Document> 物件的執行。

此外，編輯器可以藉由執行 `IVsExtensibleObject` 或 `IExtensibleObject` 介面，提供 VSPackage 特有的自動化物件，並透過 <xref:EnvDTE.Document.Object%2A> 方法抓取。 [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)會提供 RTF 檔特定的 automation 物件。

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
