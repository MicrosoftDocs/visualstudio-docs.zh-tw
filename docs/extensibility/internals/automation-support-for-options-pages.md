---
title: 選項頁的自動化支援 |Microsoft Docs
description: 瞭解如何將 Vspackage 中的自訂工具選項頁面提供給 Visual Studio automation 模型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b587af698cf7f044c02baab1a8207be1457d6cfd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086218"
---
# <a name="automation-support-for-options-pages"></a>選項頁的自動化支援
Vspackage 可以提供自訂 **選項** 對話方塊至 [ **工具** ] 功能表 (的 [ **工具選項** ] 頁面) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，並可讓這些對話方塊提供給 automation 模型使用。

## <a name="tools-options-pages"></a>工具選項頁
 若要建立 [ **工具選項** ] 頁面，VSPackage 必須透過 VSPackage 的方法執行，提供將使用者控制項執行傳回至環境的程式 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 。  (或適用于 managed 程式碼的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法。 ) 

 這是選擇性的，但強烈建議使用，以允許透過 automation 模型存取此新頁面。 您可以執行下列步驟來達成目的：

1. <xref:EnvDTE._DTE.Properties%2A>透過 IDispatch 衍生物件的實作為擴充物件。

2. 傳回方法的實 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (或針對 managed 程式碼， <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 方法) 至 IDispatch 衍生的物件。

3. 當自動化取用者 <xref:EnvDTE._DTE.Properties%2A> 在自訂 **選項** 屬性頁上呼叫方法時，環境會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法來取得自訂 **工具選項** 頁面的自動化執行。

4. 然後，會使用 VSPackage 的 automation 物件來提供每個 <xref:EnvDTE.Property> 傳回的 <xref:EnvDTE._DTE.Properties%2A> 。

   如需執行自訂 **工具選項** 頁面的範例，請參閱 [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

## <a name="see-also"></a>另請參閱
- [公開專案物件](../../extensibility/internals/exposing-project-objects.md)
