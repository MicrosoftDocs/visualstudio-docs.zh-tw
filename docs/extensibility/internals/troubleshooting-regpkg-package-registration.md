---
title: 針對 RegPkg 套件註冊進行疑難排解 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722270"
---
# <a name="troubleshooting-regpkg-package-registration"></a>針對 RegPkg 套件註冊進行疑難排解
> [!NOTE]
> 在 Visual Studio 中註冊封裝的慣用方法是使用 .pkgdef 檔案。 這可讓您進行延伸模組部署，而不需要存取系統登錄。 .Pkgdef 檔案是使用[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)建立的。

 若要在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中使用 RegPkg 註冊封裝，您必須使用適用于您的套件的 RegPkg 版本。

## <a name="regpkg-versions-related-to-package-versions"></a>與套件版本相關的 RegPkg 版本
 有兩個版本的 RegPkg。 其中一個版本包含在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中。 使用此版本來註冊已使用下列其中一個元件建立的封裝：

1. VisualStudioShell 9.0 .dll

2. VisualStudioShell 10.0 .dll

3. VisualStudioShell 11.0 .dll

   它無法註冊使用先前的 VisualStudio 元件所建立的封裝。

   舊版的 RegPkg 可以註冊使用 VisualStudio 所建立的封裝，也就是。 不過，它無法註冊使用該元件的較新版本所建立的封裝。

## <a name="see-also"></a>請參閱
- [VSPackage](../../extensibility/internals/vspackages.md)