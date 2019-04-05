---
title: 組態和 SelectedItem 物件的自動化 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942441"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>組態和 SelectedItem 物件的自動化
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以自動化組建和選取的項目中的程序[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
## <a name="automation-for-builds"></a>組建的自動化  
 建置或設定具有您實作時，會提供 automation 模型<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>。 如需詳細資訊，請參閱[了解組建組態](../../ide/understanding-build-configurations.md)。  
  
 如果您建立 VSPackage，而且想要控制組態選項，您必須使用 automation 模型。  
  
## <a name="automation-for-selecteditem"></a>SelectedItem 自動化  
 您沒有提供實作`SelectedItem`物件，因為 Visual Studio 包含標準的實作。 不過，您可以實作`SelectedItem`如果您偏好的物件。 您必須實作物件，包含`SelectedItem`介面，並將回應傳回給呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>VSITEMID 方法設為<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [參與 Automation 模型](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [了解組建組態](../../ide/understanding-build-configurations.md)
