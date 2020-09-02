---
title: Configuration 和 SelectedItem 物件的自動化 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157254"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>組態和 SelectedItem 物件的自動化
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以自動化中的組建和選取的專案進程 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
## <a name="automation-for-builds"></a>組建的自動化  
 組建或設定具有可在您執行時提供的自動化模型 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> 。 如需詳細資訊，請參閱[了解組建組態](../../ide/understanding-build-configurations.md)。  
  
 如果您建立 VSPackage 並想要控制設定選項，就必須使用 automation 模型。  
  
## <a name="automation-for-selecteditem"></a>SelectedItem 自動化  
 您不需要提供物件的執行， `SelectedItem` 因為 Visual Studio 包含標準的執行。 但是，如果您想要的話，可以執行此 `SelectedItem` 物件。 您必須執行包含介面的物件 `SelectedItem` ，並將 VSITEMID 設定為，將回應傳回給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法的呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [參與 Automation 模型](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [瞭解組建設定](../../ide/understanding-build-configurations.md)
