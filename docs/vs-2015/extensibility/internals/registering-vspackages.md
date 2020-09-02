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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157382"
---
# <a name="registering-vspackages"></a>註冊 VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 依賴 .pkgdef 檔案來描述和找出 VSPackage。 .Pkgdef 檔案包含所有註冊資訊，否則會新增至系統登錄。 藉由將屬性加入至原始程式碼，然後在產生的元件上執行 [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md) 來產生 .pkgdef 檔案，即可註冊 Managed vspackage。  
  
## <a name="in-this-section"></a>本節內容  
 [為 VS Shell 指定 VSPackage 檔案位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 描述 Vspackage 的載入路徑。  
  
 [註冊和取消註冊 VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 說明如何註冊 VSPackage。  
  
 [使用自訂註冊屬性來註冊延伸模組](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 說明如何建立可用於部署受控 VSPackage 的註冊資訊清單。
