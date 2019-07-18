---
title: RegPkg 封裝註冊進行疑難排解 |Microsoft Docs
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
ms.openlocfilehash: 219a21eac296daa442fc2f705eb2758790777333
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344745"
---
# <a name="troubleshooting-regpkg-package-registration"></a>針對 RegPkg 套件註冊進行疑難排解
> [!NOTE]
> Visual Studio 中註冊套件的慣用的方法是使用.pkgdef 檔案。 這可讓擴充功能部署而不需要存取系統登錄。 使用建立 Pkgdef 檔案[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)。

 使用中的 RegPkg 註冊封裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您必須使用 RegPkg 適用於您的套件版本。

## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg 版本相關的套件版本
 有兩個 RegPkg 版本。 一種版本納入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 使用這個版本以註冊使用其中一種下列組件已建置的套件：

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   它無法註冊使用較早的 Microsoft.VisualStudio.Shell.dll 組件已建置的套件。

   RegPkg 舊版可以註冊使用 Microsoft.VisualStudio.Shell.dll 組件已建置的套件。 不過，它無法登錄使用的組件的更新版本所建置的套件。

## <a name="see-also"></a>另請參閱
- [VSPackage](../../extensibility/internals/vspackages.md)