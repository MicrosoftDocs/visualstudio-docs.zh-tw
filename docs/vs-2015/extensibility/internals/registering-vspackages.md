---
title: 註冊 Vspackage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940966"
---
# <a name="registering-vspackages"></a>註冊 VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 依賴.pkgdef 檔案，來描述及尋找 VSPackage。 .Pkgdef 檔案包含所有的註冊資訊，否則會新增至系統登錄。 將屬性加入至原始碼，然後執行註冊 managed 的 Vspackage [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)上產生的組件，以產生.pkgdef 檔。  
  
## <a name="in-this-section"></a>本節內容  
 [為 VS Shell 指定 VSPackage 檔案位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 描述 Vspackage 的載入路徑。  
  
 [註冊和取消註冊 VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 說明如何註冊 VSPackage。  
  
 [使用自訂註冊屬性來註冊延伸模組](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 描述如何建立可用來部署 managed 的 VSPackage 的註冊資訊清單。
