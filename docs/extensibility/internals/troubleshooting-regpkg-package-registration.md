---
title: 疑難排解 RegPkg 套件登錄 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4857e41888962a92dced87d63fa2b63161ecac55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-regpkg-package-registration"></a>疑難排解 RegPkg 套件登錄
> [!NOTE]
>  註冊套件在 Visual Studio 中的慣用的方法是使用.pkgdef 檔。 這可讓擴充部署而不需要存取系統登錄。 使用建立 Pkgdef 檔案[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)。  
  
 使用中的 RegPkg 註冊封裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您必須使用 RegPkg 適用於您封裝的版本。  
  
## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg 版本與封裝版本  
 有兩個 RegPkg 版本。 一種版本隨附於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 註冊套件已使用下列組件的其中一個建置中使用這個版本：  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 它無法註冊使用舊版 Microsoft.VisualStudio.Shell.dll 組件都已建置完成的封裝。  
  
 RegPkg 舊版可以註冊使用 Microsoft.VisualStudio.Shell.dll 組件都已建置完成的封裝。 不過，它無法登錄所使用的組件的更新版本建立的封裝。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../../extensibility/internals/vspackages.md)