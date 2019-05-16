---
title: 在 Vspackage 中安全性的最佳作法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697273"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage 中安全性的最佳做法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

若要安裝[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]您在電腦上，您必須執行系統管理認證的內容中。 安全性和部署的基本單位[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]應用程式[Vspackage](../../extensibility/internals/vspackages.md)。 必須使用註冊 VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，也需要系統管理認證。  
  
 系統管理員具有完整權限以寫入登錄和檔案系統，並執行任何程式碼。 您必須具有這些權限，來開發、 部署，或安裝 VSPackage。  
  
 所安裝，則 VSPackage 會是完全受信任。 因為如此高程度的 VSPackage 相關聯的權限，就可能會不慎安裝具有惡意的 VSPackage。  
  
 使用者應該確定在安裝 Vspackage，僅從信任的來源。 開發 VSPackages 的公司應該強式名稱，登入它們，以確保該竄改的使用者將無法。 開發 VSPackages 的公司應該檢查其外部的相依性，例如 web 服務和遠端安裝，評估，並更正任何安全性問題。  
  
 如需詳細資訊，請參閱 < 安全程式碼撰寫方針適用於.NET Framework ([https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>另請參閱  
 [增益集安全性](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 安全性](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
