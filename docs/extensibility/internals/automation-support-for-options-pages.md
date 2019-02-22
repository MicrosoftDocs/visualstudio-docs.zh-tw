---
title: 選項頁的自動化支援 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34d59fbfe6213bbcec1311cf9ad6216b3d8c86c1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629141"
---
# <a name="automation-support-for-options-pages"></a>自動化支援的選項頁面
Vspackage 可以提供自訂**選項**對話方塊來**工具**功能表 (**工具選項**頁面) 中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並可供自動化模型。

## <a name="tools-options-pages"></a>工具選項頁
 若要建立**工具選項**頁面上，VSPackage 必須提供環境透過 VSPackage 的實作傳回的使用者控制項實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法。 (或者，若為 managed 程式碼，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法。)

 它是選擇性的但極力建議您，以允許存取這個新的頁面，透過 automation 模型。 您可以執行下列步驟：

1. 擴充<xref:EnvDTE._DTE.Properties%2A>透過實作 IDispatch 衍生物件的物件。

2. 傳回實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法 (或 managed 程式碼<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>方法) 至 IDispatch 衍生物件。

3. 當自動化取用者呼叫<xref:EnvDTE._DTE.Properties%2A>方法，在自訂**選項**屬性頁面中，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法，以取得自訂**工具選項**頁面的自動化實作。

4. VSPackage 的 automation 物件則用來提供每個<xref:EnvDTE.Property>所傳回<xref:EnvDTE._DTE.Properties%2A>。

   如需範例實作自訂**工具選項**頁面上，請參閱[VSSDK 範例](http://aka.ms/vs2015sdksamples)。

## <a name="see-also"></a>另請參閱
- [公開專案物件](../../extensibility/internals/exposing-project-objects.md)