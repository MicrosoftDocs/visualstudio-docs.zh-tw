---
title: 如何： 提供的 Windows 自動化 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1c16b0688cd5fa07fee8be0296958b23aa8c0ae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742330"
---
# <a name="how-to-provide-automation-for-windows"></a>如何： 提供的 Windows 自動化
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以提供文件和工具視窗的自動化。 提供自動化是建議的每當您想要在視窗中，提供 automation 物件和環境已不提供現成的自動化物件，其方式就如同使用 工作清單。  
  
## <a name="automation-for-tool-windows"></a>自動化工具 Windows  
 環境所傳回的標準工具視窗上提供自動化<xref:EnvDTE.Window>物件中的下列程序所述：  
  
#### <a name="to-provide-automation-for-tool-windows"></a>可讓工具視窗  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法，透過與環境<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>作為`VSFPROPID`參數，以取得`Window`物件。  
  
2.  當呼叫端要求 VSPackage 特有的自動化物件，為您的工具視窗，透過<xref:EnvDTE.Window.Object%2A>，此環境會呼叫`QueryInterface`如`IExtensibleObject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，或`IDispatch`介面。 兩者`IExtensibleObject`並`IVsExtensibleObject`提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>方法。  
  
3.  當環境然後呼叫`GetAutomationObject`方法並傳遞`NULL`，回應傳遞回您 VSPackage 所指定的物件。  
  
4.  如果呼叫`QueryInterface`for`IExtensibleObject`並`IVsExtensibleObject`失敗，則環境會呼叫`QueryInterface`如`IDispatch`。  
  
## <a name="automation-for-document-windows"></a>自動化文件的 Windows  
 標準<xref:EnvDTE.Document>物件也會提供在環境中，雖然編輯器可以有它自己的實作`T:EnvDTE.Document`藉由實作的物件`IExtensibleObject`介面及回應`GetAutomationObject`。  
  
 此外，編輯器可以提供 VSPackage 特有的自動化物件，透過擷取<xref:EnvDTE.Document.Object%2A>方法，藉由實作`IVsExtensibleObject`或`IExtensibleObject`介面。 [VSSDK 範例](../../misc/vssdk-samples.md)提供 RTF 文件特定的自動化物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>

