---
title: 註冊 Vspackage |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c826b61e4f6d2255be7b7fdad967bab0d8dea74
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488604"
---
# <a name="registering-vspackages"></a>註冊 VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[註冊 Vspackage](https://docs.microsoft.com/visualstudio/extensibility/internals/registering-vspackages)。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 依賴.pkgdef 檔案，來描述及尋找 VSPackage。 .Pkgdef 檔案包含所有的註冊資訊，否則會新增至系統登錄。 將屬性加入至原始碼，然後執行註冊 managed 的 Vspackage [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)上產生的組件，以產生.pkgdef 檔。  
  
## <a name="in-this-section"></a>本節內容  
 [為 VS Shell 指定 VSPackage 檔案位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 描述 Vspackage 的載入路徑。  
  
 [註冊和取消註冊 VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 說明如何註冊 VSPackage。  
  
 [使用自訂註冊屬性來註冊延伸模組](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 描述如何建立可用來部署 managed 的 VSPackage 的註冊資訊清單。

