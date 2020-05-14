---
title: 故障排除 RegPkg 包裝註冊 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704321"
---
# <a name="troubleshooting-regpkg-package-registration"></a>針對 RegPkg 套件註冊進行疑難排解
> [!NOTE]
> 在 Visual Studio 中註冊包的首選方法是使用 .pkgdef 檔。 這允許擴展部署,而無需訪問系統註冊表。 Pkgdef 檔案是透過使用[CreatePkgDef 實用程式](../../extensibility/internals/createpkgdef-utility.md)創建的。

 要在中使用 RegPkg[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊包,必須使用適合您的包的 RegPkg 版本。

## <a name="regpkg-versions-related-to-package-versions"></a>與套件版本相關的 RegPkg 版本
 RegPkg 有兩個版本。 中包含版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 使用此版本可以註冊使用以下程式集之一生成的套件:

1. 微軟.VisualStudioShell.9.0.dll

2. 微軟.VisualStudioShell.10.0.dll

3. 微軟.VisualStudioShell.11.0.dll

   它不能註冊使用早期的 Microsoft.VisualStudio.Shell.dll 程式集構建的包。

   早期版本的 RegPkg 可以註冊使用 Microsoft.VisualStudio.shell.dll 程式集構建的包。 但是,它不能註冊使用該程式集的更高版本生成的包。

## <a name="see-also"></a>另請參閱
- [VSPackage](../../extensibility/internals/vspackages.md)
