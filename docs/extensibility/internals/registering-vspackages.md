---
title: 註冊 Vspackage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6f7e603fbc023415ad2b8ddc157f239feb53768
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128841"
---
# <a name="registering-vspackages"></a>註冊 Vspackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 依賴.pkgdef 檔案，來描述及尋找 VSPackage。 .Pkgdef 檔包含否則會加入至系統登錄的所有登錄資訊。 將屬性加入至原始程式碼，然後執行登錄 managed 的 Vspackage [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)上產生的組件，以產生.pkgdef 檔。  
  
## <a name="in-this-section"></a>本節內容  
 [為 VS Shell 指定 VSPackage 檔案位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 描述 Vspackage 的載入路徑。  
  
 [註冊和取消註冊 VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 說明如何註冊 VSPackage。  
