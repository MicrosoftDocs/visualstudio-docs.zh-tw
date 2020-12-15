---
title: 針對 RegPkg 套件註冊進行疑難排解 |Microsoft Docs
description: 使用此資訊可針對 Visual Studio 中的 RegPkg 套件註冊進行疑難排解。 使用適用于您套件的 RegPkg 版本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eef67b86925bc38a317196bbf00860b75a6ee15c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487708"
---
# <a name="troubleshooting-regpkg-package-registration"></a>針對 RegPkg 套件註冊進行疑難排解
> [!NOTE]
> 在 Visual Studio 中註冊封裝的慣用方式是使用 .pkgdef 檔。 這可讓您進行擴充部署，而不需要存取系統登錄。 .Pkgdef 檔案是使用 [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)建立的。

 若要在中使用 RegPkg 註冊封裝 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您必須使用適用于封裝的 RegPkg 版本。

## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg 與套件版本相關的版本
 有兩個版本的 RegPkg。 包含其中一個版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 使用此版本來註冊使用下列其中一個元件建立的封裝：

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   它無法註冊使用舊版 Microsoft.VisualStudio.Shell.dll 元件所建立的封裝。

   舊版 RegPkg 可以註冊使用 Microsoft.VisualStudio.Shell.dll 元件建立的封裝。 但是，它無法註冊使用該元件的較新版本所建立的封裝。

## <a name="see-also"></a>另請參閱
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)
