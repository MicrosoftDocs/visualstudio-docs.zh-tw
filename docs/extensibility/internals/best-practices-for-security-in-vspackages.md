---
title: "在 Vspackage 中的安全性最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71f06fdd67e4f1789637c2d935f0d25a06eb9863
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>在 Vspackage 中的安全性最佳作法
若要安裝[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]您在電腦上，您必須執行系統管理認證的內容中。 安全性和部署的基本單位[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]應用程式是[Vspackage](../../extensibility/internals/vspackages.md)。 VSPackage 必須使用來註冊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，也需要系統管理認證。  
  
 系統管理員具有完整權限來寫入至檔案系統與登錄及執行任何程式碼。 您必須擁有這些權限到開發、 部署或安裝 VSPackage。  
  
 所安裝，則 VSPackage 會是完全受信任。 此高層級的 VSPackage 相關聯的權限，因為很可能不小心安裝 VSPackage，已被用於惡意用途。  
  
 使用者應該確保他們只從受信任的來源安裝 Vspackage。 開發 Vspackage 的公司應該強式名稱並加以簽署，就無法以確保使用者該資料遭到竄改。 開發 Vspackage 的公司應該檢查其外部的相依性，例如 web 服務和遠端安裝時，評估並更正任何安全性問題。  
  
 如需詳細資訊，請參閱 < 安全程式碼撰寫方針適用於.NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>請參閱  
 [增益集安全性](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 安全性](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)