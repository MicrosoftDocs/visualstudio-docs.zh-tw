---
title: 針對 RegPkg 套件註冊進行疑難排解 |Microsoft Docs
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
ms.openlocfilehash: b5266579ff235a0f6c4f3e555d79d5a00de2c194
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234857"
---
# <a name="troubleshooting-regpkg-package-registration"></a>針對 RegPkg 套件註冊進行疑難排解
> [!NOTE]
> 在 Visual Studio 中註冊封裝的慣用方法是使用 .pkgdef 檔案。 這可讓您進行延伸模組部署，而不需要存取系統登錄。 .Pkgdef 檔案是使用[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)建立的。

 若要使用中的 RegPkg 註冊封裝 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您必須使用適用于您的封裝的 RegPkg 版本。

## <a name="regpkg-versions-related-to-package-versions"></a>與套件版本相關的 RegPkg 版本
 有兩個版本的 RegPkg。 包含其中一個版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 使用此版本來註冊已使用下列其中一個元件建立的封裝：

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   它無法註冊使用舊版 Microsoft.VisualStudio.Shell.dll 元件所建立的封裝。

   舊版的 RegPkg 可以註冊使用 Microsoft.VisualStudio.Shell.dll 元件所建立的封裝。 不過，它無法註冊使用該元件的較新版本所建立的封裝。

## <a name="see-also"></a>另請參閱
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)
