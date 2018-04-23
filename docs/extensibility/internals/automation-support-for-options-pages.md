---
title: 選項頁面的自動化支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="automation-support-for-options-pages"></a>選項頁面的自動化支援
Vspackage 可以提供自訂**選項**對話方塊方塊中以**工具**功能表 （[工具選項] 頁面） 中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以讓它們可以使用 automation 模型。  
  
## <a name="tools-options-pages"></a>工具選項頁  
 若要建立**工具選項** 頁面上，VSPackage 必須提供傳回透過實作 VSPackage 的環境的使用者控制項實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法 (或 managed 程式碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法）。  
  
 它是選擇性的但是我們強烈建議，以允許存取這個新的頁面，透過 automation 模型。 您可以透過下列步驟：  
  
1.  擴充<xref:EnvDTE._DTE.Properties%2A>物件，用來實作 IDispatch 衍生的物件。  
  
2.  傳回的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法 (或 managed 程式碼<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>方法) 至 IDispatch 衍生物件。  
  
3.  當 automation 取用者呼叫<xref:EnvDTE._DTE.Properties%2A>方法在自訂**選項**屬性頁面中，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法，以取得自訂**工具選項**網頁的自動化實作。  
  
4.  VSPackage 的 automation 物件則用來提供每個<xref:EnvDTE.Property>傳回<xref:EnvDTE._DTE.Properties%2A>。  
  
 如需實作自訂的工具選項頁面的範例，請參閱[VSSDK 範例](http://aka.ms/vs2015sdksamples)。  
  
## <a name="see-also"></a>另請參閱  
 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)