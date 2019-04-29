---
title: 註冊 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 426adc0cd150d5867760a8570df5777fec8260a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859250"
---
# <a name="registering-vspackages"></a>註冊 VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 依賴.pkgdef 檔案，來描述及尋找 VSPackage。 .Pkgdef 檔案包含所有的註冊資訊，否則會新增至系統登錄。 將屬性加入至原始碼，然後執行註冊 managed 的 Vspackage [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)上產生的組件，以產生.pkgdef 檔。

## <a name="in-this-section"></a>本節內容
- [為 VS Shell 指定 VSPackage 檔案位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 描述 Vspackage 的載入路徑。

- [註冊和取消註冊 VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 說明如何註冊 VSPackage。
