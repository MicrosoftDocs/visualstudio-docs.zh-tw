---
title: 選項頁的自動化支援 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848974"
---
# <a name="automation-support-for-options-pages"></a>[選項] 頁面的自動化支援
Vspackage 可以將 [自訂**選項**] 對話方塊提供給 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中的 [**工具**] 功能表（[工具] [**選項**] 頁面），並可讓它們可供 automation 模型使用。

## <a name="tools-options-pages"></a>工具選項頁
 若要建立 [**工具選項**] 頁面，VSPackage 必須透過 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法的執行，提供傳回給環境的使用者控制項實。 （或者，如果是 managed 程式碼，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法）。

 這是選擇性的，但強烈建議您透過 automation 模型來允許存取這個新頁面。 您可以使用下列步驟來執行此動作：

1. 透過 IDispatch 衍生物件的執行，擴充 <xref:EnvDTE._DTE.Properties%2A> 物件。

2. 將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法（或 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 方法的 managed 程式碼）的執行傳回給 IDispatch 衍生的物件。

3. 當自動化取用者在自訂**選項**屬性頁上呼叫 <xref:EnvDTE._DTE.Properties%2A> 方法時，環境會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法來取得自訂**工具選項**頁面的自動化執行。

4. 然後，VSPackage 的 automation 物件會用來提供 <xref:EnvDTE._DTE.Properties%2A>所傳回的每個 <xref:EnvDTE.Property>。

   如需執行自訂**工具選項**頁面的範例，請參閱[VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

## <a name="see-also"></a>請參閱
- [公開專案物件](../../extensibility/internals/exposing-project-objects.md)
