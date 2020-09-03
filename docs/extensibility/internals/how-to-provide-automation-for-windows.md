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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905261"
---
# <a name="how-to-provide-automation-for-windows"></a>如何：為 windows 提供自動化

您可以為檔和工具視窗提供自動化功能。 當您想要讓自動化物件可在視窗上使用時，建議您提供自動化，而且環境還不會提供現成的自動化物件，如同工作清單一樣。

## <a name="automation-for-tool-windows"></a>工具視窗的自動化

環境會傳回標準物件，以在工具視窗上提供自動化， <xref:EnvDTE.Window> 如下列程式所述：

1. 透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> __VSFPROPID 的環境來呼叫方法 [。VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) 作為 `VSFPROPID` 取得物件的參數 `Window` 。

2. 當呼叫端要求您的工具視窗的 VSPackage 特定 automation 物件通過時 <xref:EnvDTE.Window.Object%2A> ，環境會呼叫 `QueryInterface` `IExtensibleObject` 、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> 或 `IDispatch` 介面。 `IExtensibleObject`和都 `IVsExtensibleObject` 提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 方法。

3. 當環境接著呼叫 `GetAutomationObject` 方法傳遞時 `NULL` ，會傳回您的 VSPackage 特定物件以回應。

4. 如果呼叫 `QueryInterface` `IExtensibleObject` `IVsExtensibleObject` 失敗，則環境會呼叫 `QueryInterface` `IDispatch` 。

## <a name="automation-for-document-windows"></a>文件視窗的自動化

您 <xref:EnvDTE.Document> 也可以從環境中使用標準物件，雖然編輯器可以藉由實作為 <xref:EnvDTE.Document> `IExtensibleObject` 介面並回應來執行它自己的物件 `GetAutomationObject` 。

此外，編輯器還可以藉 <xref:EnvDTE.Document.Object%2A> 由實作為 `IVsExtensibleObject` 或介面，提供 VSPackage 專屬的自動化物件，並透過方法取出 `IExtensibleObject` 。 [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)會貢獻 RTF 檔專屬的 automation 物件。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
