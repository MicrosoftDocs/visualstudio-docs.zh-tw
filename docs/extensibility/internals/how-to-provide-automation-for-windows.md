---
title: 如何:為 Windows 提供自動化 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707956"
---
# <a name="how-to-provide-automation-for-windows"></a>如何:為視窗提供自動化

您可以為文件和工具視窗提供自動化。 每當您想要使自動化物件在視窗中可用時,建議提供自動化,並且環境尚未提供現成的自動化物件,就像使用任務列表一樣。

## <a name="automation-for-tool-windows"></a>工具視窗自動化

環境通過傳回<xref:EnvDTE.Window>標準 物件(如以下過程所述)在工具視窗中提供自動化:

1. 使用__VSFPROPID<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>透過環境呼叫該方法[。VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>)`VSFPROPID`作為參數`Window`獲取 物件。

2. 當呼叫者要求指定 VSPackage 的自動化物件以存取<xref:EnvDTE.Window.Object%2A>工具視窗時,`QueryInterface`環境將`IExtensibleObject`<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>呼`IDispatch`叫 。 和`IExtensibleObject``IVsExtensibleObject`都<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>提供了一種方法。

3. 當環境調用傳遞`GetAutomationObject``NULL`方法時,通過傳遞特定於 VSPackage 的物件來回應。

4. 如果呼叫`QueryInterface``IExtensibleObject``IVsExtensibleObject`並 失敗,則環境將`QueryInterface``IDispatch`呼叫 。

## <a name="automation-for-document-windows"></a>文件視窗自動化

標準<xref:EnvDTE.Document>物件也可以從環境中提供,儘管編輯器可以<xref:EnvDTE.Document>`IExtensibleObject`通過實現`GetAutomationObject`介面和回應 來實現該物件。

此外,編輯器可以通過<xref:EnvDTE.Document.Object%2A>`IVsExtensibleObject`實現`IExtensibleObject`或介面提供通過方法檢索的特定於 VSPackage 的自動化物件。 [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)提供特定於 RTF 文件的自動化物件。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
