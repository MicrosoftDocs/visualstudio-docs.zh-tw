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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157238"
---
# <a name="automation-support-for-options-pages"></a>選項頁的自動化支援
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage 可以提供自訂 **選項** 對話方塊至 [ **工具** ] 功能表 (的 [工具選項] 頁面) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，並可讓這些對話方塊提供給 automation 模型使用。  
  
## <a name="tools-options-pages"></a>工具選項頁面  
 若要建立 [ **工具選項** ] 頁面，VSPackage 必須透過 VSPackage 的方法的執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方式（ (或) 方法的 managed 程式碼），提供將使用者控制項執行傳回至環境 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 。  
  
 這是選擇性的，但強烈建議使用，以允許透過 automation 模型存取此新頁面。 您可以透過下列步驟來執行此動作：  
  
1. <xref:EnvDTE._DTE.Properties%2A>透過 IDispatch 衍生物件的實作為擴充物件。  
  
2. 傳回方法的實 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (或針對 managed 程式碼， <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 方法) 至 IDispatch 衍生的物件。  
  
3. 當自動化取用者 <xref:EnvDTE._DTE.Properties%2A> 在自訂 **選項** 屬性頁上呼叫方法時，環境會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法來取得自訂 **工具選項** 頁面的自動化執行。  
  
4. 然後，會使用 VSPackage 的 automation 物件來提供每個 <xref:EnvDTE.Property> 傳回的 <xref:EnvDTE._DTE.Properties%2A> 。  
  
   如需執行自訂工具選項頁面的範例，請參閱 [VSSDK 範例](../../misc/vssdk-samples.md)。  
  
## <a name="see-also"></a>另請參閱  
 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)
