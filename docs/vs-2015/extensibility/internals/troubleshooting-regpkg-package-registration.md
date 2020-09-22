---
title: 針對 RegPkg 套件註冊進行疑難排解 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839001"
---
# <a name="troubleshooting-regpkg-package-registration"></a>針對 RegPkg 套件註冊進行疑難排解
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> 在 Visual Studio 中註冊封裝的慣用方式是使用 .pkgdef 檔。 這可讓您進行擴充部署，而不需要存取系統登錄。 .Pkgdef 檔案是使用 [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)建立的。  
  
 若要在中使用 RegPkg 註冊封裝 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，您必須使用適用于封裝的 RegPkg 版本。  
  
## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg 與套件版本相關的版本  
 有兩個版本的 RegPkg。 包含其中一個版本 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 使用此版本來註冊使用下列其中一個元件建立的封裝：  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   它無法註冊使用舊版 Microsoft.VisualStudio.Shell.dll 元件所建立的封裝。  
  
   舊版 RegPkg 可以註冊使用 Microsoft.VisualStudio.Shell.dll 元件建立的封裝。 但是，它無法註冊使用該元件的較新版本所建立的封裝。  
  
## <a name="see-also"></a>另請參閱  
 [發行產品](../../misc/releasing-a-visual-studio-integration-product.md)
