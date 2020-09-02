---
title: 註冊 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705750"
---
# <a name="registering-vspackages"></a>註冊 VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 依賴 .pkgdef 檔案來描述和找出 VSPackage。 .Pkgdef 檔案包含所有註冊資訊，否則會新增至系統登錄。 藉由將屬性加入至原始程式碼，然後在產生的元件上執行 [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md) 來產生 .pkgdef 檔案，即可註冊 Managed vspackage。

## <a name="in-this-section"></a>本節內容
- [為 VS Shell 指定 VSPackage 檔案位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 描述 Vspackage 的載入路徑。

- [註冊和取消註冊 VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 說明如何註冊 VSPackage。
