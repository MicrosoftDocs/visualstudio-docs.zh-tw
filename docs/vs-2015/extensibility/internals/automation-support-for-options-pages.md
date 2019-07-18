---
title: 選項頁的自動化支援 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157238"
---
# <a name="automation-support-for-options-pages"></a>選項頁的自動化支援
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage 可以提供自訂**選項**對話方塊來**工具**中的功能表 （[工具選項] 頁面）[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]並可讓使用 automation 模型。  
  
## <a name="tools-options-pages"></a>工具選項頁  
 若要建立**工具選項**頁面上，VSPackage 必須提供環境透過 VSPackage 的實作傳回的使用者控制項實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法 (或 managed 程式碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法）。  
  
 它是選擇性的但極力建議您，以允許存取這個新的頁面，透過 automation 模型。 您可以透過下列步驟來這麼做：  
  
1. 擴充<xref:EnvDTE._DTE.Properties%2A>透過實作 IDispatch 衍生物件的物件。  
  
2. 傳回實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法 (或 managed 程式碼<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>方法) 至 IDispatch 衍生物件。  
  
3. 當自動化取用者呼叫<xref:EnvDTE._DTE.Properties%2A>方法，在自訂**選項**屬性頁面中，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法，以取得自訂**工具選項**頁面的自動化實作。  
  
4. VSPackage 的 automation 物件則用來提供每個<xref:EnvDTE.Property>所傳回<xref:EnvDTE._DTE.Properties%2A>。  
  
   如需實作自訂的 [工具選項] 頁面的範例，請參閱[VSSDK 範例](../../misc/vssdk-samples.md)。  
  
## <a name="see-also"></a>另請參閱  
 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)
