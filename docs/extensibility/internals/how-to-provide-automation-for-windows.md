---
title: "如何： 提供適用於 Windows 的自動化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17cf60573b6feb9fd317116eec4639dbf88f6089
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-automation-for-windows"></a>如何： 提供適用於 Windows 的自動化
您可以提供文件和工具視窗的自動化。 每當您想要的視窗中，使用 automation 物件和環境不存在時，提供自動化建議提供的現成的 automation 物件，與工作清單。  
  
## <a name="automation-for-tool-windows"></a>自動化的工具視窗  
 環境工具視窗上提供自動化功能，藉由傳回標準<xref:EnvDTE.Window>物件中的下列程序所述：  
  
#### <a name="to-provide-automation-for-tool-windows"></a>可讓工具視窗  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法，透過使用在環境<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>為`VSFPROPID`參數，以取得`Window`物件。  
  
2.  當呼叫端要求特定 VSPackage 的 automation 物件透過工具視窗<xref:EnvDTE.Window.Object%2A>，環境呼叫`QueryInterface`如`IExtensibleObject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，或`IDispatch`介面。 同時`IExtensibleObject`和`IVsExtensibleObject`提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>方法。  
  
3.  然後呼叫環境`GetAutomationObject`方法傳遞`NULL`，藉由傳遞回應回 VSPackage 特定物件。  
  
4.  如果呼叫`QueryInterface`如`IExtensibleObject`和`IVsExtensibleObject`失敗，則環境會呼叫`QueryInterface`如`IDispatch`。  
  
## <a name="automation-for-document-windows"></a>文件視窗的自動化  
 標準<xref:EnvDTE.Document>物件也會提供環境，雖然編輯器可以有自己的實作`T:EnvDTE.Document`物件藉由實作`IExtensibleObject`介面，而且回應`GetAutomationObject`。  
  
 此外，編輯器可提供 VSPackage 特有的 automation 物件，透過擷取<xref:EnvDTE.Document.Object%2A>方法，藉由實作`IVsExtensibleObject`或`IExtensibleObject`介面。 [VSSDK 範例](http://aka.ms/vs2015sdksamples)佔 RTF 特定文件的自動化物件。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>