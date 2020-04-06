---
title: 選項頁的自動化支援 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709924"
---
# <a name="automation-support-for-options-pages"></a>選項頁的自動化支援
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackages 可以為 中的 **「工具**選項」功能表(**工具選項**頁)提供自訂**選項**對話框,並可將其提供給自動化模型。

## <a name="tools-options-pages"></a>工具選項頁
 要建立**工具選項**頁,VSPackage 必須提供透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>VSPackage 方法實現返回給環境的使用者控制項實現。 (或者,對於託管代碼,<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>該方法。

 允許通過自動化模型訪問此新頁面是可選的,但強烈建議。 您可以透過以下步驟執行此操作:

1. 通過實現<xref:EnvDTE._DTE.Properties%2A>IDispatch 派生的物件來擴展物件。

2. 將<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法的實現(或對於託管代碼<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>的方法)返回到IDispatch派生的物件。

3. 當自動化消費者在自定義<xref:EnvDTE._DTE.Properties%2A>**Option**屬性頁上調用 該方法時<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>,環境使用 該方法獲取自定義**工具選項**頁的自動化實現。

4. 然後,VSPackage 的自動化物件用於提供返回的<xref:EnvDTE.Property><xref:EnvDTE._DTE.Properties%2A>每個 物件。

   有關實現自訂**工具選項**頁的範例,請參閱[VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

## <a name="see-also"></a>另請參閱
- [公開項目物件](../../extensibility/internals/exposing-project-objects.md)
