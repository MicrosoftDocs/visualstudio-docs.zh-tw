---
title: 在 Vspackage 中安全性的最佳作法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5b3b86736a5425640c1a87df6a3e2c6e6cec0c5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513344"
---
# <a name="best-practices-for-security-in-vspackages"></a>在 Vspackage 中安全性的最佳做法
若要安裝[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]您在電腦上，您必須執行系統管理認證的內容中。 安全性和部署的基本單位[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]應用程式[VSPackage](../../extensibility/internals/vspackages.md)。 必須使用註冊 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，也需要系統管理認證。  
  
 系統管理員具有完整權限以寫入登錄和檔案系統，並執行任何程式碼。 您必須具有這些權限，來開發、 部署，或安裝 VSPackage。  
  
 所安裝，則 VSPackage 會是完全受信任。 因為如此高程度的 VSPackage 相關聯的權限，就可能會不慎安裝具有惡意的 VSPackage。  
  
 使用者應該確定在安裝 Vspackage，僅從信任的來源。 開發 VSPackages 的公司應該強式名稱，登入它們，以確保該竄改的使用者將無法。 開發 VSPackages 的公司應該檢查其外部的相依性，例如 web 服務和遠端安裝，評估，並更正任何安全性問題。  
  
 如需詳細資訊，請參閱 <<c0> [ 安全適用於.NET Framework 程式碼撰寫方針](http://msdn.microsoft.com/library/d55zzx87.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [增益集安全性](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 安全性](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)